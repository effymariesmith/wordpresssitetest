---
ID: 1418
post_title: Advanced Omegalib/OSG Applications
author: davm
post_date: 2016-08-10 00:26:48
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/tutorials/advancedomegalibosgapplications/
published: true
panels_data:
  - |
    a:3:{s:7:"widgets";a:5:{i:0;a:6:{s:5:"title";s:0:"";s:4:"text";s:61:"<h3 style="text-align: center;">Omegalib Tutorial Series</h3>";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578723843cea2";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:0;s:9:"widget_id";s:36:"1ea35202-0ffb-4952-88db-1380842ca3f4";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:1;a:5:{s:8:"headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:4:"left";s:24:"so_field_container_state";s:4:"open";}s:12:"sub_headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:6:"center";s:24:"so_field_container_state";s:4:"open";}s:7:"divider";a:8:{s:5:"style";s:5:"solid";s:6:"weight";s:4:"thin";s:5:"color";b:0;s:11:"side_margin";s:4:"20px";s:16:"side_margin_unit";s:2:"px";s:10:"top_margin";s:4:"20px";s:15:"top_margin_unit";s:2:"px";s:24:"so_field_container_state";s:4:"open";}s:12:"_sow_form_id";s:13:"57871dc1b3fe7";s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Headline_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:1;s:9:"widget_id";s:36:"42c24578-cfd7-4dd5-8d52-e5b5178da0b8";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:2;a:6:{s:5:"title";s:0:"";s:4:"text";s:563:"<h4>Tutorials</h4>
    <ol>
     	<li style="text-align: left;"><a href="/wordpress/tutorials/load-box/">Load Geometry </a></li>
     	<li style="text-align: left;"><a href="/wordpress/tutorials/building-the-scenegraph/"><strong>Building The Scenegraph</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/tutorials/defining-interactions/"><strong>Defining Interactions</strong></a></li>
            <li style="text-align: left;"><a href="/wordpress/tutorials/advancedomegalibosgapplications/"><strong>Advanced Omegalib/OSG Applications</strong></a></li>
    
    </ol>
    ";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"576b4c626e8f5";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:0;s:2:"id";i:2;s:9:"widget_id";s:36:"4a98973e-09c0-48a2-923d-fcbc887ca755";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:3;a:6:{s:5:"title";s:0:"";s:4:"text";s:28213:"<h1>Advanced omegalib/osg applications</h1><p>Building visualizations with cyclops in python can produce stunning results and provides tools for many use cases, however there are certain applications which cannot be built with cyclops/python (without extending the cyclops c++ classes).<br />The underlying framework OpenSceneGraph is a powerful general purpose computer graphics library, which omegalib/cyclops uses to render computer graphics distributed across multiple displays.<br />Reasons for programming in osg/omegalib in c++ could be</p><ul><li>You already have an existing application application using osg that you want to port to a multi-display setup in omegalib</li><li>Your application requires a large amount of data processing, dynamic geometry or special effects</li><li>You want to use third party c++ libraries, such as physics or sound engines</li><li>You want to use any methods of osg which are not accesible in cyclops</li></ul><p>This tutorial assumes that you already have knowledge of programming in osg. If not, there are many good resources on the internet to learn programming the OpenSceneGraph, for example, the OpenSceneGraph Beginner’s Guide (<a href="http://ahux.narod.ru/olderfiles/1/OpenSceneGraph.3.0.Beginners.Guide-3208.pdf">http://ahux.narod.ru/olderfiles/1/OpenSceneGraph.3.0.Beginners.Guide-3208.pdf</a>) will get you started and contains many good examples. Going further, the OpenSceneGraph Cookbook (<a href="https://www.packtpub.com/game-development/openscenegraph-3-cookbook">https://www.packtpub.com/game-development/openscenegraph-3-cookbook</a>) provides recipes for many advanced topics.</p><h3>Integration of osg and omegalib</h3><p>Omegalib comes with support for openscenegraph as its rendering system in form of the omegaOsg module. It is important to know, how osg is actually integrated into omegalib and how rendering on distributed nodes work, to be able to efficiently develop applications in omegalib. Unfortunately, there is no official documentation of the omegaOsg module, which leaves programmers with only the source code to work with. Luckily, the binding code between osg and omegalib is rather small and not too complex.</p><p><img class="wp-image-1429 aligncenter" src="http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-300x167.png" alt="diagramOmegaOsg" width="708" height="394" /></p><p>(insert diagramomegaOsg.png)</p><p>The omegaOsg module is a omegalib module which contains a osg::Node (the root) and registers a custom renderpass to the omegalib library. On each frame, the equalizer displaysystem calls the render method (on all nodes) of the renderpass class. Internally, the osgmodule copies over all transforms and properties of the omegalib camera to a osg::Camera and then the sceneview class performs the culling and rendering of the scenegraph. It is important to know, that no geometry is shared among nodes (in fact not even transforms are shared), the distributed nodes all run the same program and the renderloop execution is synced. Therefore transforms or dynamic geometry might have be synced by yourself. We will elaborate on this topic later again.</p><h1>Building a standalone application</h1><p>All examples, which come with the omegalib, are embedded into its environment and can only be built by invoking the general omegalib build command. If you are developing a larger application, this is really inconvenient and you probably want to seperate your application binaries, data, etc. from the binaries of omegalib. The omegalib wiki has a page on building standalone applications (<a href="https://github.com/uic-evl/omegalib/wiki/NewApplication">https://github.com/uic-evl/omegalib/wiki/NewApplication</a>), however it does not cover all the aspects needed to get a running environment.</p><p>Omegalib assumes that libraries are relative to the current binary runpath. If you are not running the application binary from omegalib/build/bin, however, the libraries needed will not be found.<br />You can add the directory of the binaries to the datamanager. In the cmakelists, add in a definition which points to the directory:</p><pre><code>add_definitions(-DOMEGALIB_BIN_DIR="${Omegalib_DIR}/bin")</code></pre><p>and in your code, before calling omain add the directory to the data manager so the libraries can be dynamically loaded:</p><pre><code>omega::DataManager* dataManager = omega::SystemManager::instance()-&amp;gt;getDataManager();
    dataManager-&amp;gt;addSource(new omega::FilesystemDataSource(OMEGALIB_BIN_DIR));</code></pre><p>Next, we show a minimal example for building a standalone Application using omegalib. First, we declare our Module class. The class will be constructed by omegalib. The constructor creates a new osgmodule and reigsters it in the omega moduleservices. The actual initialization of the scene is done in initialize, which is called by omegalib on the first iteration of the renderloop.</p><pre><code>#include &amp;lt;osgDB/ReadFile&amp;gt;
    #include
    #include &amp;lt;omegaOsg/omegaOsg.h&amp;gt;
    
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
    };</code></pre><p>Our initialize method simply loads a node file from the disk, using a modelname passed in over the commandline.<br />Omegalib initiliazes all its state in the module initiliaze traversal, whichs initializes equalizer, omgealib, omicron, etc.<br />Make sure that any calls with references to omegalib objects are invoked in the initialize method at the earliest.</p><pre><code>void MinimalExample::initialize()
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
    // attach any global state (shaders, lights, etc.) to this node
    myOsg-&amp;gt;setRootNode(node);
    }</code></pre><p>Finally, the main methods creates a omegalib application, reads from the commandline and then executes the main omegalib loop.</p><pre><code>///////////////////////////////////////////////////////////////////////////////
    // Application entry point
    int main(int argc, char** argv)
    {
    omega::Application app("minimalExample");
    omega::oargs().newNamedString(':', "model", "model", "The osg model to load", sModelName);
    return omega::omain(app, argc, argv);
    }</code></pre><h3>Overriding omegalib file loaders</h3><p>Omegalib registers custom file loaders, which in some cases override the standard osg plugins. Sometimes, this can lead to unexpected behaviour: for example the tga of omegalib does not implement the full tga standard and loading images with 24bpp, which loaded fine with the osgdb_tga plugin will not work anymore. To use a certain osg loader, you have two options: load data/textures/nodes before the omegalib <code>omain</code> call or manually remove loaders from registry. The first method is preferred, if you only need to load files once and can do this before starting the actual application. If not, the second method provides a (little bit hacky) workaround.</p><p>To remove a loader from the osgDB registry, first store the filepaths before running <code>omain</code>:</p><pre><code>for (auto libPath : osgDB::Registry::instance()-&amp;gt;getLibraryFilePathList ())
    {
    _storedLibPaths += libPath + ":";
    }</code></pre><p>storedLibPaths should then contain the correct directories of plugins (the standard osg directories), you want to load.<br />When running omain, the omegaOsg initiliaze method will set the plugin library searchpath automatically to a directory containing the loaders you don’t want to use.<br />To revert this, reset the osgDB::Registry library search path to its original path.<br />Then, remove the reader writer which is giving troubles from the registry, this will cause a reload on invocation using the plugins in the correct path</p><pre><code>// The omegaOsg instance() method initiliazes it and configures its libpaths, so it is safe
    // to revert these libpaths in our initialize method
    MinimalExample::initialize(){
    osgDB::Registry* reg = osgDB::Registry::instance();
    
    reg-&amp;gt;setLibraryFilePathList(_storedLibPaths);
    osgDB::Registry::instance()-&amp;gt;removeReaderWriter(
    osgDB::Registry::instance()-&amp;gt;getReaderWriterForExtension("tga"));
    
    // now you can load your tga files, and they will be correctly loaded by the osg loader plugin</code></pre><h3>Debugging your application</h3><p>Debugging computer graphics application can be quite hard, as the errors can manifest themselves as visual artefacts or other errors, which are quite hard to trace down.<br />Setting the notify and log level to debug can help tracing down many errors:<br />set the <code>OSG_NOTIFY_LEVEL=DEBUG</code> in your environment for detailed osg debug messages<br />pass the <code>--log v</code> flag to your application, for omegalib debug messages</p><p>Crashes which happen during the initiliaze call can sometimes be hard to debug, as no actual debug messages are displayed. Shifting the method call into your gameloop to test assumptions often helps in getting more useful error messages.</p><p>When debugging an application over multiple nodes in equalizer, getting debug traces can be tricky. One way to get information about segfaults is to have a custom launcher script for children in the .cfg file and log the stack trace to a a file:<br />Set the nodelauncher in your .cfg file to a custom script:</p><pre><code>nodeLauncher = "ssh -n %h startTroenSlave.sh %d %c"</code></pre><p>startTroenSlave. sh:</p><pre><code>D=$1
    C=$2
    cd $D
    ... # set other environment variables
    export LD_LIBRARY_PATH=$D:${D}/osg:${D}/osg/osgPlugins-3.3.0:$LD_LIBRARY_PATH
    
    # -r is for remote log
    gdb -x gdbcommand.txt --args $C -r --log v $*</code></pre><p>gdbcommand.txt:</p><pre><code>set logging file gdb.txt
    set logging on
    run
    bt</code></pre><h3>Gotchas when using omegaOsg</h3><p>Although omegaOsg allows the usage of most osg concepts, some osg features do not work when used in omegalib</p><ul><li>rendering masks are not processed by omegaOsg, therefore all geometry will be displayed twice if you are using two cameras with different camera masks. If you experience similar artifacts as in figure 1</li><li><img class="alignnone wp-image-1431" src="http://localhost/wordpress/wp-content/uploads/2016/08/flickering-300x188.png" alt="flickering" width="489" height="306" /></li><li>(insert flickering.png), you might have probably have multiple cameras rendering the scene with either ignored camera mask settings, culling settings or render order settings.</li><li>You do not have access to the actual osg rendering camera before rendering. There is however a framefinished callback, which gives you access to the rendering internals</li></ul><h1>Hands On: Integrating a game into omegalib</h1><p>In this section, we will show a few common problems arising, when integrating highly interactive applications such as games. We will show the solution to these problems in the context of integrating a game using osg and bullet physics, called Troen. For source reference and more in-depth examples of integrating a fairly advanced osg application into omegalib, you can find the source of the game on <a href="https://github.com/MaxReimann/Troen">github</a>.</p><p> </p><p><img class="alignnone  wp-image-1432" src="http://localhost/wordpress/wp-content/uploads/2016/08/reflectionmultiplewindows-300x73.png" alt="reflectionmultiplewindows" width="875" height="213" /></p><p>(insert troen-2window.png)</p><p>screenshot of the game running across two windows</p><h3>Setting transforms on omega cameras:</h3><p>The main interaction between omegalib and osg concerns the setting and updating of cameras. When implementing or porting an application with dynamic cameras, which can move around, rotate/orbit, etc. care must be taken to apply the correct transform.<br />In osg, cameras can be part of the scene graph in lower levels. When their reference frame is set to RELATIVE_RF, they will reference all underlying geomertry from a relative coordinate frame. However, omega cameras are commonly set in an absolute reference frame. When calculating transforms, e.g. taking the output of a osg camera manipulator, care must be taken to convert the local transform into the world transform.</p><p>An example for such a transformation is the updateCamera method of the nodetrackermanipulator, which orbits around a tracked node and sets the camera in every frame. The nodetrackermanipulator computes a center and rotation around the tracked node and when updating the camera, it uses the inverse of this transform to set its lookat:</p><pre><code>void NodeTrackerManipulator::updateCamera(osg::Camera&amp;amp; camera)
    {
    osg::Vec3d eye, center, up, unused;
    osg::Matrixd invMatrix = getInverseMatrix();
    invMatrix.getLookAt(eye, center, up);
    camera.setViewMatrixAsLookAt(eye,center,up);
    }</code></pre><p>The <em>omega::Camera</em> also has a lookat method, however, if you update the <em>omega::Camera</em> by using its lookat method, it will produce weird, incorrect rotations, which are a symptom of the wrong coordinate frame of the center vector: The coordinate frame of the calculated center vector is in the camera view space but should really be in the world space.</p><pre><code>void NodeTrackerManipulator::updateOmegaCamera(omega::Camera *cam){
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
    cam-&amp;gt;setPosition( OSGVEC3_OMEGA(eye) );
    cam-&amp;gt;lookAt(oCenterVec, OSGVEC3_OMEGA(up) );
    }</code></pre><h3>Executing pre-render cameras</h3><p>In osg, cameras can have different render orders: Pre-render, normal, and post-render.<br />Pre-render cameras are often used, to render a certain effect into a texture, which are then used in the actual rendering of the scene. A common use case is rendering reflections on surfaces.</p><p>In our game, we want to render a very shiny surface. A pre-render camera is used, to render the scene with a flipped z-transform:</p><p>(todo: extract and insert snapshot from presentation)</p><p>Our camera therefore moves with the main camera and its position has to be updated accordingly. Setting the transformation of the reflection camera at the right time is crucial, because setting it too late will result in the reflection lagging one frame behind and too early will result in the main camera not being updated with the new transform yet. A hacky method could be to directly copy over the main camera transform to the reflection camera, when it is set in the cameramanipulator. However, this could break as soon as we have other methods influencing the camera position: imagine a method setting the field of view dynamically or a method preventing cameras flying into obstacles. Another problem is, that in omega multiple windows can be created on one machine, each update method is therefore executed once for each camera.If you have two windows, you will probably see constantly switching reflections between the windows, because the transform is applied to the wrong reflection camera. What we actually want is to have a camera callback executed right before the reflection camera is rendered.</p><p>In osg, the cull traverse decides what objects to render and what to cull away. The Cullvisitor actually computes the correct transformation of each node and pushes objects into the the draw stage, which is executed after the Cullvisitor has visited all nodes. Therefore, the CullCallback is the latest point, we can influence a nodes transform before it is rendered. However the cullcallback is executed after the node transforms have already been pushed into the render stage.If we would therefore execute the cullcallback directly on the camera, we would not see any positional change. We must therefore set the cullcallback on a node above the camera (we named it cameragroup) and then access its child:</p><pre><code>class CUpdateCameraCallback : public osg::NodeCallback
    {
    public:
    CUpdateCameraCallback() : NodeCallback(){}
    void operator()(osg::Node *node, osg::NodeVisitor *nv)
    {
    // only execute this callback if in the culling stage
    if (nv-&amp;gt;getVisitorType() == osg::NodeVisitor::CULL_VISITOR)
    {
    // the camera is the only child of the camera group
    osg::Camera *camera = dynamic_cast(node-&amp;gt;asGroup()-&amp;gt;getChild(0));
    // The cullvisitor holds information about the current (main) camera
    osgUtil::CullVisitor* cv = static_cast&amp;lt;osgUtil::CullVisitor*&amp;gt;(nv);
    
    if (camera != NULL)
    {
    // copy over the transforms of the main camera
    camera-&amp;gt;setProjectionMatrix(cv-&amp;gt;getCurrentCamera()-&amp;gt;getProjectionMatrix() );
    camera-&amp;gt;setViewMatrix(cv-&amp;gt;getCurrentCamera()-&amp;gt;getViewMatrix());
    // set the eye point in the shader
    g_cameraEyeU-&amp;gt;set(cv-&amp;gt;getEyePoint());
    }
    }
    this-&amp;gt;traverse(node, nv);
    }
    };</code></pre><p>Now we show , how to set up the camera correctly:</p><pre><code>cameraGroup = new osg::Group();
    m_reflectionCamera = new osg::Camera();
    reflectionTransform = new osg::MatrixTransform();
    
    cameraGroup-&amp;gt;addChild(m_reflectionCamera);
    m_reflectionCamera-&amp;gt;addChild(reflectionTransform);
    
    m_reflectionCamera-&amp;gt;setClearMask(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);
    // render the camera before the main camera
    m_reflectionCamera-&amp;gt;setRenderOrder(osg::Camera::PRE_RENDER);
    // write into a frame buffer later used as texture
    m_reflectionCamera-&amp;gt;setRenderTargetImplementation(osg::Camera::FRAME_BUFFER_OBJECT);
    // prevent near clipping
    m_reflectionCamera-&amp;gt;setComputeNearFarMode(osg::CullSettings::DO_NOT_COMPUTE_NEAR_FAR);
    // calculate all transforms in world space
    m_reflectionCamera-&amp;gt;setReferenceFrame(osg::Transform::ABSOLUTE_RF);
    // set the viewport to the size of the texture
    m_reflectionCamera-&amp;gt;setViewport(0, 0, texSize, texSize);
    m_reflectionCamera-&amp;gt;setClearDepth(1.0);
    
    //Important: set our cull callback on the cameragroup, not the camera itself
    m_cameraGroupCallback = new CUpdateCameraCallback();
    cameraGroup-&amp;gt;setCullCallback(m_cameraGroupCallback);</code></pre><p>Calculating the actual reflection does not need any extra adjustements for distributed rendering, but is shown here for reference:</p><pre><code>// add a clipping plane, to clip everything below z=0.0.
    //beware, that vec4(a,b,c,d) is a plane equation with a,b,c the plane normal and d the plane height
    m_reflectionClipPlane = new osg::ClipPlane(0, osg::Vec4d(0.0, 0.0, 1.0, 0.0));
    m_reflectionClipNode = new osg::ClipNode;
    m_reflectionClipNode-&amp;gt;addClipPlane(m_reflectionClipPlane);
    reflectionTransform-&amp;gt;addChild(m_reflectionClipNode);
    // mirror the scene along the z axis
    reflectionTransform-&amp;gt;setMatrix(osg::Matrix::scale(1.0, 1.0, -1.0));
    
    // render the reflection camera into a texture
    osg::ref_ptr texture = new osg::Texture2D();
    texture-&amp;gt;setTextureSize(texSize, texSize);
    m_reflectionCamera-&amp;gt;attach((osg::Camera::BufferComponent) osg::Camera::COLOR_BUFFER0, texture);
    
    osg::StateSet *cameraState = m_reflectionCamera-&amp;gt;getOrCreateStateSet();
    cameraState-&amp;gt;setMode(GL_CULL_FACE, osg::StateAttribute::OFF | osg::StateAttribute::OVERRIDE);
    // Set reflection textures
    osg::StateSet* floorStateSet = reflectingSurface-&amp;gt;getOrCreateStateSet();
    floorStateSet-&amp;gt;setTextureAttributeAndModes(0, texture, osg::StateAttribute::ON);</code></pre><p>The complete reflection code is found in source/view/reflection.cpp and shaders/grid.(vert|frag)</p><h2>Distributed rendering with omegalib+osg+equalizer</h2><p>When programming an application in omegalib, the underlying displaysystem (equalizer) is mostly opaque to the programmer. It is however important to understand what is going on, when programming for a distributed, parallel rendering environment such as the Data Arena.</p><h5>What is parallel rendering ?</h5><p>Quoting the introduction chapter of the Equalizer programming guide:</p><p><img class="alignnone wp-image-1430" src="http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-277x300.png" alt="eq_sequence" width="522" height="565" /></p><p>(insert figure 1 of equalizer programming guide)</p><p>Figure ? illustrates the basic principle of any parallel rendering application. The typical OpenGL application, for example using GLUT, has an event loop which redraws the scene, updates application data based on received events, and eventually renders a new frame.<br />A parallel rendering application uses the same basic execution model, extending it by separating the rendering code from the main event loop. The rendering code is then executed in parallel on different resources, depending on the configuration chosen at runtime.</p><h5>How does parallel rendering work in omegalib ?</h5><p><img class="alignnone wp-image-1428" src="http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-300x184.png" alt="diagramOmegaEqFrame" width="919" height="564" /></p><p>(insert diagramOmegaFrame.png)</p><p>Rendering a frame with omegalib</p><p>The EqualizerDisplaySystem in omegalib runs the mainloop and calls the Configimpl startFrame method. ConfigImpl is a implementation of the Config class methods in Equalizer. For an in-depth discussion of the various Equalizer concepts, check out the Equalizer Programming Guide, it is recommended to read the Introduction chapter and the "Equalizer Parallel Rendering Framework" chapter.</p><p>The master, which drives the slaves rendering, first shares all Events to all nodes, each node is then reponsible for handling these Events. When handling events, commonly things such as calculating the new camera position are performed. Then other shared data is synced, for example a user could sync the position of an object across the nodes. Next the update call is performed on the master, which calls the update method on all registered modules. The update method internally calculates the correct offset of each screen camera, therefore the camera position should not be changed after the update traversal anymore. The update callback is also the place for the user to do any larger computations, such as running a physics simulation step. The startFrame(version) method tells all slave nodes to update themselves. It carries the frame version to sync all nodes to render the same frame. After all updates have been performed all nodes render the frame, which translates to calls to the osgModule, which executes culling and drawing traversals. Finally all nodes are synced on the end of the frame again.</p><p>Of course, this process has some intrecate issues that can arise when building complex applications. Often looking at the source code of omegalib, without having to extensively debug, can solve the issue as the code is fairly well commented.</p><h2>Data sharing and dynamic geometry</h2><p> </p><p><img class="alignnone  wp-image-1433" src="http://localhost/wordpress/wp-content/uploads/2016/08/troen2-window-300x106.png" alt="troen2-window" width="846" height="299" /></p><p> </p><p> </p><p>Any moving objects, which are synchronized over multiple screens should use the shared data commit/update pattern.<br />Equalizer handles distribution of datastreams to clients. Data can be added/extracted from the stream by calling</p><pre><code>// only run on master
    void commitSharedData(omega::SharedOStream&amp;amp; out)
    {
    out &amp;lt;&amp;lt; myPosition; } // only run on slaves! void updateSharedData(omega::SharedIStream&amp;amp; in) { in &amp;gt;&amp;gt; myPosition;
    }</code></pre><p>on a omegamodule class. We implemented this for all the relevant game classes using a listener pattern:<br />An interface is declared as</p><pre><code>class SharedDataListener {
    public:
    virtual void commitSharedData(omega::SharedOStream&amp;amp; out) = 0;
    virtual void updateSharedData(omega::SharedIStream&amp;amp; in) = 0;
    };</code></pre><p>and all classes which want to commit data to the stream inherit and implement this interface.<br />Then register the listening classes in you omega module and iteratively dispatch them. Note that the input must the same order as the output.</p><p>An example of synchronizing a dynamic gemeotry is the fence, which trails the bike in the Troen game.<br />First we create a Geometry with a vertex array and quad strip primitive set:</p><pre><code>void FenceView::initializeFence()
    {
    m_coordinates = new osg::Vec3Array();
    m_coordinates-&amp;gt;setDataVariance(osg::Object::DYNAMIC);
    
    m_geometry = new osg::Geometry();
    m_geometry-&amp;gt;setVertexArray(m_coordinates);
    
    // use VBOs, not display lists. important for dynamic updates
    m_geometry-&amp;gt;setUseDisplayList(false);
    
    m_drawArrays = new osg::DrawArrays(osg::PrimitiveSet::QUAD_STRIP, 0, 0);
    m_geometry-&amp;gt;addPrimitiveSet(m_drawArrays);
    }</code></pre><p>In our update method, we add a new fence part, when the bike has moved a certain distance. When porting osg applications to omegalib, always make sure that all modified vertex arrays and geometry is dirtied, as else there will be crashes even if it runs fine under pure osg.</p><pre><code>void FenceView::addFencePart(osg::Vec3 currentPosition)
    // game fence part
    m_coordinates-&amp;gt;push_back(currentPosition);
    m_coordinates-&amp;gt;push_back(currentPosition + osg::Vec3(0,0,10));
    // trigger new boundary calculation
    m_geometry-&amp;gt;dirtyBound();
    // very important to dirty vertex and attributes, as otherwise this will segfault in omegalib
    m_coordinates-&amp;gt;dirty();
    // update the size of the draw array
    m_drawArrays-&amp;gt;setCount(m_coordinates-&amp;gt;size());
    // if its the master, cache the position to use in the commit data method
    if (omega::SystemManager::instance()-&amp;gt;isMaster())
    {
    m_currentPositionCached = currentPosition;
    m_fenceUpdated = true;
    }</code></pre><p>We call the <em>addFencePart</em> method in our update method, but only on the master. On the client, the method is called, when it receives new shared data:</p><pre><code>void FenceView::commitSharedData(omega::SharedOStream&amp;amp; out)
    {
    out &amp;lt;&amp;lt; m_fenceUpdated &amp;lt;&amp;lt; m_currentPositionCached; // clear per frame states m_fenceUpdated = false; } void FenceView::updateSharedData(omega::SharedIStream&amp;amp; in) { in &amp;gt;&amp;gt; m_fenceUpdated &amp;gt;&amp;gt; m_currentPositionCached;
    if (m_fenceUpdated)
    addFencePart(m_currentPositionCached);
    }</code></pre><p>It is usually not necessary to sync the physics state, because the commit/update method is called every frame and the datalink in the Data Arena has a low latency. In Troen, we only synchronize the view transforms and do not execute the physics simulation on the child nodes at all. By doing this, we ensure that all nodes are in a consistent state and we do not have to worry about diverging physics states.</p><p>There can be situations however, where syncing the individual object transforms is not possible in a scalable manner, for example if a large particle system should be synced. In this case, the parameters of the particle system have to be synced and the simulation simultaneausly ran, setting random seeds uniformly.</p>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"5770c532d1e3d";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:1;s:2:"id";i:3;s:9:"widget_id";s:36:"1391920e-3d6d-43e3-a359-05f94389c1e0";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:4;a:14:{s:8:"features";a:3:{i:0;a:9:{s:15:"container_color";b:0;s:4:"icon";s:31:"fontawesome-arrow-circle-o-left";s:10:"icon_color";s:7:"#3d3d3d";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:17:"Previous Tutorial";s:8:"more_url";s:30:"/wordpress/tutorials/load-box/";}i:1;a:9:{s:15:"container_color";s:7:"#404040";s:4:"icon";s:0:"";s:10:"icon_color";s:7:"#FFFFFF";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:0:"";s:8:"more_url";s:0:"";}i:2;a:9:{s:15:"container_color";s:7:"#e8e8e8";s:4:"icon";s:32:"fontawesome-arrow-circle-o-right";s:10:"icon_color";s:7:"#3d3d3d";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:13:"Next Tutorial";s:8:"more_url";s:45:"/wordpress/tutorials/building-the-scenegraph/";}}s:5:"fonts";a:4:{s:13:"title_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:12:"text_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:17:"more_text_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:24:"so_field_container_state";s:6:"closed";}s:15:"container_shape";s:0:"";s:14:"container_size";s:4:"84px";s:19:"container_size_unit";s:2:"px";s:9:"icon_size";s:4:"24px";s:14:"icon_size_unit";s:2:"px";s:7:"per_row";i:3;s:10:"responsive";b:1;s:12:"_sow_form_id";s:13:"57873dc4344d9";s:10:"title_link";b:0;s:9:"icon_link";b:0;s:10:"new_window";b:0;s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Features_Widget";s:3:"raw";b:0;s:4:"grid";i:5;s:4:"cell";i:0;s:2:"id";i:4;s:9:"widget_id";s:36:"9cfce0d0-9f38-47ab-930d-0f36248ba8e9";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}}s:5:"grids";a:6:{i:0;a:2:{s:5:"cells";i:1;s:5:"style";a:3:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:1;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"10px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:2;a:2:{s:5:"cells";i:4;s:5:"style";a:4:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:3;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:4;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:5;a:2:{s:5:"cells";i:1;s:5:"style";a:0:{}}}s:10:"grid_cells";a:15:{i:0;a:2:{s:4:"grid";i:0;s:6:"weight";i:1;}i:1;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.227000000000000035083047578154946677386760711669921875;}i:2;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.6910000000000000586197757002082653343677520751953125;}i:3;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.082000000000000017319479184152442030608654022216796875;}i:4;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.2295751633986897466410681545312399975955486297607421875;}i:5;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.270424836601309726002995148519403301179409027099609375;}i:6;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.41907785081558956985503527903347276151180267333984375;}i:7;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.08092214918441091586753799447251367382705211639404296875;}i:8;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.2312091503267995340475948751191026531159877777099609375;}i:9;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.6937117253778286585230716809746809303760528564453125;}i:10;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.07507912429537184906269686734958668239414691925048828125;}i:11;a:2:{s:4:"grid";i:4;s:6:"weight";d:0.229575163398691384220029476637137122452259063720703125;}i:12;a:2:{s:4:"grid";i:4;s:6:"weight";d:0.69444444444444408670591428744955919682979583740234375;}i:13;a:2:{s:4:"grid";i:4;s:6:"weight";d:0.07598039215686445968511719684101990424096584320068359375;}i:14;a:2:{s:4:"grid";i:5;s:6:"weight";i:1;}}}
---
<h3 style="text-align: center;">Omegalib Tutorial Series</h3>
<h4>Tutorials</h4>
<ol>
 	<li style="text-align: left;"><a href="/wordpress/tutorials/load-box/">Load Geometry </a></li>
 	<li style="text-align: left;"><a href="/wordpress/tutorials/building-the-scenegraph/"><strong>Building The Scenegraph</strong></a></li>
 	<li style="text-align: left;"><a href="/wordpress/tutorials/defining-interactions/"><strong>Defining Interactions</strong></a></li>
 	<li style="text-align: left;"><a href="/wordpress/tutorials/advancedomegalibosgapplications/"><strong>Advanced Omegalib/OSG Applications</strong></a></li>
</ol>
<h1>Advanced omegalib/osg applications</h1>
Building visualizations with cyclops in python can produce stunning results and provides tools for many use cases, however there are certain applications which cannot be built with cyclops/python (without extending the cyclops c++ classes).
The underlying framework OpenSceneGraph is a powerful general purpose computer graphics library, which omegalib/cyclops uses to render computer graphics distributed across multiple displays.
Reasons for programming in osg/omegalib in c++ could be
<ul>
 	<li>You already have an existing application application using osg that you want to port to a multi-display setup in omegalib</li>
 	<li>Your application requires a large amount of data processing, dynamic geometry or special effects</li>
 	<li>You want to use third party c++ libraries, such as physics or sound engines</li>
 	<li>You want to use any methods of osg which are not accesible in cyclops</li>
</ul>
This tutorial assumes that you already have knowledge of programming in osg. If not, there are many good resources on the internet to learn programming the OpenSceneGraph, for example, the OpenSceneGraph Beginner’s Guide (<a href="http://ahux.narod.ru/olderfiles/1/OpenSceneGraph.3.0.Beginners.Guide-3208.pdf">http://ahux.narod.ru/olderfiles/1/OpenSceneGraph.3.0.Beginners.Guide-3208.pdf</a>) will get you started and contains many good examples. Going further, the OpenSceneGraph Cookbook (<a href="https://www.packtpub.com/game-development/openscenegraph-3-cookbook">https://www.packtpub.com/game-development/openscenegraph-3-cookbook</a>) provides recipes for many advanced topics.
<h3>Integration of osg and omegalib</h3>
Omegalib comes with support for openscenegraph as its rendering system in form of the omegaOsg module. It is important to know, how osg is actually integrated into omegalib and how rendering on distributed nodes work, to be able to efficiently develop applications in omegalib. Unfortunately, there is no official documentation of the omegaOsg module, which leaves programmers with only the source code to work with. Luckily, the binding code between osg and omegalib is rather small and not too complex.

<img class="alignnone wp-image-1429" src="http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-300x167.png" sizes="(max-width: 575px) 100vw, 575px" srcset="http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-300x167.png 300w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-768x429.png 768w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-1024x572.png 1024w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-830x463.png 830w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-230x128.png 230w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-350x195.png 350w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaOsg-480x268.png 480w" alt="diagramOmegaOsg" width="575" height="320" />

(insert diagramomegaOsg.png)

The omegaOsg module is a omegalib module which contains a osg::Node (the root) and registers a custom renderpass to the omegalib library. On each frame, the equalizer displaysystem calls the render method (on all nodes) of the renderpass class. Internally, the osgmodule copies over all transforms and properties of the omegalib camera to a osg::Camera and then the sceneview class performs the culling and rendering of the scenegraph. It is important to know, that no geometry is shared among nodes (in fact not even transforms are shared), the distributed nodes all run the same program and the renderloop execution is synced. Therefore transforms or dynamic geometry might have be synced by yourself. We will elaborate on this topic later again.
<h1>Building a standalone application</h1>
All examples, which come with the omegalib, are embedded into its environment and can only be built by invoking the general omegalib build command. If you are developing a larger application, this is really inconvenient and you probably want to seperate your application binaries, data, etc. from the binaries of omegalib. The omegalib wiki has a page on building standalone applications (<a href="https://github.com/uic-evl/omegalib/wiki/NewApplication">https://github.com/uic-evl/omegalib/wiki/NewApplication</a>), however it does not cover all the aspects needed to get a running environment.

Omegalib assumes that libraries are relative to the current binary runpath. If you are not running the application binary from omegalib/build/bin, however, the libraries needed will not be found.
You can add the directory of the binaries to the datamanager. In the cmakelists, add in a definition which points to the directory:
<pre><code>add_definitions(-DOMEGALIB_BIN_DIR="${Omegalib_DIR}/bin")</code></pre>
and in your code, before calling omain add the directory to the data manager so the libraries can be dynamically loaded:
<pre><code>omega::DataManager* dataManager = omega::SystemManager::instance()-&amp;gt;getDataManager();
dataManager-&amp;gt;addSource(new omega::FilesystemDataSource(OMEGALIB_BIN_DIR));</code></pre>
Next, we show a minimal example for building a standalone Application using omegalib. First, we declare our Module class. The class will be constructed by omegalib. The constructor creates a new osgmodule and reigsters it in the omega moduleservices. The actual initialization of the scene is done in initialize, which is called by omegalib on the first iteration of the renderloop.
<pre><code>#include &amp;lt;osgDB/ReadFile&amp;gt;
#include
#include &amp;lt;omegaOsg/omegaOsg.h&amp;gt;
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
};</code></pre>
Our initialize method simply loads a node file from the disk, using a modelname passed in over the commandline.
Omegalib initiliazes all its state in the module initiliaze traversal, whichs initializes equalizer, omgealib, omicron, etc.
Make sure that any calls with references to omegalib objects are invoked in the initialize method at the earliest.
<pre><code>void MinimalExample::initialize()
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
// attach any global state (shaders, lights, etc.) to this node
myOsg-&amp;gt;setRootNode(node);
}</code></pre>
Finally, the main methods creates a omegalib application, reads from the commandline and then executes the main omegalib loop.
<pre><code>///////////////////////////////////////////////////////////////////////////////
// Application entry point
int main(int argc, char** argv)
{
omega::Application app("minimalExample");
omega::oargs().newNamedString(':', "model", "model", "The osg model to load", sModelName);
return omega::omain(app, argc, argv);
}</code></pre>
<h3>Overriding omegalib file loaders</h3>
Omegalib registers custom file loaders, which in some cases override the standard osg plugins. Sometimes, this can lead to unexpected behaviour: for example the tga of omegalib does not implement the full tga standard and loading images with 24bpp, which loaded fine with the osgdb_tga plugin will not work anymore. To use a certain osg loader, you have two options: load data/textures/nodes before the omegalib <code>omain</code> call or manually remove loaders from registry. The first method is preferred, if you only need to load files once and can do this before starting the actual application. If not, the second method provides a (little bit hacky) workaround.

To remove a loader from the osgDB registry, first store the filepaths before running <code>omain</code>:
<pre><code>for (auto libPath : osgDB::Registry::instance()-&amp;gt;getLibraryFilePathList ())
{
_storedLibPaths += libPath + ":";
}</code></pre>
storedLibPaths should then contain the correct directories of plugins (the standard osg directories), you want to load.
When running omain, the omegaOsg initiliaze method will set the plugin library searchpath automatically to a directory containing the loaders you don’t want to use.
To revert this, reset the osgDB::Registry library search path to its original path.
Then, remove the reader writer which is giving troubles from the registry, this will cause a reload on invocation using the plugins in the correct path
<pre><code>// The omegaOsg instance() method initiliazes it and configures its libpaths, so it is safe
// to revert these libpaths in our initialize method
MinimalExample::initialize(){
osgDB::Registry* reg = osgDB::Registry::instance();
reg-&amp;gt;setLibraryFilePathList(_storedLibPaths);
osgDB::Registry::instance()-&amp;gt;removeReaderWriter(
osgDB::Registry::instance()-&amp;gt;getReaderWriterForExtension("tga"));
// now you can load your tga files, and they will be correctly loaded by the osg loader plugin</code></pre>
<h3>Debugging your application</h3>
Debugging computer graphics application can be quite hard, as the errors can manifest themselves as visual artefacts or other errors, which are quite hard to trace down.
Setting the notify and log level to debug can help tracing down many errors:
set the <code>OSG_NOTIFY_LEVEL=DEBUG</code> in your environment for detailed osg debug messages
pass the <code>--log v</code> flag to your application, for omegalib debug messages

Crashes which happen during the initiliaze call can sometimes be hard to debug, as no actual debug messages are displayed. Shifting the method call into your gameloop to test assumptions often helps in getting more useful error messages.

When debugging an application over multiple nodes in equalizer, getting debug traces can be tricky. One way to get information about segfaults is to have a custom launcher script for children in the .cfg file and log the stack trace to a a file:
Set the nodelauncher in your .cfg file to a custom script:
<pre><code>nodeLauncher = "ssh -n %h startTroenSlave.sh %d %c"</code></pre>
startTroenSlave. sh:
<pre><code>D=$1
C=$2
cd $D
... # set other environment variables
export LD_LIBRARY_PATH=$D:${D}/osg:${D}/osg/osgPlugins-3.3.0:$LD_LIBRARY_PATH
# -r is for remote log
gdb -x gdbcommand.txt --args $C -r --log v $*</code></pre>
gdbcommand.txt:
<pre><code>set logging file gdb.txt
set logging on
run
bt</code></pre>
<h3>Gotchas when using omegaOsg</h3>
Although omegaOsg allows the usage of most osg concepts, some osg features do not work when used in omegalib
<ul>
 	<li>rendering masks are not processed by omegaOsg, therefore all geometry will be displayed twice if you are using two cameras with different camera masks. If you experience similar artifacts as in figure 1</li>
 	<li><img class="alignnone wp-image-1431" src="http://localhost/wordpress/wp-content/uploads/2016/08/flickering-300x188.png" sizes="(max-width: 489px) 100vw, 489px" srcset="http://localhost/wordpress/wp-content/uploads/2016/08/flickering-300x188.png 300w, http://localhost/wordpress/wp-content/uploads/2016/08/flickering-768x480.png 768w, http://localhost/wordpress/wp-content/uploads/2016/08/flickering-1024x640.png 1024w, http://localhost/wordpress/wp-content/uploads/2016/08/flickering-830x519.png 830w, http://localhost/wordpress/wp-content/uploads/2016/08/flickering-230x144.png 230w, http://localhost/wordpress/wp-content/uploads/2016/08/flickering-350x219.png 350w, http://localhost/wordpress/wp-content/uploads/2016/08/flickering-480x300.png 480w" alt="flickering" width="489" height="306" /></li>
 	<li>(insert flickering.png), you might have probably have multiple cameras rendering the scene with either ignored camera mask settings, culling settings or render order settings.</li>
 	<li>You do not have access to the actual osg rendering camera before rendering. There is however a framefinished callback, which gives you access to the rendering internals</li>
</ul>
<h1>Hands On: Integrating a game into omegalib</h1>
In this section, we will show a few common problems arising, when integrating highly interactive applications such as games. We will show the solution to these problems in the context of integrating a game using osg and bullet physics, called Troen. For source reference and more in-depth examples of integrating a fairly advanced osg application into omegalib, you can find the source of the game on <a href="https://github.com/MaxReimann/Troen">github</a>.

(insert troen-2window.png)

screenshot of the game running across two windows
<h3>Setting transforms on omega cameras:</h3>
The main interaction between omegalib and osg concerns the setting and updating of cameras. When implementing or porting an application with dynamic cameras, which can move around, rotate/orbit, etc. care must be taken to apply the correct transform.
In osg, cameras can be part of the scene graph in lower levels. When their reference frame is set to RELATIVE_RF, they will reference all underlying geomertry from a relative coordinate frame. However, omega cameras are commonly set in an absolute reference frame. When calculating transforms, e.g. taking the output of a osg camera manipulator, care must be taken to convert the local transform into the world transform.

An example for such a transformation is the updateCamera method of the nodetrackermanipulator, which orbits around a tracked node and sets the camera in every frame. The nodetrackermanipulator computes a center and rotation around the tracked node and when updating the camera, it uses the inverse of this transform to set its lookat:
<pre><code>void NodeTrackerManipulator::updateCamera(osg::Camera&amp;amp; camera)
{
osg::Vec3d eye, center, up, unused;
osg::Matrixd invMatrix = getInverseMatrix();
invMatrix.getLookAt(eye, center, up);
camera.setViewMatrixAsLookAt(eye,center,up);
}</code></pre>
The <em>omega::Camera</em> also has a lookat method, however, if you update the <em>omega::Camera</em> by using its lookat method, it will produce weird, incorrect rotations, which are a symptom of the wrong coordinate frame of the center vector: The coordinate frame of the calculated center vector is in the camera view space but should really be in the world space.
<pre><code>void NodeTrackerManipulator::updateOmegaCamera(omega::Camera *cam){
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
cam-&amp;gt;setPosition( OSGVEC3_OMEGA(eye) );
cam-&amp;gt;lookAt(oCenterVec, OSGVEC3_OMEGA(up) );
}</code></pre>
<h3>Executing pre-render cameras</h3>
In osg, cameras can have different render orders: Pre-render, normal, and post-render.
Pre-render cameras are often used, to render a certain effect into a texture, which are then used in the actual rendering of the scene. A common use case is rendering reflections on surfaces.

In our game, we want to render a very shiny surface. A pre-render camera is used, to render the scene with a flipped z-transform:

(todo: extract and insert snapshot from presentation)

Our camera therefore moves with the main camera and its position has to be updated accordingly. Setting the transformation of the reflection camera at the right time is crucial, because setting it too late will result in the reflection lagging one frame behind and too early will result in the main camera not being updated with the new transform yet. A hacky method could be to directly copy over the main camera transform to the reflection camera, when it is set in the cameramanipulator. However, this could break as soon as we have other methods influencing the camera position: imagine a method setting the field of view dynamically or a method preventing cameras flying into obstacles. Another problem is, that in omega multiple windows can be created on one machine, each update method is therefore executed once for each camera.If you have two windows, you will probably see constantly switching reflections between the windows, because the transform is applied to the wrong reflection camera. What we actually want is to have a camera callback executed right before the reflection camera is rendered.

In osg, the cull traverse decides what objects to render and what to cull away. The Cullvisitor actually computes the correct transformation of each node and pushes objects into the the draw stage, which is executed after the Cullvisitor has visited all nodes. Therefore, the CullCallback is the latest point, we can influence a nodes transform before it is rendered. However the cullcallback is executed after the node transforms have already been pushed into the render stage.If we would therefore execute the cullcallback directly on the camera, we would not see any positional change. We must therefore set the cullcallback on a node above the camera (we named it cameragroup) and then access its child:
<pre><code>class CUpdateCameraCallback : public osg::NodeCallback
{
public:
CUpdateCameraCallback() : NodeCallback(){}
void operator()(osg::Node *node, osg::NodeVisitor *nv)
{
// only execute this callback if in the culling stage
if (nv-&amp;gt;getVisitorType() == osg::NodeVisitor::CULL_VISITOR)
{
// the camera is the only child of the camera group
osg::Camera *camera = dynamic_cast(node-&amp;gt;asGroup()-&amp;gt;getChild(0));
// The cullvisitor holds information about the current (main) camera
osgUtil::CullVisitor* cv = static_cast&amp;lt;osgUtil::CullVisitor*&amp;gt;(nv);
if (camera != NULL)
{
// copy over the transforms of the main camera
camera-&amp;gt;setProjectionMatrix(cv-&amp;gt;getCurrentCamera()-&amp;gt;getProjectionMatrix() );
camera-&amp;gt;setViewMatrix(cv-&amp;gt;getCurrentCamera()-&amp;gt;getViewMatrix());
// set the eye point in the shader
g_cameraEyeU-&amp;gt;set(cv-&amp;gt;getEyePoint());
}
}
this-&amp;gt;traverse(node, nv);
}
};</code></pre>
Now we show , how to set up the camera correctly:
<pre><code>cameraGroup = new osg::Group();
m_reflectionCamera = new osg::Camera();
reflectionTransform = new osg::MatrixTransform();
cameraGroup-&amp;gt;addChild(m_reflectionCamera);
m_reflectionCamera-&amp;gt;addChild(reflectionTransform);
m_reflectionCamera-&amp;gt;setClearMask(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);
// render the camera before the main camera
m_reflectionCamera-&amp;gt;setRenderOrder(osg::Camera::PRE_RENDER);
// write into a frame buffer later used as texture
m_reflectionCamera-&amp;gt;setRenderTargetImplementation(osg::Camera::FRAME_BUFFER_OBJECT);
// prevent near clipping
m_reflectionCamera-&amp;gt;setComputeNearFarMode(osg::CullSettings::DO_NOT_COMPUTE_NEAR_FAR);
// calculate all transforms in world space
m_reflectionCamera-&amp;gt;setReferenceFrame(osg::Transform::ABSOLUTE_RF);
// set the viewport to the size of the texture
m_reflectionCamera-&amp;gt;setViewport(0, 0, texSize, texSize);
m_reflectionCamera-&amp;gt;setClearDepth(1.0);
//Important: set our cull callback on the cameragroup, not the camera itself
m_cameraGroupCallback = new CUpdateCameraCallback();
cameraGroup-&amp;gt;setCullCallback(m_cameraGroupCallback);</code></pre>
Calculating the actual reflection does not need any extra adjustements for distributed rendering, but is shown here for reference:
<pre><code>// add a clipping plane, to clip everything below z=0.0.
//beware, that vec4(a,b,c,d) is a plane equation with a,b,c the plane normal and d the plane height
m_reflectionClipPlane = new osg::ClipPlane(0, osg::Vec4d(0.0, 0.0, 1.0, 0.0));
m_reflectionClipNode = new osg::ClipNode;
m_reflectionClipNode-&amp;gt;addClipPlane(m_reflectionClipPlane);
reflectionTransform-&amp;gt;addChild(m_reflectionClipNode);
// mirror the scene along the z axis
reflectionTransform-&amp;gt;setMatrix(osg::Matrix::scale(1.0, 1.0, -1.0));
// render the reflection camera into a texture
osg::ref_ptr texture = new osg::Texture2D();
texture-&amp;gt;setTextureSize(texSize, texSize);
m_reflectionCamera-&amp;gt;attach((osg::Camera::BufferComponent) osg::Camera::COLOR_BUFFER0, texture);
osg::StateSet *cameraState = m_reflectionCamera-&amp;gt;getOrCreateStateSet();
cameraState-&amp;gt;setMode(GL_CULL_FACE, osg::StateAttribute::OFF | osg::StateAttribute::OVERRIDE);
// Set reflection textures
osg::StateSet* floorStateSet = reflectingSurface-&amp;gt;getOrCreateStateSet();
floorStateSet-&amp;gt;setTextureAttributeAndModes(0, texture, osg::StateAttribute::ON);</code></pre>
The complete reflection code is found in source/view/reflection.cpp and shaders/grid.(vert|frag)
<h2>Distributed rendering with omegalib+osg+equalizer</h2>
When programming an application in omegalib, the underlying displaysystem (equalizer) is mostly opaque to the programmer. It is however important to understand what is going on, when programming for a distributed, parallel rendering environment such as the Data Arena.
<h5>What is parallel rendering ?</h5>
Quoting the introduction chapter of the Equalizer programming guide:

<img class="alignnone wp-image-1430" src="http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-277x300.png" sizes="(max-width: 522px) 100vw, 522px" srcset="http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-277x300.png 277w, http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-768x832.png 768w, http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-945x1024.png 945w, http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-830x900.png 830w, http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-230x249.png 230w, http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-350x379.png 350w, http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence-480x520.png 480w, http://localhost/wordpress/wp-content/uploads/2016/08/eq_sequence.png 1085w" alt="eq_sequence" width="522" height="565" />

(insert figure 1 of equalizer programming guide)

Figure ? illustrates the basic principle of any parallel rendering application. The typical OpenGL application, for example using GLUT, has an event loop which redraws the scene, updates application data based on received events, and eventually renders a new frame.
A parallel rendering application uses the same basic execution model, extending it by separating the rendering code from the main event loop. The rendering code is then executed in parallel on different resources, depending on the configuration chosen at runtime.
<h5>How does parallel rendering work in omegalib ?</h5>
<img class="alignnone wp-image-1428" src="http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-300x184.png" sizes="(max-width: 533px) 100vw, 533px" srcset="http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-300x184.png 300w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-768x470.png 768w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-1024x627.png 1024w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-830x508.png 830w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-230x141.png 230w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-350x214.png 350w, http://localhost/wordpress/wp-content/uploads/2016/08/diagramOmegaEqFrame-480x294.png 480w" alt="diagramOmegaEqFrame" width="533" height="327" />

(insert diagramOmegaFrame.png)

Rendering a frame with omegalib

The EqualizerDisplaySystem in omegalib runs the mainloop and calls the Configimpl startFrame method. ConfigImpl is a implementation of the Config class methods in Equalizer. For an in-depth discussion of the various Equalizer concepts, check out the Equalizer Programming Guide, it is recommended to read the Introduction chapter and the "Equalizer Parallel Rendering Framework" chapter.

The master, which drives the slaves rendering, first shares all Events to all nodes, each node is then reponsible for handling these Events. When handling events, commonly things such as calculating the new camera position are performed. Then other shared data is synced, for example a user could sync the position of an object across the nodes. Next the update call is performed on the master, which calls the update method on all registered modules. The update method internally calculates the correct offset of each screen camera, therefore the camera position should not be changed after the update traversal anymore. The update callback is also the place for the user to do any larger computations, such as running a physics simulation step. The startFrame(version) method tells all slave nodes to update themselves. It carries the frame version to sync all nodes to render the same frame. After all updates have been performed all nodes render the frame, which translates to calls to the osgModule, which executes culling and drawing traversals. Finally all nodes are synced on the end of the frame again.

Of course, this process has some intrecate issues that can arise when building complex applications. Often looking at the source code of omegalib, without having to extensively debug, can solve the issue as the code is fairly well commented.
<h2>Data sharing and dynamic geometry</h2>
Any moving objects, which are synchronized over multiple screens should use the shared data commit/update pattern.
Equalizer handles distribution of datastreams to clients. Data can be added/extracted from the stream by calling
<pre><code>// only run on master
void commitSharedData(omega::SharedOStream&amp;amp; out)
{
out &amp;lt;&amp;lt; myPosition; } // only run on slaves! void updateSharedData(omega::SharedIStream&amp;amp; in) { in &amp;gt;&amp;gt; myPosition;
}</code></pre>
on a omegamodule class. We implemented this for all the relevant game classes using a listener pattern:
An interface is declared as
<pre><code>class SharedDataListener {
public:
virtual void commitSharedData(omega::SharedOStream&amp;amp; out) = 0;
virtual void updateSharedData(omega::SharedIStream&amp;amp; in) = 0;
};</code></pre>
and all classes which want to commit data to the stream inherit and implement this interface.
Then register the listening classes in you omega module and iteratively dispatch them. Note that the input must the same order as the output.

An example of synchronizing a dynamic gemeotry is the fence, which trails the bike in the Troen game.
First we create a Geometry with a vertex array and quad strip primitive set:
<pre><code>void FenceView::initializeFence()
{
m_coordinates = new osg::Vec3Array();
m_coordinates-&amp;gt;setDataVariance(osg::Object::DYNAMIC);
m_geometry = new osg::Geometry();
m_geometry-&amp;gt;setVertexArray(m_coordinates);
// use VBOs, not display lists. important for dynamic updates
m_geometry-&amp;gt;setUseDisplayList(false);
m_drawArrays = new osg::DrawArrays(osg::PrimitiveSet::QUAD_STRIP, 0, 0);
m_geometry-&amp;gt;addPrimitiveSet(m_drawArrays);
}</code></pre>
In our update method, we add a new fence part, when the bike has moved a certain distance. When porting osg applications to omegalib, always make sure that all modified vertex arrays and geometry is dirtied, as else there will be crashes even if it runs fine under pure osg.
<pre><code>void FenceView::addFencePart(osg::Vec3 currentPosition)
// game fence part
m_coordinates-&amp;gt;push_back(currentPosition);
m_coordinates-&amp;gt;push_back(currentPosition + osg::Vec3(0,0,10));
// trigger new boundary calculation
m_geometry-&amp;gt;dirtyBound();
// very important to dirty vertex and attributes, as otherwise this will segfault in omegalib
m_coordinates-&amp;gt;dirty();
// update the size of the draw array
m_drawArrays-&amp;gt;setCount(m_coordinates-&amp;gt;size());
// if its the master, cache the position to use in the commit data method
if (omega::SystemManager::instance()-&amp;gt;isMaster())
{
m_currentPositionCached = currentPosition;
m_fenceUpdated = true;
}</code></pre>
We call the <em>addFencePart</em> method in our update method, but only on the master. On the client, the method is called, when it receives new shared data:
<pre><code>void FenceView::commitSharedData(omega::SharedOStream&amp;amp; out)
{
out &amp;lt;&amp;lt; m_fenceUpdated &amp;lt;&amp;lt; m_currentPositionCached; // clear per frame states m_fenceUpdated = false; } void FenceView::updateSharedData(omega::SharedIStream&amp;amp; in) { in &amp;gt;&amp;gt; m_fenceUpdated &amp;gt;&amp;gt; m_currentPositionCached;
if (m_fenceUpdated)
addFencePart(m_currentPositionCached);
}</code></pre>
It is usually not necessary to sync the physics state, because the commit/update method is called every frame and the datalink in the Data Arena has a low latency. In Troen, we only synchronize the view transforms and do not execute the physics simulation on the child nodes at all. By doing this, we ensure that all nodes are in a consistent state and we do not have to worry about diverging physics states.

There can be situations however, where syncing the individual object transforms is not possible in a scalable manner, for example if a large particle system should be synced. In this case, the parameters of the particle system have to be synced and the simulation simultaneausly ran, setting random seeds uniformly.

&nbsp;
<p class="sow-more-text"><a href="/wordpress/tutorials/load-box/"> Previous Tutorial </a></p>
<p class="sow-more-text"><a href="/wordpress/tutorials/building-the-scenegraph/"> Next Tutorial </a></p>