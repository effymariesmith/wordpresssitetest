---
ID: 557
post_title: Building the Scenegraph
author: davm
post_date: 2016-06-30 07:07:45
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/tutorials/building-the-scenegraph/
published: true
panels_data:
  - |
    a:3:{s:7:"widgets";a:4:{i:0;a:6:{s:5:"title";s:0:"";s:4:"text";s:61:"<h3 style="text-align: center;">Omegalib Tutorial Series</h3>";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578723843cea2";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:0;s:9:"widget_id";s:36:"1ea35202-0ffb-4952-88db-1380842ca3f4";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:1;a:5:{s:8:"headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:4:"left";s:24:"so_field_container_state";s:4:"open";}s:12:"sub_headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:6:"center";s:24:"so_field_container_state";s:4:"open";}s:7:"divider";a:8:{s:5:"style";s:5:"solid";s:6:"weight";s:4:"thin";s:5:"color";b:0;s:11:"side_margin";s:4:"20px";s:16:"side_margin_unit";s:2:"px";s:10:"top_margin";s:4:"20px";s:15:"top_margin_unit";s:2:"px";s:24:"so_field_container_state";s:4:"open";}s:12:"_sow_form_id";s:13:"57871dc1b3fe7";s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Headline_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:1;s:9:"widget_id";s:36:"42c24578-cfd7-4dd5-8d52-e5b5178da0b8";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:2;a:4:{s:5:"title";s:0:"";s:4:"text";s:255:"In the following tutorials we will show you, how to create, import and display cool models and bring them to the Data Arena.
    
    Graphics programming experience is not a prerequisite, although it will help to have some understanding of the graphics pipeline.";s:6:"filter";b:0;s:11:"panels_info";a:7:{s:5:"class";s:14:"WP_Widget_Text";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:0;s:2:"id";i:2;s:9:"widget_id";s:36:"8458d952-2849-47ac-8244-b11bcc3949d1";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:3;a:6:{s:5:"title";s:0:"";s:4:"text";s:8030:"<h3>Building the scencegraph</h3>
    The Geometry class provides a quick way of loading and interacting with models, however if you want to customize your models, materials etc., you have to build your own class for handling these models. Cyclops (or more precise the underlying OpenSceneGraph) uses a scenegraph to control the 3D geometry, states and transforms.
    
    A scene graph is a collection of nodes in a graph or tree structure. A tree node (in the overall tree structure of the scene graph) may have many children but often only a single parent, with the effect of a parent applied to all its child nodes; an operation performed on a group automatically propagates its effect to all of its members. Associating a geometrical transformation matrix at each group level and concatenating such matrices together is an efficient and natural way to process such operations. Commonly different shapes/objects are combined into a compound object that can then be moved, transformed, selected, etc. as easily as a single object.
    
    In this tutorial, we are going to define our own geometry, build the scene graph and add different effects to objects.
    <h4>Step 1: Defining Geometry</h4>
    In cyclops, simple geometry can be defined by using the ModelGeometry (add link) class. The defined Geometry maps to OpenGL primitive definitions, with a few abstractions. You can read up on this topic here: <a href="http://math.hws.edu/graphicsbook/c3/s1.html">http://math.hws.edu/graphicsbook/c3/s1.html</a>, especially if you have never worked with computer graphics.
    In this tutorial, you will build and colorize a simple quad.
    <pre><code class="language-python">geom = ModelGeometry.create('quad')
    v1 = geom.addVertex(Vector3(0, 0, 0))
    v2 = geom.addVertex(Vector3(0, -1, 0))
    v3 = geom.addVertex(Vector3(1, 0, 0))
    v4 = geom.addVertex(Vector3(1, -1, 0))
    geom.addPrimitive(PrimitiveType.TriangleStrip, 0, 4)</code></pre>
    This snippet shows how to define a simple quad. The <em>ModelGeometry</em> class is actually a wrapper for OSG Geometry (insert) and defines a leaf-node of the scene graph (called geode in osg).In cyclops, all entities (visible objects) have to be registered in the scenemanager. This can be done using <code>scenemanager.addModel()</code>, which stores a new ModelAsset in the scenemanager.
    <pre><code class="language-python">getSceneManager().addModel(geom)
    
    quad = StaticObject.create('quad')
    quad.setPosition(Vector3(0,2.5,-3))</code></pre>
    To see the primitive, you have to add it to the root in the scene graph. Cyclops manages the root node in the scene-manager and a model can be added by creating a StaticObject (add link), and passing the name of the geometry. Cyclops stores a dictionary with a name to model mapping, and nodes can therefore generally be retrieved by their name. StaticObject derives from Entity (a cyclops class), which derives from SceneNode (an omega class), which both provide many functions to interact with scenegraph nodes. All entities are automatically added to the root node of the scenegraph, thereforeThe default camera is slightly tilted, therefore the object must be shifted into the camera field. Also the z-value (the depth) has to be lowered, because otherwise the quad overlaps exactly with the camera plane and will be clipped.
    <h4>Step 2: Adding instances</h4>
    Now that the geometry has been defined, it can be used in any numbers of nodes. You can, for example, arrange quads in a circular way and add different colors:
    <pre><code class="language-python">self.colors = ["white", "green", "blue", "yellow", "black", "#ff00f4", "#00FFFF", "red"]
    pi = 3.141592
    
    for i in range(0, 8, 1):
        quad = StaticObject.create("quad")
        # arrange in a circular fashion in pi/4 intervals
        quad.setPosition(Vector3(sin(pi * i / 4.0) * 2,
                                     cos(pi * i / 4.0) * 2 + 2.5, -10))
        quad.setEffect('colored -e ' + self.colors[i])</code></pre>
    Effects are a quick way to add custom appearance to objects and will be covered in another tutorial.
    
    <img class="alignnone size-medium wp-image-568" src="http://localhost/wordpress/wp-content/uploads/2016/06/planes1-300x171.png" sizes="(max-width: 300px) 100vw, 300px" srcset="http://localhost/wordpress/wp-content/uploads/2016/06/planes1-300x171.png 300w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-768x438.png 768w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-830x473.png 830w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-230x131.png 230w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-350x200.png 350w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-480x274.png 480w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1.png 831w" alt="planes1" width="300" height="171" />
    
    (insert planes1.png)
    <h4>Step 3: interacting with the model</h4>
    Using the left mouse button, you should be able to rotate the camera and look around. However, the model itself is static. In the last tutorial, we used the GeometryHandler class to provide interaction handlers for the incoming input events. This time, we did not use the Geometry class, however, we can still use the Geometryhandlers by deriving our own class from BaseObject (pipelines.objects) and overriding the base methods.
    <pre><code class="language-python">class MyQuads(BaseObject):
        def __init__(self):
            BaseObject.__init__(self)
            #create geometry
            ...
            # create the root node of this object
            self.model = SceneNode.create("ParentNode")
            #change depth of parent instead of children
            self.model.setPosition(0,0,-10)
            self.quads = []
    
            for i in range(0, 8, 1):
                quad = StaticObject.create("quad")
                quad.setPosition(Vector3(sin(pi * i / 4.0) * 2,
                                             cos(pi * i / 4.0) * 2 , 0))
                quad.setEffect('colored -e ' + self.colors[i])
                self.quads.append(quad)
                self.model.addChild(quad)
    </code></pre>
    Here, we added a parentNode to the quads, so that the object can be transformed as a whole, the pivot center of the rotation is therefore the center of "parentNode". Adding the quads as childs of the model will aplly every transform of the parent node to the child node. We set our self.model to the position (0,0,-10) and therefore all the children will be translated -10 along the z-axis additionally to their own transformations. We also store the quads seperately in a list for convenient access in the updateModel method.
    <pre><code class="language-python">    def updateModel(self, newRotation, newPosition):
            self.model.rotate(Vector3(1, 0, 0), newRotation[0], Space.World)
            self.model.rotate(Vector3(0, 1, 0), newRotation[1], Space.World)
            self.model.rotate(Vector3(0, 0, 1), newRotation[2], Space.World)
            # add a quirky self rotation of the quads
            for quad in self.quads:
                quad.rotate(Vector3(0, 1, 0), newRotation[1] * 3, Space.World)</code></pre>
    The function <code>updateModel</code> gets called for every new event from the geometryhandler and receives the new rotation and position. This example uses only the rotation to rotate the entire circle of quads around the pivot point in three degrees of freedom (euler angles). Additionally, a y-axis rotation is added for every subquad, to show the effect of manipulating child objects.
    <pre><code class="language-python"># register object with handler
    handler = GeometryHandler()
    quad = MyQuads()
    handler.addObject(quad)
    
    setEventFunction(handler.onEvent)
    setUpdateFunction(handler.onUpdate)</code></pre>
    Finally, the handlers are initialized and registered, like in the first tutorial.
    
    <img class="alignnone size-medium wp-image-569" src="http://localhost/wordpress/wp-content/uploads/2016/06/planes2-300x170.png" alt="planes2" width="300" height="170" />
    
    (insert planes2.png)
    
    <p>
    The complete source for the example lies in <em>/local/examples/Tutorials/tut2/BuildSceneGraph.py</em></p>
    
    <!-- .entry-content -->";s:20:"text_selected_editor";s:4:"html";s:12:"_sow_form_id";s:13:"578825eb362fb";s:5:"autop";b:0;s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:0;s:2:"id";i:3;s:9:"widget_id";s:36:"efa288af-721a-4727-95ba-7e994335bf3f";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}}s:5:"grids";a:2:{i:0;a:2:{s:5:"cells";i:1;s:5:"style";a:4:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:16:"background_image";b:0;s:14:"column_padding";s:0:"";}}i:1;a:2:{s:5:"cells";i:1;s:5:"style";a:4:{s:7:"padding";s:4:"10px";s:5:"align";s:0:"";s:16:"background_image";b:0;s:14:"column_padding";s:0:"";}}}s:10:"grid_cells";a:2:{i:0;a:2:{s:4:"grid";i:0;s:6:"weight";i:1;}i:1;a:2:{s:4:"grid";i:1;s:6:"weight";i:1;}}}
---
<h3 style="text-align: center;">Omegalib Tutorial Series</h3>
In the following tutorials we will show you, how to create, import and display cool models and bring them to the Data Arena. Graphics programming experience is not a prerequisite, although it will help to have some understanding of the graphics pipeline.
<h3>Building the scencegraph</h3>
The Geometry class provides a quick way of loading and interacting with models, however if you want to customize your models, materials etc., you have to build your own class for handling these models. Cyclops (or more precise the underlying OpenSceneGraph) uses a scenegraph to control the 3D geometry, states and transforms. A scene graph is a collection of nodes in a graph or tree structure. A tree node (in the overall tree structure of the scene graph) may have many children but often only a single parent, with the effect of a parent applied to all its child nodes; an operation performed on a group automatically propagates its effect to all of its members. Associating a geometrical transformation matrix at each group level and concatenating such matrices together is an efficient and natural way to process such operations. Commonly different shapes/objects are combined into a compound object that can then be moved, transformed, selected, etc. as easily as a single object. In this tutorial, we are going to define our own geometry, build the scene graph and add different effects to objects.
<h4>Step 1: Defining Geometry</h4>
In cyclops, simple geometry can be defined by using the ModelGeometry (add link) class. The defined Geometry maps to OpenGL primitive definitions, with a few abstractions. You can read up on this topic here: <a href="http://math.hws.edu/graphicsbook/c3/s1.html">http://math.hws.edu/graphicsbook/c3/s1.html</a>, especially if you have never worked with computer graphics. In this tutorial, you will build and colorize a simple quad.
<pre><code class="language-python">geom = ModelGeometry.create('quad')
v1 = geom.addVertex(Vector3(0, 0, 0))
v2 = geom.addVertex(Vector3(0, -1, 0))
v3 = geom.addVertex(Vector3(1, 0, 0))
v4 = geom.addVertex(Vector3(1, -1, 0))
geom.addPrimitive(PrimitiveType.TriangleStrip, 0, 4)</code></pre>
This snippet shows how to define a simple quad. The <em>ModelGeometry</em> class is actually a wrapper for OSG Geometry (insert) and defines a leaf-node of the scene graph (called geode in osg).In cyclops, all entities (visible objects) have to be registered in the scenemanager. This can be done using <code>scenemanager.addModel()</code>, which stores a new ModelAsset in the scenemanager.
<pre><code class="language-python">getSceneManager().addModel(geom)
quad = StaticObject.create('quad')
quad.setPosition(Vector3(0,2.5,-3))</code></pre>
To see the primitive, you have to add it to the root in the scene graph. Cyclops manages the root node in the scene-manager and a model can be added by creating a StaticObject (add link), and passing the name of the geometry. Cyclops stores a dictionary with a name to model mapping, and nodes can therefore generally be retrieved by their name. StaticObject derives from Entity (a cyclops class), which derives from SceneNode (an omega class), which both provide many functions to interact with scenegraph nodes. All entities are automatically added to the root node of the scenegraph, thereforeThe default camera is slightly tilted, therefore the object must be shifted into the camera field. Also the z-value (the depth) has to be lowered, because otherwise the quad overlaps exactly with the camera plane and will be clipped.
<h4>Step 2: Adding instances</h4>
Now that the geometry has been defined, it can be used in any numbers of nodes. You can, for example, arrange quads in a circular way and add different colors:
<pre><code class="language-python">self.colors = ["white", "green", "blue", "yellow", "black", "#ff00f4", "#00FFFF", "red"]
pi = 3.141592
for i in range(0, 8, 1):
quad = StaticObject.create("quad")
# arrange in a circular fashion in pi/4 intervals
quad.setPosition(Vector3(sin(pi * i / 4.0) * 2,
cos(pi * i / 4.0) * 2 + 2.5, -10))
quad.setEffect('colored -e ' + self.colors[i])</code></pre>
Effects are a quick way to add custom appearance to objects and will be covered in another tutorial. <img class="alignnone size-medium wp-image-568" src="http://localhost/wordpress/wp-content/uploads/2016/06/planes1-300x171.png" sizes="(max-width: 300px) 100vw, 300px" srcset="http://localhost/wordpress/wp-content/uploads/2016/06/planes1-300x171.png 300w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-768x438.png 768w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-830x473.png 830w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-230x131.png 230w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-350x200.png 350w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1-480x274.png 480w, http://localhost/wordpress/wp-content/uploads/2016/06/planes1.png 831w" alt="planes1" width="300" height="171" /> (insert planes1.png)
<h4>Step 3: interacting with the model</h4>
Using the left mouse button, you should be able to rotate the camera and look around. However, the model itself is static. In the last tutorial, we used the GeometryHandler class to provide interaction handlers for the incoming input events. This time, we did not use the Geometry class, however, we can still use the Geometryhandlers by deriving our own class from BaseObject (pipelines.objects) and overriding the base methods.
<pre><code class="language-python">class MyQuads(BaseObject):
def __init__(self):
BaseObject.__init__(self)
#create geometry
...
# create the root node of this object
self.model = SceneNode.create("ParentNode")
#change depth of parent instead of children
self.model.setPosition(0,0,-10)
self.quads = []
for i in range(0, 8, 1):
quad = StaticObject.create("quad")
quad.setPosition(Vector3(sin(pi * i / 4.0) * 2,
cos(pi * i / 4.0) * 2 , 0))
quad.setEffect('colored -e ' + self.colors[i])
self.quads.append(quad)
self.model.addChild(quad)
</code></pre>
Here, we added a parentNode to the quads, so that the object can be transformed as a whole, the pivot center of the rotation is therefore the center of "parentNode". Adding the quads as childs of the model will aplly every transform of the parent node to the child node. We set our self.model to the position (0,0,-10) and therefore all the children will be translated -10 along the z-axis additionally to their own transformations. We also store the quads seperately in a list for convenient access in the updateModel method.
<pre><code class="language-python">    def updateModel(self, newRotation, newPosition):
self.model.rotate(Vector3(1, 0, 0), newRotation[0], Space.World)
self.model.rotate(Vector3(0, 1, 0), newRotation[1], Space.World)
self.model.rotate(Vector3(0, 0, 1), newRotation[2], Space.World)
# add a quirky self rotation of the quads
for quad in self.quads:
quad.rotate(Vector3(0, 1, 0), newRotation[1] * 3, Space.World)</code></pre>
The function <code>updateModel</code> gets called for every new event from the geometryhandler and receives the new rotation and position. This example uses only the rotation to rotate the entire circle of quads around the pivot point in three degrees of freedom (euler angles). Additionally, a y-axis rotation is added for every subquad, to show the effect of manipulating child objects.
<pre><code class="language-python"># register object with handler
handler = GeometryHandler()
quad = MyQuads()
handler.addObject(quad)
setEventFunction(handler.onEvent)
setUpdateFunction(handler.onUpdate)</code></pre>
Finally, the handlers are initialized and registered, like in the first tutorial. <img class="alignnone size-medium wp-image-569" src="http://localhost/wordpress/wp-content/uploads/2016/06/planes2-300x170.png" sizes="(max-width: 300px) 100vw, 300px" srcset="http://localhost/wordpress/wp-content/uploads/2016/06/planes2-300x170.png 300w, http://localhost/wordpress/wp-content/uploads/2016/06/planes2-768x434.png 768w, http://localhost/wordpress/wp-content/uploads/2016/06/planes2-830x469.png 830w, http://localhost/wordpress/wp-content/uploads/2016/06/planes2-230x130.png 230w, http://localhost/wordpress/wp-content/uploads/2016/06/planes2-350x198.png 350w, http://localhost/wordpress/wp-content/uploads/2016/06/planes2-480x271.png 480w, http://localhost/wordpress/wp-content/uploads/2016/06/planes2.png 831w" alt="planes2" width="300" height="170" /> (insert planes2.png) The complete source for the example lies in <em>/local/examples/Tutorials/tut2/BuildSceneGraph.py</em>

<!-- .entry-content -->