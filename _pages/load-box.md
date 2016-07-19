---
ID: 324
post_title: Cube Tutorial
author: davm
post_date: 2016-06-27 06:14:00
post_excerpt: ""
layout: page
permalink: http://localhost/wordpress/load-box/
published: true
---
<h3 style="text-align: center;">Omegalib Tutorial Series</h3>
<h4>Tutorials</h4>
<ol>
<li style="text-align: left;"><a href="https://localhost/wordpress/tutorials/load-box/">Load Geometry </a></li>
<li style="text-align: left;"><a href="http://localhost/wordpress/tutorials/building-the-scenegraph/"><strong>Building The Scenegraph</strong></a></li>
<li style="text-align: left;"><a href="http://localhost/wordpress/tutorials/defining-interactions/"><strong>Defining Interactions</strong></a></li>
<li style="text-align: left;"><a href="http://localhost/wordpress/tutorials/"><strong>Other Tutorial</strong></a></li>
</ol>
In the following tutorials we will show you, how to create, import and display cool models and bring them to the Data Arena.
Graphics programming experience is not a prerequisite, although it will help to have some understanding of the graphics pipeline.
&nbsp;&nbsp;
<h4>Technology stack</h4>
<p>(maybe make a diagram of technology stack here?)</p>
<p>The Data Arena synchronizes its displays using a library called Equalizer to replicate low-level graphics commands over a network. However you will most probably not have to interact with it. The user builds graphical applications by using omegalib (insert link), cyclops and/or OpenSceneGraph. Omegalib is middleware designed to ease the development of applications for virtual reality (VR) and immersive display environments and can integrate a variety of other frameworks. We use OpenSceneGraph (insert link), a powerful graphics rendering library, to render our graphics.</p>
<p>However, OpenSceneGraph is also a fairly complex library with a steep learning curve. Therefore, cyclops (insert link), a high-level API for osg is used to do common graphic operations in the Data Arena. The Data Arena also provides custom classes to handle standard use-cases and to ease the first steps.</p>
<p>&nbsp;</p>
<img src="http://localhost/wordpress/wp-content/uploads/2016/06/placeholder.jpg" srcset="https://localhost/wordpress/wp-content/uploads/2016/06/placeholder.jpg 498w, https://localhost/wordpress/wp-content/uploads/2016/06/placeholder-300x221.jpg 300w, https://localhost/wordpress/wp-content/uploads/2016/06/placeholder-230x169.jpg 230w, https://localhost/wordpress/wp-content/uploads/2016/06/placeholder-350x258.jpg 350w, https://localhost/wordpress/wp-content/uploads/2016/06/placeholder-480x354.jpg 480w" class="so-widget-image" height="367" width="498">
&nbsp;&nbsp;			<h4> Getting Started </h4>
The Data Arena VM comes with all the software needed to display things in the Data Arena.
For this tutorial, we will mostly interact with scripts inside the "/local/examples/" folder, which contains the examples of this tutorial(s) and the custom handlers (in the pipelines folder).
So lets get started and build our first immersive application!
<h4>Cube Tutorial</h4>
<p>The hello world program of the graphics world is displaying a simple object, such as a cube. Before being able to display anything, you have to have a model of a cube first, of course. Creating and exporting models will be covered in the next tutorial, for now, take the "box.obj" model from the "examples/box" folder. Wavefront (.obj) models are a popular format for exchanging 3d models between different applications. They contain the definition of the geometry, colors and many optional definitions. Fortunately, we don't have to parse this model by ourselves but can use a model loader, which is part of the osg package. The "Geometry" class takes care of loading the model and adding it to the scenegraph (more on that later).</p>
<p>The following is a minimal working example:</p>
<pre><span class="kn">import</span> <span class="nn">sys</span>
<span class="n">sys</span><span class="o">.</span><span class="n">path</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="s1">'/local/examples'</span><span class="p">)</span>
<span class="kn">from</span> <span class="nn">pipelines.objects</span> <span class="kn">import</span> <span class="n">Geometry</span>
<span class="kn">from</span> <span class="nn">pipelines.handler</span> <span class="kn">import</span> <span class="n">GeometryHandler</span> 
<span class="n">fileToLoad</span> <span class="o">=</span> <span class="s2">"/local/examples/box/box.obj"</span>
<span class="n">geo</span> <span class="o">=</span> <span class="n">Geometry</span><span class="p">(</span><span class="n">fileToLoad</span><span class="p">)</span>
<span class="n">handler</span> <span class="o">=</span> <span class="n">GeometryHandler</span><span class="p">()</span>
<span class="n">handler</span><span class="o">.</span><span class="n">initialCamPosition</span> <span class="o">=</span> <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">5</span><span class="p">]</span>
<span class="n">handler</span><span class="o">.</span><span class="n">addGeo</span><span class="p">(</span><span class="n">geo</span><span class="p">)</span>
</pre>
<p>The code above adds the examples folder to the system path, so the pipelines are importable.<br>
Then, by creating an Geometry object and giving it the path to the model, the box.obj model is loaded, added to the scene and its material is set. Have a look at "objects.py" (link to geometry docs or source), to see what exactly is going on.</p>
<p>Then a GeometryHandler is instanced and the geometry is registered with the addGeo() method. This step ensures, that the camera is focused on the center of the model. Before adding geometry, set the initial camera position to have a higher z value, so the camera looks from above onto the object and is not too close.</p>
<p>(embed box1 image)</p>
<p><img class="alignnone size-medium wp-image-562" src="http://localhost/wordpress/wp-content/uploads/2016/06/box1-300x169.png" alt="box1" srcset="https://localhost/wordpress/wp-content/uploads/2016/06/box1-300x169.png 300w, https://localhost/wordpress/wp-content/uploads/2016/06/box1-768x432.png 768w, https://localhost/wordpress/wp-content/uploads/2016/06/box1-830x467.png 830w, https://localhost/wordpress/wp-content/uploads/2016/06/box1-230x129.png 230w, https://localhost/wordpress/wp-content/uploads/2016/06/box1-350x197.png 350w, https://localhost/wordpress/wp-content/uploads/2016/06/box1-480x270.png 480w, https://localhost/wordpress/wp-content/uploads/2016/06/box1.png 854w" sizes="(max-width: 300px) 100vw, 300px" height="169" width="300"></p>
<p>To add another box to the scene, you can load the box in a new Geometry, set its initial position to a different position and register it to the GeometryHandler. Also set the initial camera position to the middle of both cubes.</p>
<pre><span class="c1">#update the initial camera position</span>
<span class="n">handler</span><span class="o">.</span><span class="n">initialCamPosition</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">5</span><span class="p">]</span> 
<span class="c1">#add new box</span>
<span class="n">geo2</span> <span class="o">=</span> <span class="n">Geometry</span><span class="p">(</span><span class="n">fileToLoad</span><span class="p">)</span>
<span class="n">geo2</span><span class="o">.</span><span class="n">initialPosition</span> <span class="o">=</span> <span class="p">[</span><span class="mi">2</span><span class="p">,</span><span class="mi">0</span><span class="p">,</span><span class="mi">0</span><span class="p">]</span>
<span class="n">handler</span><span class="o">.</span><span class="n">addGeo</span><span class="p">(</span><span class="n">geo2</span><span class="p">)</span>
</pre>
<p>(embed box2 image)</p>
<p><img class="alignnone size-medium wp-image-563" src="http://localhost/wordpress/wp-content/uploads/2016/06/box2-300x170.png" alt="box2" srcset="https://localhost/wordpress/wp-content/uploads/2016/06/box2-300x170.png 300w, https://localhost/wordpress/wp-content/uploads/2016/06/box2-768x434.png 768w, https://localhost/wordpress/wp-content/uploads/2016/06/box2-830x469.png 830w, https://localhost/wordpress/wp-content/uploads/2016/06/box2-230x130.png 230w, https://localhost/wordpress/wp-content/uploads/2016/06/box2-350x198.png 350w, https://localhost/wordpress/wp-content/uploads/2016/06/box2-480x271.png 480w, https://localhost/wordpress/wp-content/uploads/2016/06/box2.png 849w" sizes="(max-width: 300px) 100vw, 300px" height="170" width="300"></p>
<p>Now both boxes are displayed, but we can't interact with them yet. The GeometryHandler class contains configurable interaction handlers, which let you control the model using different input devices (mouse, ps4 controller, space navigator). To use the event handlers, they have to be registered in omegalib.</p>
<pre><span class="n">setEventFunction</span><span class="p">(</span><span class="n">handler</span><span class="o">.</span><span class="n">onEvent</span><span class="p">)</span>
<span class="n">setUpdateFunction</span><span class="p">(</span><span class="n">handler</span><span class="o">.</span><span class="n">onUpdate</span><span class="p">)</span>
</pre>
<p>The setEventFunction (add link) passes through all input events to the handler's onEvent function, the setUpdateFunction (add link) registers a script function to be called before each frame is rendered.<br>
Now the boxes can be rotate in the scene. The interaction handler provides several ways to constrain the movement of the camera and of the object, which are displayed in the console.<br>
When pressing "m", the mode can be toggled between object mode to camera mode. You can use object mode to rotate and translate the object and camera mode to orient yourself in the space in a first person way.</p>
<p>(embed box3 image)</p>
<p><img class="alignnone size-medium wp-image-564" src="http://localhost/wordpress/wp-content/uploads/2016/06/box3-300x168.png" alt="box3" srcset="https://localhost/wordpress/wp-content/uploads/2016/06/box3-300x168.png 300w, https://localhost/wordpress/wp-content/uploads/2016/06/box3-768x431.png 768w, https://localhost/wordpress/wp-content/uploads/2016/06/box3-830x466.png 830w, https://localhost/wordpress/wp-content/uploads/2016/06/box3-230x129.png 230w, https://localhost/wordpress/wp-content/uploads/2016/06/box3-350x196.png 350w, https://localhost/wordpress/wp-content/uploads/2016/06/box3-480x269.png 480w, https://localhost/wordpress/wp-content/uploads/2016/06/box3.png 850w" sizes="(max-width: 300px) 100vw, 300px" height="168" width="300"></p>
<p>In the next tutorial, you will learn how to apply simple materials to objects.</p>
&nbsp;&nbsp;&nbsp;&nbsp;
<span class="sow-icon-fontawesome" data-sow-icon="" style="font-size: 24px; color: #3d3d3d"></span>			
<p class="sow-more-text">
<a href="http://localhost/wordpress/tutorials/load-box/">						Previous Tutorial						</a>					</p>
<span class="sow-icon-fontawesome" data-sow-icon="" style="font-size: 24px; color: #3d3d3d"></span>			
<p class="sow-more-text">
<a href="http://localhost/wordpress/tutorials/building-the-scenegraph/">						Next Tutorial						</a>					</p>