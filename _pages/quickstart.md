---
ID: 1389
post_title: Quickstart
author: davm
post_date: 2016-08-09 06:55:37
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/2userguide/quickstart/
published: true
---
Have a look at the already developed <a href="/wordpress/2userguide/examples/">examples</a>.

&nbsp;
<h3>3D</h3>
This is a guide to load 3D data into the Data Arena virtual machine.
The format we consider here are object models in <a href="{filename}data.md">.ply,</a> .obj and other formats.
A few examples are provided in <code>/local/examples</code>.
<ol>
 	<li>Copy the file <code>/local/examples/box/LoadBox.py</code></li>
 	<li>Change the variable <code>fileToLoad</code> to the absolute path of your file</li>
 	<li>Load the object with <code>orun LoadBox.py</code> in your working directory</li>
</ol>
To adjust your model, you can add several parameters, such as positioning of object and camera, adding a shader for textures or changing the navigation behavior.
See other examples or the <a href="/wordpress/2userguide/examples/">API documentation</a> for more details.
<h3>Motion Capture</h3>
In order to visualize motion capture data, you first need to preprocess the data with Houdini and create a <a href="/wordpress/2userguide/data/">channel file</a>.
Read more about Houdini <a href="/wordpress/2userguide/visualizationtools/">here</a>.

After that, you can load the motion capture OTL with <code>orun /loca/examples/mocap/LoadOTL.py</code>.
In the menu, you can enter the file path to your .chan file.
The other parameters specify frames, which are left out at start and end of the scene.

Now you can play (Space) the scene, jump between frames (f: forward, b:backward) or seconds (Shift+f, Shift+b).
<h3>Parallel Coordinates</h3>
This pipeline creates a parallel coordinates diagram from a CSV file.
First, export your spreadsheet as CSV, include the column header and escape non numeric values. <em>Mind data values can be numeric or categorical.</em>

With the command <code>python /local/examples/parallel/builder/builder.py PATH_TO_CSV GROUP_COLUMN</code> you create the diagram.
The GROUP_COLUMN specifies the coloring in the diagram (values of this column are grouped and should appear in multiple rows).

If there are spaces in your column names, specify them using quotes. An example of this: ‘Market Share’, or ‘Year To Date Average’.

In the working directory, you will find a new directory named after the CSV file.
You can view the website <code>index.html</code> locally or run <code>orun LoadParallel.py</code> to launch the Data Arena environment.
<h3>drishti</h3>
We also run visualizations developed with Drishti.
This software creates 3D, textured models from image slices.
You can download the program from <a href="https://github.com/AjayLimaye/drishti">GitHub</a> and create your model.
In the Data Arena, we can open the project file and interact with the visualization.