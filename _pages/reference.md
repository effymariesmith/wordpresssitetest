---
ID: 375
post_title: Reference
author: davm
post_date: 2016-06-27 07:49:49
post_excerpt: ""
layout: page
permalink: http://localhost/wordpress/reference/
published: true
---
<h3>Reference List</h3>
<form role="search" method="get" class="search-form" action="http://localhost/wordpress/">
<label>
<span class="screen-reader-text">Search for:</span>
<input class="search-field" placeholder="Search …" value="" name="s" type="search">
</label>
<input class="search-submit" value="Search" type="submit">
</form>
<h3> Analytic Tools</h3>
<p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel.</p>
<h4>Title</h4>
<p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo ligula, porttitor eu, consequat vitae, eleifend ac, enim. </p>
<p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo ligula, porttitor eu, consequat vitae, eleifend ac, enim. </p>
<h4>Title</h4>
<p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo ligula, porttitor eu, consequat vitae, eleifend ac, enim. </p>
<h3> System </h3>
<p>In the backend of the Data Arena, we run the same software stack as in the virtual machine.<br>
That makes it possible to abstract from the backend and prototype your visualization in the virtual machine, instead of the Data Arena.<br>
If you still require some information about the software, we give a short overview on this page.</p>
<h4>Equalizer</h4>
<p>Equalizer is the rendering framework, which allows to create a window either on your screen in the virtual machine or the projectors in the Data Arena.<br>
It parallizes the rendering, allows 3D projection and much more.<br>
The open source project is available on <a href="https://github.com/Eyescale/Equalizer">GitHub</a>.<br>
Extensiv documentation can be found <a href="http://www.equalizergraphics.com/documentation.html">here</a>.</p>
<h4>Omegalib</h4>
<p>All graphic visualization is created with the omegalib framework, which interacts with Equalizer.<br>
It is an abstraction of OpenGL and allows developement in Python.<br>
Primitive objects, an Open Scene Graph or webviews are all integrated or available over modules.</p>
<p>The Python API is documented <a href="https://github.com/uic-evl/omegalib/wiki/Python-Reference##omegalib-python-reference">here</a>.<br>
Unfortunately, this is not frequently updated, but provides a sufficient overview of the functionality.<br>
For comprehensive documentation, we refer to the <a href="https://github.com/uic-evl/omegalib/blob/master/src/omega/omegaPythonApi.cpp">sources</a>, since the project is also available on <a href="https://github.com/uic-evl/omegalib">GitHub</a>.</p>
<h4>VRPN</h4>
<p>A VRPN server provides an interface for all <strong>V</strong>irtual <strong>R</strong>eality <strong>P</strong>eripherals.<br>
With that, we can handle a variety of input devices, such as Mouse, Keyboard, Motion Tracker, Space Navigator or Gamepads.<br>
The software is on <a href="https://github.com/vrpn/vrpn/wiki">GitHub</a> and documentation can be found <a href="http://dev.vrpn.org/docs/classes.html">here</a>.</p>