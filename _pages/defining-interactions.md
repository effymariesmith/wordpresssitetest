---
ID: 902
post_title: Defining Interactions
author: davm
post_date: 2016-07-15 00:19:25
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/tutorials/defining-interactions/
published: true
panels_data:
  - |
    a:3:{s:7:"widgets";a:6:{i:0;a:6:{s:5:"title";s:0:"";s:4:"text";s:61:"<h3 style="text-align: center;">Omegalib Tutorial Series</h3>";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578723843cea2";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:0;s:9:"widget_id";s:36:"1ea35202-0ffb-4952-88db-1380842ca3f4";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:1;a:5:{s:8:"headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:4:"left";s:24:"so_field_container_state";s:4:"open";}s:12:"sub_headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:6:"center";s:24:"so_field_container_state";s:4:"open";}s:7:"divider";a:8:{s:5:"style";s:5:"solid";s:6:"weight";s:4:"thin";s:5:"color";b:0;s:11:"side_margin";s:4:"20px";s:16:"side_margin_unit";s:2:"px";s:10:"top_margin";s:4:"20px";s:15:"top_margin_unit";s:2:"px";s:24:"so_field_container_state";s:4:"open";}s:12:"_sow_form_id";s:13:"57871dc1b3fe7";s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Headline_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:1;s:9:"widget_id";s:36:"42c24578-cfd7-4dd5-8d52-e5b5178da0b8";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:2;a:6:{s:5:"title";s:0:"";s:4:"text";s:564:"<h4>Tutorials</h4>
    <ol>
     	<li style="text-align: left;"><a href="/wordpress/tutorials/load-box/">Load Geometry </a></li>
     	<li style="text-align: left;"><a href="/wordpress/tutorials/building-the-scenegraph/"><strong>Building The Scenegraph</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/tutorials/defining-interactions/"><strong>Defining Interactions</strong></a></li>
            <li style="text-align: left;"><a href="/wordpress/tutorials/advancedomegalibosgapplications/"><strong>Advanced Omegalib/OSG Applications</strong></a></li>
    
    </ol>
    
    ";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"576b4c626e8f5";s:11:"panels_info";a:6:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:4:"grid";i:1;s:4:"cell";i:0;s:2:"id";i:2;s:9:"widget_id";s:36:"4a98973e-09c0-48a2-923d-fcbc887ca755";s:5:"style";a:2:{s:27:"background_image_attachment";b:0;s:18:"background_display";s:4:"tile";}}}i:3;a:4:{s:5:"title";s:0:"";s:4:"text";s:255:"In the following tutorials we will show you, how to create, import and display cool models and bring them to the Data Arena.
    
    Graphics programming experience is not a prerequisite, although it will help to have some understanding of the graphics pipeline.";s:6:"filter";b:0;s:11:"panels_info";a:7:{s:5:"class";s:14:"WP_Widget_Text";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:1;s:2:"id";i:3;s:9:"widget_id";s:36:"8458d952-2849-47ac-8244-b11bcc3949d1";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:4;a:6:{s:5:"title";s:0:"";s:4:"text";s:15607:"<h3>Defining your own interactions</h3>
    In this tutorial you will learn
    <ul>
     	<li>how to implement custom interaction handlers</li>
     	<li>how to export 3D models from a modelling software and import them to omegalib</li>
     	<li>how to display text</li>
    </ul>
    Suppose you want to visualize a portion of a city and enable the user to query information about particular buildings by clicking on them.
    In this tutorial you will build and export a 3d model of a building block, assign values to the building and define interaction handlers to process click events and then display information about the building in a text-over block.
    <h3>Building and exporting the model</h3>
    Fire up your 3D modelling tool of choice, and start building your model. This tutorial uses Blender, but the workflow is similar to other 3D modelling tools.
    
    A small building block model can be made, by importing a highly detailed map section, covering the buildings with polygons and extruding them. We have built a simple model of the UTS:
    
    (insert blender.png)
    
    Now, the model has to be exported to omegalib. The underlying OpenSceneGraph can understand many common formats (.obj, .3ds, .ply, …), however the most convinient way is to export into .osgt, the native osg format. This format explicitly defines the scenegraph is easibly readable for humans. Check <a href="http://trac.openscenegraph.org/projects/osg//wiki/Community/Plugins">http://trac.openscenegraph.org/projects/osg//wiki/Community/Plugins</a> for available exporters, there are exporters for 3D Studio Max, Maya and Blender (plugins for other model packages might exist elsewhere). The best plugin for Blender is maintained under <a href="https://github.com/cedricpinson/osgexport">https://github.com/cedricpinson/osgexport</a>, use this to export your scene into .osgt, the default settings for the export are appropriate.
    
    Now have a look at the osgt file to grasp, what the scenegraph looks like. There is a root object and child objects. Depending on the object type, it has material, vertex and/or texture data assigned. Note that in Blender, only the materials set for the Blender renderer (not cycles) are exported. You can import and show the pieces of your model in python:
    <pre><code class="language-python">modelInfo = ModelInfo()
    modelInfo.name = "UTS"
    modelInfo.path = "UTS.osgt"
    modelInfo.size = 65.0
    #its important to not use the optimizer, 
    # so that all seperately defined objects stay seperate
    modelInfo.optimize = False
    # loads model, but does not attach it yet
    getSceneManager().loadModel(modelInfo)
    # loads model by name, and attaches it to scene
    model = StaticObject.create("UTS")
    #print out all objects defined in the model
    for pieceName in  model.listPieces("Root"):
        print pieceName</code></pre>
    When executing this code, the diplayed model should look similar to this:
    (insert cyclops1.png)
    
    The camera is oriented horizontally to the model and can not be moved.
    We want to the camera a more interesting camera angle and position. Trying out different positions from python
    is a lot of tiring manual work and therefore we want to use the camera view transformation defined in our modelling program.
    To get this, find out the name of your camera in Blender (or other modelling program) and check, if this name is present as a node in the .osgt file (which it should be).
    
    To get the position, extract the node from the model graph:
    <pre><code class="language-python">cam = model.getPiece("Root/Camera")
    print cam.getPosition()</code></pre>
    The getPiece method returns an <code>Entity</code>, which is still anchored in the scenegraph, and we can retrieve its position.
    The next thing we need is the camera lookat and up vector. We will avoid having to calculate a orientation to lookat transformation by setting the camera lookat point ourself. In Blender (or other program), create an Empty at the center position of the camera and set the camera to its parent. By doing this, the Empty, which you can call the CameraFocus, will always stay centered in the camera view. Now export the scene again and retrieve the camerafocus position by
    <pre><code class="language-python">focus = cam.getPiece("CameraFocus")
    worldfocusPos = cam.convertLocalToWorldPosition( focus.getPosition() )</code></pre>
    Note that the focus position is local to its parent and has to be transformed into world space.
    
    You will use these positions in the next step.
    <h3>View Manipulators</h3>
    In previous tutorials, we have used the <code>GeometryHandler</code> class to walk though the model in a first-person style.
    In this tutorial, we want to be able to rotate, pan and zoom the model similar to the 3D view in modelling programs.
    The Data Arena version of cyclops offers a <code>ManipulatorController</code> class, which makes it possible to use <em>osg::CameraManipulator</em> with omegalib cameras.
    
    Create a class which instantiates both a <code>ManipulatorController</code> and a <code>TerrainManipulator</code> and set the ManipulatorController to use the TerrainManipulator.
    
    <code>TerrainManipulator</code> is a wrapper around <code>osg::TerrainManipulator</code> and defines zooming, panning and rotating around terrains with horizontal terrain zooming.
    Other currently implemented Manipulators are: <code>OrbitManipulator</code> and <code>NodeTrackerManipulator</code>.
    <pre><code class="language-python">class CameraHandler:
        def __init__(self):
            # controller for camera manipulators
            self.camManipController = CameraManipulator.create()
            # the actual camera manipulator
            self.manipulator = TerrainManipulator.create()
            self.camManipController.setManipulator(self.manipulator)
    
        def onEvent(self):
            """Callback for omegalib to register with `setEventFunction`."""
            self.camManipController.onEvent(getEvent())</code></pre>
    Now, we can instatiate the CameraHandler and set it to handle our model:
    <pre><code class="language-python">...
    camManipulator = CameraHandler()
    camManipulator.setCameraHome(cam.getPosition(), worldFocusPos)
    
    setEventFunction(camManipulator.onEvent)</code></pre>
    Rotating, panning and zooming should now be possible.
    
    By default, the manipulators use the mouse.Using different input devices is also possible, by using a different <code>EventHandler</code>. EventHandlers transform input of various devices into mouse events for osg. To use a playstation controller, for instance, add a <code>MyControllerAdapter</code> in the constructor of the CameraHandler.
    <pre><code class="language-python">    def __init__(self):
            ...
            self.eventAdapter = MyControllerAdapter(self.manipulator)
            self.camManipController.setEventAdapter(self.eventAdapter)
    
            def onUpdate(self, frame, time, dt):
                if self.eventAdapter != None:
                    self.eventAdapter.onUpdate(self.camManipController)
    ...
    setUpdateFunction(camManipulator.onUpdate)</code></pre>
    The onUpdate function ensures smooth transformation for controller events.
    <h3>Selecting models in the view</h3>
    To enable the user to interact with the model, we want to him to to be able to hover over model parts, make selections and get visual feedback. We want to color a node if the cursor is hover over it:
    (insert cyclops2.png)
    
    The first step is to check if our mouse is hovering over a model.
    Define a new class called SceneHandler, and add a onEventMethod. Modularlizing your code in camerahandlers, scenehandlers, modelcontrollers, etc.. is always a good idea to encourage loose coupling and reusability of components.
    <pre><code class="language-python">class SceneHandler:
        def__init__(self):
            pass
    
        def onEvent(self):
            e = getEvent()
            if(e.getServiceType() == ServiceType.Pointer or e.getServiceType() == ServiceType.Wand):
                r = getRayFromEvent(e)
    
                # Button mappings are different when using wand or mouse
                confirmButton = EventFlags.Button1
                if(e.getServiceType() == ServiceType.Wand): confirmButton = EventFlags.Button5
    
                if(r[0]): 
                    # When the confirm button is pressed:
                    if(e.isButtonDown(confirmButton)):
                        self.mouseClickPos = e.getPosition()
                        querySceneRay(r[1], r[2], self.onClicked, QueryFlags.QuerySort | QueryFlags.QueryFirst)
                    else:
                        querySceneRay(r[1], r[2], self.colorHovered, QueryFlags.QuerySort | QueryFlags.QueryFirst)</code></pre>
    Cyclops offers functions which makes this quite easy:
    <ul>
     	<li>getRayFromEvent: returns a ray which has its startpoint set at the camera eye position and the direction towards the mouse pointer</li>
     	<li>querySceneRay: Makes intersection tests between the ray and all nodes and executing a callback for every node that is returned (hit). We sort the scene from shortest to longest distance and return closest node. Only nodes, which are set as <em>selectable</em> will be queried.</li>
    </ul>
    Until now, we only have one root <code>omega::SceneNode</code> in the scene. Note that this is a different type of node than <code>osg::Node</code>. To make different parts of the model selectable, all seperate parts of the model have to be extracted into a SceneNode.
    Using this selection method is most useful, if there is a pointer device (mouse or wand) available.
    
    Wrap the model loading part into a new class called <em>ModelController</em> and add a new method <em>setSelectableParts</em>, which is called after loading in the constructor:
    <pre><code class="language-python">#in class ModelController:
        def setSelectableParts(self):    
            self.selectableNodes = []
            self.model.setSelectable(False)
            for pieceName in self.model.listPieces("Root"):
                if pieceName == "Camera": #dont extract the camera yet
                    continue
                mod = self.model.getPiece("Root/" + pieceName)
                if pieceName.startswith("cb"):
                    if mod != None:
                        mod.setSelectable(True)
                        self.selectableNodes.append(mod)
                else:
                    mod.setSelectable(False)</code></pre>
    In Blender, we have named every building using the "CBxx" naming. We only want to make UTS building nodes selectable, so we set everything which does not start with "cb" to non-selectable. We also don’t want to extract the camera, as we do this later to query its position/lookat and a piece can only be extracted once because a new scenenode is created and maintained using its name.
    
    Next, we define the callback to be called, when there is a event (except for mouse clicks):
    <pre><code class="language-python">    def colorHovered(self, node, dist):
            if node != None:
                for n in self.modelController.getSelectableNodes():
                    if n.getName() == node.getName():
                        n.getMaterial().setColor(Color(1.0,1.0,1.0,1.0), Color(0.2, 0.2,0.2, 0.2))
                    else:
                        n.getMaterial().setColor(Color(0.2,0.2,0.2,1.0), Color(0.0, 0.0,0.0, 0.0))
            else:
                for n in self.modelController.getSelectableNodes():
                    n.getMaterial().setColor(Color(0.2,0.2,0.2,1.0), Color(0.0, 0.0,0.0, 0.0))</code></pre>
    The <em>querySceneRay</em> returns a node which was found and its distance. The node can also be None, if nothing was found.
    We set the model part’s material to a bright white color, if it is under the cursor and all other buildings to a more darkish color. If no node was found, set all parts to the same darkish color.
    Now you should be able to see you selections by hovering over buildings.
    <h3>Displaying Information on the UI</h3>
    To complete our example, it would be nice to show information about the buildings when clicked. Getting information into the visualization is always application specific, but one simple way to get in information is to define a json dictionary which maps node names to information.
    
    Displaying the height of the building will suffice for this example:
    <pre><code class="language-json">{
     "buildings":{
             "cb1" : {"height": 150},
             "cb2" : {"height": 20},
             "cb3" : {"height": 15},
             "cb4" : {"height": 15},
             "cb5" : {"height": 20},
             "cb6" : {"height": 60},
             "cb10" : {"height": 35},
             "cb11" : {"height": 40}
            }
    }</code></pre>
    Omegalib offers some UI functionality, which makes it easy to define 2D widgets, which are rendered infront of the scene.
    <pre><code class="language-python">class SceneHandler:
        def __init__(self, modelController):
            self.modelController = modelController
    
            self.ui = UiModule.createAndInitialize()
            self.wf = self.ui.getWidgetFactory()
            self.uiroot = self.ui.getUi()
    
            containerSize = Vector2(300, 100)
            self.container = self.wf.createContainer('container', self.uiroot, ContainerLayout.LayoutVertical)
            self.container.setAutosize(False)
            self.container.setSize(containerSize)
    
            self.label = self.makeLabel("label1")
            self.label2 = self.makeLabel("label2")
            self.lastMousePos = None
    
            with open('buildinginfo.json') as data_file:    
                self.buildinginfo = json.load(data_file)
    
        def makeLabel(self, name):
            label = self.wf.createLabel(name, self.container, '')
            label.setAutosize(True)
            label.setStyle('font: fonts/arial.ttf 30; color: white; alpha: 1.0;')
            label.setStyleValue('align', 'middle-left') 
            label.setVisible(False)
            return label</code></pre>
    The UI works similar to other UI frameworks. A <a href="https://github.com/uic-evl/omegalib/wiki/Container">Container</a> is needed to hold <a href="https://github.com/uic-evl/omegalib/wiki/Widget">Widgets</a>, such as <a href="https://github.com/uic-evl/omegalib/wiki/Label">Labels</a>, <a href="https://github.com/uic-evl/omegalib/wiki/Button">Buttons</a> and <a href="https://github.com/uic-evl/omegalib/wiki/Slider">Sliders</a>. There is no textwrap in omegalib, so for every line, a new label has to be created.
    
    The <code>json</code> library is used, to convert the json file into a python dictionary.
    
    The last step is to actually display the text, when the building is clicked. We define the querySceneRay callback for mousedown button events:
    <pre><code class="language-python">    def onClicked(self, node, dist):
            if node != None:
                onLeft = 1 if (getDisplayPixelSize()[0] / 2.0 &gt; self.mouseClickPos[0] ) else -1
                pos = self.mouseClickPos + onLeft * Vector3(150, 0, 0)
                self.updateTextInfo(node)
                self.container.setCenter(pos)
                self.container.setVisible(True)
            else:
                self.container.setVisible(False)           
    
        def updateTextInfo(self, selectedNode):
            if self.buildinginfo["buildings"].has_key(selectedNode.getName()):
                building = self.buildinginfo["buildings"][selectedNode.getName()]
                self.label.setText("Building: " + selectedNode.getName())
                self.label2.setText("Height: " +  str(building["height"]) + "m")
            else:
                self.label.setText("Building: N.A")
                self.label2.setText("Height: N.A")</code></pre>
    We position the text box to the left or right depending on the click position, to avoid the text box reaching out of the window bounds.
    
    (insert cyclops3.png)
    
    And thats it, you got a nice DataViz application running, ready to be deployed in the Data Arena.
    The full code (with some additions) is available at "/local/examples/Tutorials/tut3/CustomInteraction.py"
    
    <!-- .entry-content -->";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"57883288cb5f6";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:1;s:2:"id";i:4;s:9:"widget_id";s:36:"c06bb1fd-0c3a-4ecb-9786-51ba4db231ea";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:5;a:14:{s:8:"features";a:3:{i:0;a:9:{s:15:"container_color";b:0;s:4:"icon";s:31:"fontawesome-arrow-circle-o-left";s:10:"icon_color";s:7:"#3d3d3d";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:17:"Previous Tutorial";s:8:"more_url";s:61:"http://localhost/wordpress/tutorials/building-the-scenegraph/";}i:1;a:9:{s:15:"container_color";s:7:"#404040";s:4:"icon";s:0:"";s:10:"icon_color";s:7:"#FFFFFF";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:0:"";s:8:"more_url";s:0:"";}i:2;a:9:{s:15:"container_color";s:7:"#e8e8e8";s:4:"icon";s:32:"fontawesome-arrow-circle-o-right";s:10:"icon_color";s:7:"#3d3d3d";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:13:"Next Tutorial";s:8:"more_url";s:43:"/wordpress/tutorials/defining-interactions/";}}s:5:"fonts";a:4:{s:13:"title_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:12:"text_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:17:"more_text_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:24:"so_field_container_state";s:6:"closed";}s:15:"container_shape";s:0:"";s:14:"container_size";s:4:"84px";s:19:"container_size_unit";s:2:"px";s:9:"icon_size";s:4:"24px";s:14:"icon_size_unit";s:2:"px";s:7:"per_row";i:3;s:10:"responsive";b:1;s:12:"_sow_form_id";s:13:"57873dc4344d9";s:10:"title_link";b:0;s:9:"icon_link";b:0;s:10:"new_window";b:0;s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Features_Widget";s:3:"raw";b:0;s:4:"grid";i:3;s:4:"cell";i:0;s:2:"id";i:5;s:9:"widget_id";s:36:"9cfce0d0-9f38-47ab-930d-0f36248ba8e9";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}}s:5:"grids";a:4:{i:0;a:2:{s:5:"cells";i:1;s:5:"style";a:3:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:1;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"10px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:2;a:2:{s:5:"cells";i:2;s:5:"style";a:4:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:3;a:2:{s:5:"cells";i:1;s:5:"style";a:0:{}}}s:10:"grid_cells";a:7:{i:0;a:2:{s:4:"grid";i:0;s:6:"weight";i:1;}i:1;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.227000000000000035083047578154946677386760711669921875;}i:2;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.6910000000000000586197757002082653343677520751953125;}i:3;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.082000000000000017319479184152442030608654022216796875;}i:4;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.2263071895424799973017826459908974356949329376220703125;}i:5;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.7736928104575200304537929696380160748958587646484375;}i:6;a:2:{s:4:"grid";i:3;s:6:"weight";i:1;}}}
---
<h3 style="text-align: center;">Omegalib Tutorial Series</h3>
<h4>Tutorials</h4>
<ol>
 	<li style="text-align: left;"><a href="/wordpress/tutorials/load-box/">Load Geometry </a></li>
 	<li style="text-align: left;"><a href="/wordpress/tutorials/building-the-scenegraph/"><strong>Building The Scenegraph</strong></a></li>
 	<li style="text-align: left;"><a href="/wordpress/tutorials/defining-interactions/"><strong>Defining Interactions</strong></a></li>
 	<li style="text-align: left;"><a href="/wordpress/tutorials/advancedomegalibosgapplications/"><strong>Advanced Omegalib/OSG Applications</strong></a></li>
</ol>
In the following tutorials we will show you, how to create, import and display cool models and bring them to the Data Arena. Graphics programming experience is not a prerequisite, although it will help to have some understanding of the graphics pipeline.
<h3>Defining your own interactions</h3>
In this tutorial you will learn
<ul>
 	<li>how to implement custom interaction handlers</li>
 	<li>how to export 3D models from a modelling software and import them to omegalib</li>
 	<li>how to display text</li>
</ul>
Suppose you want to visualize a portion of a city and enable the user to query information about particular buildings by clicking on them.
In this tutorial you will build and export a 3d model of a building block, assign values to the building and define interaction handlers to process click events and then display information about the building in a text-over block.
<h3>Building and exporting the model</h3>
Fire up your 3D modelling tool of choice, and start building your model. This tutorial uses Blender, but the workflow is similar to other 3D modelling tools.

A small building block model can be made, by importing a highly detailed map section, covering the buildings with polygons and extruding them. We have built a simple model of the UTS:

(insert blender.png)

Now, the model has to be exported to omegalib. The underlying OpenSceneGraph can understand many common formats (.obj, .3ds, .ply, …), however the most convinient way is to export into .osgt, the native osg format. This format explicitly defines the scenegraph is easibly readable for humans. Check <a href="http://trac.openscenegraph.org/projects/osg//wiki/Community/Plugins">http://trac.openscenegraph.org/projects/osg//wiki/Community/Plugins</a> for available exporters, there are exporters for 3D Studio Max, Maya and Blender (plugins for other model packages might exist elsewhere). The best plugin for Blender is maintained under <a href="https://github.com/cedricpinson/osgexport">https://github.com/cedricpinson/osgexport</a>, use this to export your scene into .osgt, the default settings for the export are appropriate.

Now have a look at the osgt file to grasp, what the scenegraph looks like. There is a root object and child objects. Depending on the object type, it has material, vertex and/or texture data assigned. Note that in Blender, only the materials set for the Blender renderer (not cycles) are exported. You can import and show the pieces of your model in python:
<pre><code class="language-python">modelInfo = ModelInfo()
modelInfo.name = "UTS"
modelInfo.path = "UTS.osgt"
modelInfo.size = 65.0
#its important to not use the optimizer, 
# so that all seperately defined objects stay seperate
modelInfo.optimize = False
# loads model, but does not attach it yet
getSceneManager().loadModel(modelInfo)
# loads model by name, and attaches it to scene
model = StaticObject.create("UTS")
#print out all objects defined in the model
for pieceName in  model.listPieces("Root"):
print pieceName</code></pre>
When executing this code, the diplayed model should look similar to this:
(insert cyclops1.png)

The camera is oriented horizontally to the model and can not be moved.
We want to the camera a more interesting camera angle and position. Trying out different positions from python
is a lot of tiring manual work and therefore we want to use the camera view transformation defined in our modelling program.
To get this, find out the name of your camera in Blender (or other modelling program) and check, if this name is present as a node in the .osgt file (which it should be).

To get the position, extract the node from the model graph:
<pre><code class="language-python">cam = model.getPiece("Root/Camera")
print cam.getPosition()</code></pre>
The getPiece method returns an <code>Entity</code>, which is still anchored in the scenegraph, and we can retrieve its position.
The next thing we need is the camera lookat and up vector. We will avoid having to calculate a orientation to lookat transformation by setting the camera lookat point ourself. In Blender (or other program), create an Empty at the center position of the camera and set the camera to its parent. By doing this, the Empty, which you can call the CameraFocus, will always stay centered in the camera view. Now export the scene again and retrieve the camerafocus position by
<pre><code class="language-python">focus = cam.getPiece("CameraFocus")
worldfocusPos = cam.convertLocalToWorldPosition( focus.getPosition() )</code></pre>
Note that the focus position is local to its parent and has to be transformed into world space.

You will use these positions in the next step.
<h3>View Manipulators</h3>
In previous tutorials, we have used the <code>GeometryHandler</code> class to walk though the model in a first-person style.
In this tutorial, we want to be able to rotate, pan and zoom the model similar to the 3D view in modelling programs.
The Data Arena version of cyclops offers a <code>ManipulatorController</code> class, which makes it possible to use <em>osg::CameraManipulator</em> with omegalib cameras.

Create a class which instantiates both a <code>ManipulatorController</code> and a <code>TerrainManipulator</code> and set the ManipulatorController to use the TerrainManipulator.

<code>TerrainManipulator</code> is a wrapper around <code>osg::TerrainManipulator</code> and defines zooming, panning and rotating around terrains with horizontal terrain zooming.
Other currently implemented Manipulators are: <code>OrbitManipulator</code> and <code>NodeTrackerManipulator</code>.
<pre><code class="language-python">class CameraHandler:
def __init__(self):
# controller for camera manipulators
self.camManipController = CameraManipulator.create()
# the actual camera manipulator
self.manipulator = TerrainManipulator.create()
self.camManipController.setManipulator(self.manipulator)
def onEvent(self):
"""Callback for omegalib to register with `setEventFunction`."""
self.camManipController.onEvent(getEvent())</code></pre>
Now, we can instatiate the CameraHandler and set it to handle our model:
<pre><code class="language-python">...
camManipulator = CameraHandler()
camManipulator.setCameraHome(cam.getPosition(), worldFocusPos)
setEventFunction(camManipulator.onEvent)</code></pre>
Rotating, panning and zooming should now be possible.

By default, the manipulators use the mouse.Using different input devices is also possible, by using a different <code>EventHandler</code>. EventHandlers transform input of various devices into mouse events for osg. To use a playstation controller, for instance, add a <code>MyControllerAdapter</code> in the constructor of the CameraHandler.
<pre><code class="language-python">    def __init__(self):
...
self.eventAdapter = MyControllerAdapter(self.manipulator)
self.camManipController.setEventAdapter(self.eventAdapter)
def onUpdate(self, frame, time, dt):
if self.eventAdapter != None:
self.eventAdapter.onUpdate(self.camManipController)
...
setUpdateFunction(camManipulator.onUpdate)</code></pre>
The onUpdate function ensures smooth transformation for controller events.
<h3>Selecting models in the view</h3>
To enable the user to interact with the model, we want to him to to be able to hover over model parts, make selections and get visual feedback. We want to color a node if the cursor is hover over it:
(insert cyclops2.png)

The first step is to check if our mouse is hovering over a model.
Define a new class called SceneHandler, and add a onEventMethod. Modularlizing your code in camerahandlers, scenehandlers, modelcontrollers, etc.. is always a good idea to encourage loose coupling and reusability of components.
<pre><code class="language-python">class SceneHandler:
def__init__(self):
pass
def onEvent(self):
e = getEvent()
if(e.getServiceType() == ServiceType.Pointer or e.getServiceType() == ServiceType.Wand):
r = getRayFromEvent(e)
# Button mappings are different when using wand or mouse
confirmButton = EventFlags.Button1
if(e.getServiceType() == ServiceType.Wand): confirmButton = EventFlags.Button5
if(r[0]): 
# When the confirm button is pressed:
if(e.isButtonDown(confirmButton)):
self.mouseClickPos = e.getPosition()
querySceneRay(r[1], r[2], self.onClicked, QueryFlags.QuerySort | QueryFlags.QueryFirst)
else:
querySceneRay(r[1], r[2], self.colorHovered, QueryFlags.QuerySort | QueryFlags.QueryFirst)</code></pre>
Cyclops offers functions which makes this quite easy:
<ul>
 	<li>getRayFromEvent: returns a ray which has its startpoint set at the camera eye position and the direction towards the mouse pointer</li>
 	<li>querySceneRay: Makes intersection tests between the ray and all nodes and executing a callback for every node that is returned (hit). We sort the scene from shortest to longest distance and return closest node. Only nodes, which are set as <em>selectable</em> will be queried.</li>
</ul>
Until now, we only have one root <code>omega::SceneNode</code> in the scene. Note that this is a different type of node than <code>osg::Node</code>. To make different parts of the model selectable, all seperate parts of the model have to be extracted into a SceneNode.
Using this selection method is most useful, if there is a pointer device (mouse or wand) available.

Wrap the model loading part into a new class called <em>ModelController</em> and add a new method <em>setSelectableParts</em>, which is called after loading in the constructor:
<pre><code class="language-python">#in class ModelController:
def setSelectableParts(self):    
self.selectableNodes = []
self.model.setSelectable(False)
for pieceName in self.model.listPieces("Root"):
if pieceName == "Camera": #dont extract the camera yet
continue
mod = self.model.getPiece("Root/" + pieceName)
if pieceName.startswith("cb"):
if mod != None:
mod.setSelectable(True)
self.selectableNodes.append(mod)
else:
mod.setSelectable(False)</code></pre>
In Blender, we have named every building using the "CBxx" naming. We only want to make UTS building nodes selectable, so we set everything which does not start with "cb" to non-selectable. We also don’t want to extract the camera, as we do this later to query its position/lookat and a piece can only be extracted once because a new scenenode is created and maintained using its name.

Next, we define the callback to be called, when there is a event (except for mouse clicks):
<pre><code class="language-python">    def colorHovered(self, node, dist):
if node != None:
for n in self.modelController.getSelectableNodes():
if n.getName() == node.getName():
n.getMaterial().setColor(Color(1.0,1.0,1.0,1.0), Color(0.2, 0.2,0.2, 0.2))
else:
n.getMaterial().setColor(Color(0.2,0.2,0.2,1.0), Color(0.0, 0.0,0.0, 0.0))
else:
for n in self.modelController.getSelectableNodes():
n.getMaterial().setColor(Color(0.2,0.2,0.2,1.0), Color(0.0, 0.0,0.0, 0.0))</code></pre>
The <em>querySceneRay</em> returns a node which was found and its distance. The node can also be None, if nothing was found.
We set the model part’s material to a bright white color, if it is under the cursor and all other buildings to a more darkish color. If no node was found, set all parts to the same darkish color.
Now you should be able to see you selections by hovering over buildings.
<h3>Displaying Information on the UI</h3>
To complete our example, it would be nice to show information about the buildings when clicked. Getting information into the visualization is always application specific, but one simple way to get in information is to define a json dictionary which maps node names to information.

Displaying the height of the building will suffice for this example:
<pre><code class="language-json">{
"buildings":{
"cb1" : {"height": 150},
"cb2" : {"height": 20},
"cb3" : {"height": 15},
"cb4" : {"height": 15},
"cb5" : {"height": 20},
"cb6" : {"height": 60},
"cb10" : {"height": 35},
"cb11" : {"height": 40}
}
}</code></pre>
Omegalib offers some UI functionality, which makes it easy to define 2D widgets, which are rendered infront of the scene.
<pre><code class="language-python">class SceneHandler:
def __init__(self, modelController):
self.modelController = modelController
self.ui = UiModule.createAndInitialize()
self.wf = self.ui.getWidgetFactory()
self.uiroot = self.ui.getUi()
containerSize = Vector2(300, 100)
self.container = self.wf.createContainer('container', self.uiroot, ContainerLayout.LayoutVertical)
self.container.setAutosize(False)
self.container.setSize(containerSize)
self.label = self.makeLabel("label1")
self.label2 = self.makeLabel("label2")
self.lastMousePos = None
with open('buildinginfo.json') as data_file:    
self.buildinginfo = json.load(data_file)
def makeLabel(self, name):
label = self.wf.createLabel(name, self.container, '')
label.setAutosize(True)
label.setStyle('font: fonts/arial.ttf 30; color: white; alpha: 1.0;')
label.setStyleValue('align', 'middle-left') 
label.setVisible(False)
return label</code></pre>
The UI works similar to other UI frameworks. A <a href="https://github.com/uic-evl/omegalib/wiki/Container">Container</a> is needed to hold <a href="https://github.com/uic-evl/omegalib/wiki/Widget">Widgets</a>, such as <a href="https://github.com/uic-evl/omegalib/wiki/Label">Labels</a>, <a href="https://github.com/uic-evl/omegalib/wiki/Button">Buttons</a> and <a href="https://github.com/uic-evl/omegalib/wiki/Slider">Sliders</a>. There is no textwrap in omegalib, so for every line, a new label has to be created.

The <code>json</code> library is used, to convert the json file into a python dictionary.

The last step is to actually display the text, when the building is clicked. We define the querySceneRay callback for mousedown button events:
<pre><code class="language-python">    def onClicked(self, node, dist):
if node != None:
onLeft = 1 if (getDisplayPixelSize()[0] / 2.0 &gt; self.mouseClickPos[0] ) else -1
pos = self.mouseClickPos + onLeft * Vector3(150, 0, 0)
self.updateTextInfo(node)
self.container.setCenter(pos)
self.container.setVisible(True)
else:
self.container.setVisible(False)           
def updateTextInfo(self, selectedNode):
if self.buildinginfo["buildings"].has_key(selectedNode.getName()):
building = self.buildinginfo["buildings"][selectedNode.getName()]
self.label.setText("Building: " + selectedNode.getName())
self.label2.setText("Height: " +  str(building["height"]) + "m")
else:
self.label.setText("Building: N.A")
self.label2.setText("Height: N.A")</code></pre>
We position the text box to the left or right depending on the click position, to avoid the text box reaching out of the window bounds.

(insert cyclops3.png)

And thats it, you got a nice DataViz application running, ready to be deployed in the Data Arena.
The full code (with some additions) is available at "/local/examples/Tutorials/tut3/CustomInteraction.py"

<!-- .entry-content -->

&nbsp;
<p class="sow-more-text"><a href="http://localhost/wordpress/tutorials/building-the-scenegraph/"> Previous Tutorial </a></p>
<p class="sow-more-text"><a href="/wordpress/tutorials/defining-interactions/"> Next Tutorial </a></p>