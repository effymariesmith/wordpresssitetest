---
ID: 230
post_title: Load Box
author: davm
post_date: 2016-06-27 01:21:13
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/data-type/geometry/load-box/
published: true
panels_data:
  - |
    a:3:{s:7:"widgets";a:8:{i:0;a:13:{s:5:"image";i:219;s:14:"image_fallback";s:0:"";s:4:"size";s:4:"full";s:5:"align";s:7:"default";s:5:"title";s:16:"Photo of pipline";s:14:"title_position";s:6:"hidden";s:3:"alt";s:0:"";s:3:"url";s:0:"";s:5:"bound";b:1;s:12:"_sow_form_id";s:13:"576b62d946865";s:10:"new_window";b:0;s:10:"full_width";b:0;s:11:"panels_info";a:7:{s:5:"class";s:30:"SiteOrigin_Widget_Image_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:0;s:9:"widget_id";s:36:"09ee1a72-2e0d-4e23-8d1a-a4d8946c4a10";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:1;a:4:{s:5:"title";s:0:"";s:4:"text";s:757:"<h4><a href="http://localhost/wordpress/data-type/geometry/load-box/"><strong> Load Box</strong></a> Example</h4>
    <p> </p>
    <h6> Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus elementum semper nisi.  </h6>
    
    <p> </p>
    <p> </p>
    <p> </p>
     <h4>Run Load Box <a href=""><strong> Demo</strong></a></h4>";s:6:"filter";b:0;s:11:"panels_info";a:7:{s:5:"class";s:14:"WP_Widget_Text";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:1;s:2:"id";i:1;s:9:"widget_id";s:36:"fa9f1c94-74c1-4106-a290-9bcb34cde362";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:2;a:4:{s:5:"title";s:0:"";s:4:"text";s:351:"<h2>Use this <a href="">Example</a> </h2>
    <p> </p>
    <h2>1 </h2><h8> Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus</h8>
    <p> </p>
    <p> </p>
    
    <h2>2</h2> Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    ";s:6:"filter";b:0;s:11:"panels_info";a:7:{s:5:"class";s:14:"WP_Widget_Text";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:0;s:2:"id";i:2;s:9:"widget_id";s:36:"54851dee-99e3-4a0e-adda-373a231fe652";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:3;a:4:{s:5:"title";s:0:"";s:4:"text";s:364:"<p><h2>.<h2/> </p>
    
    
    <p> </p>
    <p> </p>
    <h2>3</h2> Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, 
    <p> </p>
    <p> </p>
    
    <h2>4</h2> Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa.
    <p> </p>
    ";s:6:"filter";b:0;s:11:"panels_info";a:7:{s:5:"class";s:14:"WP_Widget_Text";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:1;s:2:"id";i:3;s:9:"widget_id";s:36:"7107df68-9d33-4eb6-9aa3-46f20a2e72c7";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:4;a:6:{s:5:"title";s:0:"";s:4:"text";s:6300:"<h2>Follow this <a>Tutorial</a></h2><h4>Check out our tutorial <a href="http://localhost/wordpress/tutorials/"> series </a></h4><h4> </h4><h4>Getting Started</h4><p>The Data Arena VM comes with all the software needed to display things in the Data Arena.<br /> For this tutorial, we will mostly interact with scripts inside the "/local/examples/" folder, which contains the examples of this tutorial(s) and the custom handlers (in the pipelines folder).</p><p>So lets get started and build our first immersive application!</p><h4>Cube Tutorial</h4><p>The hello world program of the graphics world is displaying a simple object, such as a cube. Before being able to display anything, you have to have a model of a cube first, of course. Creating and exporting models will be covered in the next tutorial, for now, take the "box.obj" model from the "examples/box" folder. Wavefront (.obj) models are a popular format for exchanging 3d models between different applications. They contain the definition of the geometry, colors and many optional definitions. Fortunately, we don't have to parse this model by ourselves but can use a model loader, which is part of the osg package. The "Geometry" class takes care of loading the model and adding it to the scenegraph (more on that later).</p><p>The following is a minimal working example:</p><div class="highlight"><pre><span class="kn">import</span> <span class="nn">sys</span>
    <span class="n">sys</span><span class="o">.</span><span class="n">path</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="s1">'/local/examples'</span><span class="p">)</span>
    
    <span class="kn">from</span> <span class="nn">pipelines.objects</span> <span class="kn">import</span> <span class="n">Geometry</span>
    <span class="kn">from</span> <span class="nn">pipelines.handler</span> <span class="kn">import</span> <span class="n">GeometryHandler</span> 
    
    <span class="n">fileToLoad</span> <span class="o">=</span> <span class="s2">"/local/examples/box/box.obj"</span>
    
    <span class="n">geo</span> <span class="o">=</span> <span class="n">Geometry</span><span class="p">(</span><span class="n">fileToLoad</span><span class="p">)</span>
    
    <span class="n">handler</span> <span class="o">=</span> <span class="n">GeometryHandler</span><span class="p">()</span>
    <span class="n">handler</span><span class="o">.</span><span class="n">initialCamPosition</span> <span class="o">=</span> <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">5</span><span class="p">]</span>
    <span class="n">handler</span><span class="o">.</span><span class="n">addGeo</span><span class="p">(</span><span class="n">geo</span><span class="p">)</span>
    </pre></div><p>The code above adds the examples folder to the system path, so the pipelines are importable.<br /> Then, by creating an Geometry object and giving it the path to the model, the box.obj model is loaded, added to the scene and its material is set. Have a look at "objects.py" (link to geometry docs or source), to see what exactly is going on.</p><p>Then a GeometryHandler is instanced and the geometry is registered with the addGeo() method. This step ensures, that the camera is focused on the center of the model. Before adding geometry, set the initial camera position to have a higher z value, so the camera looks from above onto the object and is not too close.</p><p>(embed box1 image)</p><p>To add another box to the scene, you can load the box in a new Geometry, set its initial position to a different position and register it to the GeometryHandler. Also set the initial camera position to the middle of both cubes.</p><div class="highlight"><pre><span class="c1">#update the initial camera position</span>
    <span class="n">handler</span><span class="o">.</span><span class="n">initialCamPosition</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">5</span><span class="p">]</span> 
    <span class="c1">#add new box</span>
    <span class="n">geo2</span> <span class="o">=</span> <span class="n">Geometry</span><span class="p">(</span><span class="n">fileToLoad</span><span class="p">)</span>
    <span class="n">geo2</span><span class="o">.</span><span class="n">initialPosition</span> <span class="o">=</span> <span class="p">[</span><span class="mi">2</span><span class="p">,</span><span class="mi">0</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span>
    <span class="n">handler</span><span class="o">.</span><span class="n">addGeo</span><span class="p">(</span><span class="n">geo2</span><span class="p">)</span>
    </pre></div><p>(embed box2 image)</p><p>Now both boxes are displayed, but we can't interact with them yet. The GeometryHandler class contains configurable interaction handlers, which let you control the model using different input devices (mouse, ps4 controller, space navigator). To use the event handlers, they have to be registered in omegalib.</p><div class="highlight"><pre><span class="n">setEventFunction</span><span class="p">(</span><span class="n">handler</span><span class="o">.</span><span class="n">onEvent</span><span class="p">)</span>
    <span class="n">setUpdateFunction</span><span class="p">(</span><span class="n">handler</span><span class="o">.</span><span class="n">onUpdate</span><span class="p">)</span>
    </pre></div><p>The setEventFunction (add link) passes through all input events to the handler's onEvent function, the setUpdateFunction (add link) registers a script function to be called before each frame is rendered.<br /> Now the boxes can be rotate in the scene. The interaction handler provides several ways to constrain the movement of the camera and of the object, which are displayed in the console.<br /> When pressing "m", the mode can be toggled between object mode to camera mode. You can use object mode to rotate and translate the object and camera mode to orient yourself in the space in a first person way.</p><p>(embed box3 image)</p><p>In the next tutorial, you will learn how to apply simple materials to objects.</p><h4> </h4><h4>More <a href="http://localhost/wordpress/tutorials/"> Tutorials</a></h4>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"5770c532d1e3d";s:11:"panels_info";a:6:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:4:"grid";i:2;s:4:"cell";i:0;s:2:"id";i:4;s:9:"widget_id";s:36:"1391920e-3d6d-43e3-a359-05f94389c1e0";s:5:"style";a:2:{s:27:"background_image_attachment";b:0;s:18:"background_display";s:4:"tile";}}}i:5;a:13:{s:5:"image";i:144;s:14:"image_fallback";s:0:"";s:4:"size";s:4:"full";s:5:"align";s:7:"default";s:5:"title";s:0:"";s:14:"title_position";s:6:"hidden";s:3:"alt";s:0:"";s:3:"url";s:0:"";s:5:"bound";b:1;s:12:"_sow_form_id";s:13:"576b6f04ed198";s:10:"new_window";b:0;s:10:"full_width";b:0;s:11:"panels_info";a:7:{s:5:"class";s:30:"SiteOrigin_Widget_Image_Widget";s:3:"raw";b:0;s:4:"grid";i:3;s:4:"cell";i:0;s:2:"id";i:5;s:9:"widget_id";s:36:"7ff25a31-f542-4a04-a44f-2c8cea53f183";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:6;a:13:{s:5:"image";i:144;s:14:"image_fallback";s:0:"";s:4:"size";s:4:"full";s:5:"align";s:7:"default";s:5:"title";s:0:"";s:14:"title_position";s:6:"hidden";s:3:"alt";s:0:"";s:3:"url";s:0:"";s:5:"bound";b:1;s:12:"_sow_form_id";s:13:"576b6f262e8f8";s:10:"new_window";b:0;s:10:"full_width";b:0;s:11:"panels_info";a:7:{s:5:"class";s:30:"SiteOrigin_Widget_Image_Widget";s:3:"raw";b:0;s:4:"grid";i:3;s:4:"cell";i:1;s:2:"id";i:6;s:9:"widget_id";s:36:"7ff25a31-f542-4a04-a44f-2c8cea53f183";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:7;a:13:{s:5:"image";i:144;s:14:"image_fallback";s:0:"";s:4:"size";s:4:"full";s:5:"align";s:7:"default";s:5:"title";s:0:"";s:14:"title_position";s:6:"hidden";s:3:"alt";s:0:"";s:3:"url";s:0:"";s:5:"bound";b:1;s:12:"_sow_form_id";s:13:"576b6f29382de";s:10:"new_window";b:0;s:10:"full_width";b:0;s:11:"panels_info";a:7:{s:5:"class";s:30:"SiteOrigin_Widget_Image_Widget";s:3:"raw";b:0;s:4:"grid";i:3;s:4:"cell";i:2;s:2:"id";i:7;s:9:"widget_id";s:36:"7ff25a31-f542-4a04-a44f-2c8cea53f183";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}}s:5:"grids";a:4:{i:0;a:2:{s:5:"cells";i:2;s:5:"style";a:5:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"mobile_padding";s:9:"mob-pad-0";s:14:"column_padding";s:0:"";}}i:1;a:2:{s:5:"cells";i:2;s:5:"style";a:4:{s:7:"padding";s:4:"50px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:2;a:2:{s:5:"cells";i:1;s:5:"style";a:3:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:3;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}}s:10:"grid_cells";a:8:{i:0;a:2:{s:4:"grid";i:0;s:6:"weight";d:0.352225981713649993753989519973401911556720733642578125;}i:1;a:2:{s:4:"grid";i:0;s:6:"weight";d:0.64777401828634995073485924876877106726169586181640625;}i:2;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.5;}i:3;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.5;}i:4;a:2:{s:4:"grid";i:2;s:6:"weight";i:1;}i:5;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.333333333333333314829616256247390992939472198486328125;}i:6;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.333333333333333314829616256247390992939472198486328125;}i:7;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.333333333333333314829616256247390992939472198486328125;}}}
---
<img src="http://localhost/wordpress/wp-content/uploads/2016/07/loadbox01.jpg" title="Photo of pipline" class="so-widget-image" height="457" width="685">
<h4><a href="http://localhost/wordpress/data-type/geometry/load-box/"><strong> Load Box</strong></a> Example</h4>
<p> </p>
<h6> Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus elementum semper nisi.  </h6>
<p> </p>
<p> </p>
<p> </p>
<h4>Run Load Box <a href=""><strong> Demo</strong></a></h4>
<h6>Use this example</h6>
Follow some quick <a href="#howto"><strong>how to's</strong></a> 
or for a more in-depth understand, follow our<a href="https://localhost/wordpress/tutorials/load-box/"><strong> Omegalib Tutorial Series</strong></a> <p></p>
<h2 style="text-align: left">Use this example</h2>
<p><a name="howto"></a> </p>
<h3 style="text-align: left">Load Demo from command line</h3>
<ul class="sow-slider-images">		<li class="sow-slider-image">
<img src="http://localhost/wordpress/wp-content/uploads/2016/07/box.png" class="attachment-full size-full" alt="box" height="589" width="920">				
</li>
</ul>				<ol class="sow-slider-pagination">
<li><a href="#">1</a></li>
</ol>
<a href="#">
<em class="sow-sld-icon-thin-right"></em>
</a>
<a href="#">
<em class="sow-sld-icon-thin-left"></em>
</a>
<h3>1 </h3>Using Dolphin or linux shell navigate to  /local/examples/box

<h3>2</h3> In the linux shell enter
<pre> <code>
orun LoadBox.py  
</code> </pre>
<h3>3</h3>  Enter <code> :q </code> to quick the demo
<h3>Getting Started</h3>
<p>The Data Arena VM comes with all the software needed to display things in the Data Arena.<br>
For this tutorial, we will mostly interact with scripts inside the "/local/examples/" folder, which contains the examples of this tutorial(s)<br>
and the custom handlers (in the pipelines folder).</p>
<p>So lets get started and build our first immersive application!</p>
<h4>Read <a href="http://localhost/wordpress/tutorials/load-box/">More</a></h4>
<h6>Or check out our tutorial <a href="http://localhost/wordpress/tutorials/"> series </a></h6>
<h3 style="text-align: center">Explore More Examples</h3>
<a href="http://localhost/wordpress/data-type/geometry/fashion-turntable/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-300x248.jpg" title="Fashion Turntable" class="so-widget-image" height="248" width="300">
</a>
<a href="http://localhost/wordpress/data-type/point-cloud/wombeyan-caves/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/cave02-300x248.jpg" title="Caves" class="so-widget-image" height="248" width="300">
</a>
<a href="http://localhost/wordpress/data-type/speedsheet/parallelcoordinates/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-300x248.jpg" title="Parallel Coordinates" class="so-widget-image" height="248" width="300">
</a>
<h2>Overview </h2>
<p> </p>
<h2>1 </h2> Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus
<p> </p>
<p> </p>
<h2>2</h2> Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
<p></p><h2>.</h2><h2></h2> <p></p>
<p> </p>
<p> </p>
<h2>3</h2> Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, 
<p> </p>
<p> </p>
<h2>4</h2> Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa.
<p> </p>