---
ID: 1697
post_title: Building a standalone Application
author: davm
post_date: 2016-08-17 00:19:13
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/omegalib-tutorials/advancedomegalibosgapplications/building-a-standalone-application/
published: true
---
[md]


```cpp
void NodeTrackerManipulator::updateOmegaCamera(omega::Camera *cam){
    osg::Vec3d eye, unused_center, up;

    // call same method, that osg internally uses for its camera updates
    osg::Matrixd invMatrix = getInverseMatrix();
	invMatrix.getLookAt(eye, unused_center, up);

   	osg::NodePath nodePath;
   	//get the path from the tracked node to the top level element
   	getTrackNodePath().getNodePath(nodePath);
   	//compute a transform from the tracked node space to world space
    osg::Matrixd localToWorld = osg::computeLocalToWorld(nodePath, true);
    // apply this transformation to the cameramanipulator center
    // this is normally the tracked node center, but might be panned
    osg::Vec3d worldCenter = _center * localToWorld;

    omega::Vector3f oCenterVec = OSGVEC3_OMEGA(worldCenter);
    // set the lookat of omega camera
    //order is important here, setting lookat before position 
    // will result in choppy camera rotation
    cam->setPosition( OSGVEC3_OMEGA(eye) );
    cam->lookAt(oCenterVec, OSGVEC3_OMEGA(up) );     
}
```

### Executing pre-render cameras

In osg, cameras can have different render orders: Pre-render, normal, and post-render.
Pre-render cameras are often used, to render a certain effect into a texture, which are then used in the actual rendering of the scene. A common use case is rendering reflections on surfaces.

In our game, we want to render a very shiny surface. A pre-render camera is used, to render the scene with a flipped z-transform:

(todo: extract and insert snapshot from presentation)

Our camera therefore moves with the main camera and its position has to be updated accordingly. Setting the transformation of the reflection camera at the right time is crucial, because setting it too late will result in the reflection lagging one frame behind and too early will result in the main camera not being updated with the new transform yet. A hacky method  could be to directly copy over the main camera transform to the reflection camera, when it is set in the cameramanipulator. However, this could break as soon as we have other methods influencing the camera position: imagine a method setting the field of view dynamically or a method preventing cameras flying into obstacles. Another problem is, that in omega multiple windows can be created on one machine, each update method is therefore executed once for each camera.If you have two windows, you will probably see constantly switching reflections between the windows, because the transform is applied to the wrong reflection camera. What we actually want is to have a camera callback executed right before the reflection camera is rendered. 

In osg, the cull traverse decides what objects to render and what to cull away. The Cullvisitor actually computes the correct transformation of each node and pushes objects into the the draw stage, which is executed after the Cullvisitor has visited all nodes. Therefore, the CullCallback is the latest point, we can influence a nodes transform before it is rendered. However the cullcallback is executed after the node transforms have already been pushed into the render stage.If we would therefore execute the cullcallback directly on the camera, we would not see any positional change. We must therefore set the cullcallback on a node above the camera (we named it cameragroup) and then access its child:

```cpp
class CUpdateCameraCallback : public osg::NodeCallback
{
public:	
	CUpdateCameraCallback() : NodeCallback(){}
	void operator()(osg::Node *node, osg::NodeVisitor *nv)
	{
	    // only execute this callback if in the culling stage
		if (nv->getVisitorType() == osg::NodeVisitor::CULL_VISITOR)
		{
		    // the camera is the only child of the camera group
			osg::Camera	*camera = dynamic_cast<osg::Camera *>(node->asGroup()->getChild(0));
			// The cullvisitor holds information about the current (main) camera
			osgUtil::CullVisitor* cv = static_cast<osgUtil::CullVisitor*>(nv);

			if (camera != NULL)
			{
			    // copy over the transforms of the main camera
				camera->setProjectionMatrix(cv->getCurrentCamera()->getProjectionMatrix() );
				camera->setViewMatrix(cv->getCurrentCamera()->getViewMatrix());
				// set the eye point in the shader
				g_cameraEyeU->set(cv->getEyePoint());
			}
		}
		this->traverse(node, nv);
	}
};
```









# Advanced omegalib/osg applications

