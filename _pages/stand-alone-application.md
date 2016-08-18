---
ID: 1745
post_title: Stand Alone Application
author: davm
post_date: 2016-08-18 01:00:58
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/omegalib-tutorials/stand-alone-application/
published: true
---
[md]

###  Building a standalone application

All examples, which come with the omegalib, are embedded into its environment and can only be built by invoking the general omegalib build command. If you are developing a larger application, this is really inconvenient and you probably want to seperate your application binaries, data, etc. from the binaries of omegalib. The omegalib wiki has a page on building standalone applications (https://github.com/uic-evl/omegalib/wiki/NewApplication), however it does not cover all the aspects needed to get a running environment.

Omegalib assumes that libraries are relative to the current binary runpath. If you are not running the application binary from omegalib/build/bin, however, the libraries needed will not be found. 
You can add the directory of the binaries to the datamanager. In the cmakelists, add in a definition which points to the directory:
```
add_definitions(-DOMEGALIB_BIN_DIR="${Omegalib_DIR}/bin")
```
and in your code, before calling omain add the directory to the data manager so the libraries can be dynamically loaded:
```cpp
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

#####  Overriding omegalib file loaders

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



#####  Gotchas when using omegaOsg
Although omegaOsg allows the usage of most osg concepts, some osg features do not work when used in omegalib
- rendering masks are not processed by omegaOsg, therefore all geometry will be displayed twice if you are using two cameras with different camera masks.  If you experience similar artifacts as in figure 1 (insert flickering.png), you might have probably have multiple cameras rendering the scene with either ignored camera mask settings, culling settings or render order settings.
- You do not have access to the actual osg rendering camera before rendering. There is however a framefinished callback, which gives you access to the rendering internals

[/md]