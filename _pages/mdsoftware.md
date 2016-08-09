---
ID: 1399
post_title: mdsoftware
author: davm
post_date: 2016-08-09 07:01:44
post_excerpt: ""
layout: page
permalink: http://localhost/wordpress/mdsoftware/
published: true
---
[md]


In the backend of the Data Arena, we run the same software stack as in the virtual machine.
That makes it possible to abstract from the backend and prototype your visualization in the virtual machine, instead of the Data Arena.
If you still require some information about the software, we give a short overview on this page.

## Equalizer

Equalizer is the rendering framework, which allows to create a window either on your screen in the virtual machine or the projectors in the Data Arena.
It parallizes the rendering, allows 3D projection and much more.
The open source project is available on [GitHub](https://github.com/Eyescale/Equalizer).
Extensiv documentation can be found [here](http://www.equalizergraphics.com/documentation.html).

## Omegalib

All graphic visualization is created with the omegalib framework, which interacts with Equalizer.
It is an abstraction of OpenGL and allows developement in Python.
Primitive objects, an Open Scene Graph or webviews are all integrated or available over modules.

The Python API is documented [here](https://github.com/uic-evl/omegalib/wiki/Python-Reference##omegalib-python-reference).
Unfortunately, this is not frequently updated, but provides a sufficient overview of the functionality.
For comprehensive documentation, we refer to the [sources](https://github.com/uic-evl/omegalib/blob/master/src/omega/omegaPythonApi.cpp), since the project is also available on [GitHub](https://github.com/uic-evl/omegalib).

## VRPN

A VRPN server provides an interface for all **V**irtual **R**eality **P**eripherals.
With that, we can handle a variety of input devices, such as Mouse, Keyboard, Motion Tracker, Space Navigator or Gamepads.
The software is on [GitHub](https://github.com/vrpn/vrpn/wiki) and documentation can be found [here](http://dev.vrpn.org/docs/classes.html).

[/md]