Building visualizations with cyclops in python can produce stunning results and provides tools for many use cases, however there are certain applications which cannot be built with cyclops/python (without extending the cyclops c++ classes).
The underlying framework OpenSceneGraph is a powerful general purpose computer graphics library, which omegalib/cyclops uses to render computer graphics distributed across multiple displays.
Reasons for programming in osg/omegalib in c++ could be
* You already have an existing application application using osg that you want to port to a multi-display setup in omegalib
* Your application requires a large amount of data processing, dynamic geometry or special effects
* You want to use third party c++ libraries, such as physics or sound engines
* You want to use any methods of osg which are not accesible in cyclops


This tutorial assumes that you already have knowledge of programming in osg. If not, there are many good resources on the internet to learn programming the OpenSceneGraph, for example, the OpenSceneGraph Beginner's Guide (http://ahux.narod.ru/olderfiles/1/OpenSceneGraph.3.0.Beginners.Guide-3208.pdf) will get you started and contains many good examples. Going further, the OpenSceneGraph Cookbook (https://www.packtpub.com/game-development/openscenegraph-3-cookbook) provides recipes for many advanced topics.

### Integration of osg and omegalib

Omegalib comes with support for openscenegraph as its rendering system in form of the omegaOsg module. It is important to know, how osg is actually integrated into omegalib and how rendering on distributed nodes work, to be able to efficiently develop applications in omegalib. Unfortunately, there is no official documentation of the omegaOsg module, which leaves programmers with only the source code to work with. Luckily, the binding code between osg and omegalib is rather small and not too complex.

(insert diagramomegaOsg.png)

The omegaOsg module is a omegalib module which contains a osg::Node (the root) and registers a custom renderpass to the omegalib library. On each frame, the equalizer displaysystem calls the render method (on all nodes) of the renderpass class. Internally, the osgmodule copies over all transforms and properties of the omegalib camera to a osg::Camera and then the sceneview class performs the culling and rendering of the scenegraph. It is important to know, that no geometry is shared among nodes (in fact not even transforms are shared), the distributed nodes all run the same program and the renderloop execution is synced. Therefore transforms or dynamic geometry might have be synced by yourself. We will elaborate on this topic later again.


# Building a standalone application

