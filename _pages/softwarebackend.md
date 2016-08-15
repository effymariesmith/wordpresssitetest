---
ID: 1405
post_title: Software
author: davm
post_date: 2016-08-09 07:51:22
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/2userguide/softwarebackend/
published: true
---
In the backend of the Data Arena, we run the same software stack as in the virtual machine.
That makes it possible to abstract from the backend and prototype your visualization in the virtual machine, instead of the Data Arena.
If you still require some information about the software, we give a short overview on this page.
<h4>Equalizer</h4>
Equalizer is the rendering framework, which allows to create a window either on your screen in the virtual machine or the projectors in the Data Arena.
It parallizes the rendering, allows 3D projection and much more.
The open source project is available on <a href="https://github.com/Eyescale/Equalizer">GitHub</a>.
Extensiv documentation can be found <a href="http://www.equalizergraphics.com/documentation.html">here</a>.
<h4>Omegalib</h4>
All graphic visualization is created with the omegalib framework, which interacts with Equalizer.
It is an abstraction of OpenGL and allows developement in Python.
Primitive objects, an Open Scene Graph or webviews are all integrated or available over modules.

The Python API is documented <a href="https://github.com/uic-evl/omegalib/wiki/Python-Reference##omegalib-python-reference">here</a>.
Unfortunately, this is not frequently updated, but provides a sufficient overview of the functionality.
For comprehensive documentation, we refer to the <a href="https://github.com/uic-evl/omegalib/blob/master/src/omega/omegaPythonApi.cpp">sources</a>, since the project is also available on <a href="https://github.com/uic-evl/omegalib">GitHub</a>.
<h4>VRPN</h4>
A VRPN server provides an interface for all <strong>V</strong>irtual <strong>R</strong>eality <strong>P</strong>eripherals.
With that, we can handle a variety of input devices, such as Mouse, Keyboard, Motion Tracker, Space Navigator or Gamepads.
The software is on <a href="https://github.com/vrpn/vrpn/wiki">GitHub</a> and documentation can be found <a href="http://dev.vrpn.org/docs/classes.html">here</a>.