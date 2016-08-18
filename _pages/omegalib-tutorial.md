---
ID: 872
post_title: Omegalib Tutorials
author: davm
post_date: 2016-07-14 07:05:54
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/omegalib-tutorials/omegalib-tutorial/
published: true
---
[md]

##Welcome to the Data Arena VM tutorial series.
In the following tutorials, we will show you how to create, import and display cool models and bring them to the Data Arena.

Graphics programming experience is not a prerequisite, although it will help to have some understanding of the graphics pipeline.

# Technology stack


The Data Arena synchronizes its displays using a library called Equalizer to replicate low-level graphics commands over a network. However, you will most probably not have to interact with it. The user builds graphical applications by using omegalib (insert link), cyclops and/or OpenSceneGraph. Omegalib is middleware designed to ease the development of applications for virtual reality (VR) and immersive display environments and can integrate a variety of other frameworks. We use OpenSceneGraph (insert link), a powerful graphics rendering library, to render our graphics. However, OpenSceneGraph is also a fairly complex library with a steep learning curve. Therefore, cyclops (insert link), a high-level API for osg is used to do common graphic operations in the Data Arena. The Data Arena also provides custom classes to handle standard use-cases and to ease the first steps.

[/md]