All examples, which come with the omegalib, are embedded into its environment and can only be built by invoking the general omegalib build command. If you are developing a larger application, this is really inconvenient and you probably want to seperate your application binaries, data, etc. from the binaries of omegalib. The omegalib wiki has a page on building standalone applications (https://github.com/uic-evl/omegalib/wiki/NewApplication), however it does not cover all the aspects needed to get a running environment.

Omegalib assumes that libraries are relative to the current binary runpath. If you are not running the application binary from omegalib/build/bin, however, the libraries needed will not be found. 
You can add the directory of the binaries to the datamanager. In the cmakelists, add in a definition which points to the directory:
```
add_definitions(-DOMEGALIB_BIN_DIR="${Omegalib_DIR}/bin")
```
and in your code, before calling omain add the directory to the data manager so the libraries can be dynamically loaded:
```c
omega::DataManager* dataManager = omega::SystemManager::instance()->getDataManager();
dataManager->addSource(new omega::FilesystemDataSource(OMEGALIB_BIN_DIR));
```

Next, we show a minimal example for building a standalone Application using omegalib. First, we declare our Module class. The class will be constructed by omegalib. The constructor creates a new osgmodule and reigsters it in the omega moduleservices. The actual initialization of the scene is done in initialize, which is called by omegalib on the first iteration of the renderloop.

```cpp
#include <osgDB/ReadFile>
#include <omega.h>
#include <omegaOsg/omegaOsg.h>

omega::String sModelName;
///////////////////////////////////////////////////////////////////////////////
class MinimalExample: public omega::EngineModule
{
public:
    MinimalExample(): EngineModule("MinimalExample")
    {
        myOsg = new omegaOsg::OsgModule::instance();
    }
    virtual void initialize();
private:
    omegaOsg::OsgModule* myOsg;
};
```

Our initialize method simply loads a node file from the disk, using a modelname passed in over the commandline. 
Omegalib initiliazes all its state in the module initiliaze traversal, whichs initializes equalizer, omgealib, omicron, etc. 
Make sure that any calls with references to omegalib objects are invoked in the initialize method at the earliest. 

```cpp
void MinimalExample::initialize()
{
    // The node containing the scene
    osg::Node* node = NULL;

    omega::String path;
    if(omega::DataManager::findFile(sModelName, path)) {
        node = osgDB::readNodeFile(path);
        if (node == NULL) {
            omega::ofwarn("!Failed to load model: %1% (unsupported file format or corrupted data)", %path); 
            return;
        }
    }
    // attach any global state (shaders, lights, etc.) to this node\
    myOsg->setRootNode(node);
}
```
Finally, the main methods creates a omegalib application, reads from the commandline and then executes the main omegalib loop.
```cpp
///////////////////////////////////////////////////////////////////////////////
// Application entry point
int main(int argc, char** argv)
{
    omega::Application<MinimalExample> app("minimalExample");
    omega::oargs().newNamedString(':', "model", "model", "The osg model to load", sModelName);
    return omega::omain(app, argc, argv);
}
```

### Overriding omegalib file loaders

Omegalib registers custom file loaders, which in some cases override the standard osg plugins. Sometimes, this can lead to unexpected behaviour: for example the tga of omegalib does not implement the full tga standard and loading images with 24bpp, which loaded fine with the osgdb_tga plugin will not work anymore. To use a certain osg loader, you have two options: load data/textures/nodes before the omegalib ``omain`` call or manually remove loaders from registry. The first method is preferred, if you only need to load files once and can do this before starting the actual application. If not, the second method provides a (little bit hacky) workaround.

To remove a loader from the osgDB registry, first store the filepaths before running ``omain``:
```cpp
for (auto libPath : osgDB::Registry::instance()->getLibraryFilePathList ()) 
{
        _storedLibPaths += libPath + ":";
}
```
storedLibPaths should then contain the correct directories of plugins (the standard osg directories), you want to load.
When running omain, the omegaOsg initiliaze method will set the plugin library searchpath automatically to a directory containing the loaders you don't want to use.
To revert this, reset the osgDB::Registry library search path to its original path. 
Then, remove the reader writer which is giving troubles from the registry, this will cause a reload on invocation using the plugins in the correct path
```cpp
// The omegaOsg instance() method initiliazes it and configures its libpaths, so it is safe 
// to revert these libpaths in our initialize method
MinimalExample::initialize(){
    osgDB::Registry* reg = osgDB::Registry::instance();

    reg->setLibraryFilePathList(_storedLibPaths);
    osgDB::Registry::instance()->removeReaderWriter(
        osgDB::Registry::instance()->getReaderWriterForExtension("tga"));
        
    // now you can load your tga files, and they will be correctly loaded by the osg loader plugin
```

### Debugging your application

Debugging computer graphics application can be quite hard, as the errors can manifest themselves as visual artefacts or other errors, which are quite hard to trace down.
Setting the notify and log level to debug can help tracing down many errors:
set the `OSG_NOTIFY_LEVEL=DEBUG`  in your environment for detailed osg debug messages
pass the `--log v` flag to your application, for omegalib debug messages

Crashes which happen during the initiliaze call can sometimes be hard to debug, as no actual debug messages are displayed. Shifting the method call into your gameloop to test assumptions often helps in getting more useful error messages.

When debugging an application over multiple nodes in equalizer, getting debug traces can be tricky. One way to get information about segfaults is to have a custom launcher script for children in the .cfg file and log the stack trace to a a file: 
Set the nodelauncher in your .cfg file to a custom script: 
```
nodeLauncher = "ssh -n %h startTroenSlave.sh %d %c"
```
 startTroenSlave. sh:
```
D=$1
C=$2
cd $D
... # set other environment variables
export LD_LIBRARY_PATH=$D:${D}/osg:${D}/osg/osgPlugins-3.3.0:$LD_LIBRARY_PATH

# -r is for remote log
gdb -x gdbcommand.txt --args  $C -r --log v  $*
```


gdbcommand.txt:
```
set logging file gdb.txt
set logging on
run
bt
```



### Gotchas when using omegaOsg
Although omegaOsg allows the usage of most osg concepts, some osg features do not work when used in omegalib
- rendering masks are not processed by omegaOsg, therefore all geometry will be displayed twice if you are using two cameras with different camera masks.  If you experience similar artifacts as in figure 1 (insert flickering.png), you might have probably have multiple cameras rendering the scene with either ignored camera mask settings, culling settings or render order settings.
- You do not have access to the actual osg rendering camera before rendering. There is however a framefinished callback, which gives you access to the rendering internals


[/md]