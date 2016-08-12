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
panels_data:
  - |
    a:3:{s:7:"widgets";a:5:{i:0;a:6:{s:5:"title";s:0:"";s:4:"text";s:46:"<h3 style="text-align: center;">Userguide</h3>";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578723843cea2";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:0;s:9:"widget_id";s:36:"1ea35202-0ffb-4952-88db-1380842ca3f4";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:1;a:5:{s:8:"headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:4:"left";s:24:"so_field_container_state";s:4:"open";}s:12:"sub_headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:6:"center";s:24:"so_field_container_state";s:4:"open";}s:7:"divider";a:8:{s:5:"style";s:5:"solid";s:6:"weight";s:4:"thin";s:5:"color";b:0;s:11:"side_margin";s:4:"20px";s:16:"side_margin_unit";s:2:"px";s:10:"top_margin";s:4:"20px";s:15:"top_margin_unit";s:2:"px";s:24:"so_field_container_state";s:4:"open";}s:12:"_sow_form_id";s:13:"57871dc1b3fe7";s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Headline_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:1;s:9:"widget_id";s:36:"42c24578-cfd7-4dd5-8d52-e5b5178da0b8";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:2;a:6:{s:5:"title";s:0:"";s:4:"text";s:910:"<h4>User Guide</h4>
    <ol>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/"> User Guide </a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/overview/"> Overview </a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/quickstart/"><strong> Quickstart</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/examples/"><strong> Examples</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/pipelines/"><strong> Pipelines</strong></a></li>
            <li style="text-align: left;"><a href="/wordpress/2userguide/data/"><strong>Data</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/visualizationtools/"><strong> Visualization Tools</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/softwarebackend/"><strong> Software/Backend</strong></a></li>
    </ol>";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"576b4c626e8f5";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:0;s:2:"id";i:2;s:9:"widget_id";s:36:"4a98973e-09c0-48a2-923d-fcbc887ca755";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:3;a:6:{s:5:"title";s:0:"";s:4:"text";s:2722:"Have a look at the already developed <a href="/wordpress/2userguide/examples/">examples</a>.
    
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
    In the Data Arena, we can open the project file and interact with the visualization.";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"57a9926dd28b0";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:1;s:2:"id";i:3;s:9:"widget_id";s:36:"c5513b87-3667-4586-96de-fec56e786160";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:4;a:14:{s:8:"features";a:3:{i:0;a:9:{s:15:"container_color";b:0;s:4:"icon";s:31:"fontawesome-arrow-circle-o-left";s:10:"icon_color";s:7:"#3d3d3d";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:9:"Previous ";s:8:"more_url";s:0:"";}i:1;a:9:{s:15:"container_color";s:7:"#404040";s:4:"icon";s:0:"";s:10:"icon_color";s:7:"#FFFFFF";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:0:"";s:8:"more_url";s:0:"";}i:2;a:9:{s:15:"container_color";s:7:"#e8e8e8";s:4:"icon";s:32:"fontawesome-arrow-circle-o-right";s:10:"icon_color";s:7:"#3d3d3d";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:5:"Next ";s:8:"more_url";s:0:"";}}s:5:"fonts";a:4:{s:13:"title_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:12:"text_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:17:"more_text_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:24:"so_field_container_state";s:6:"closed";}s:15:"container_shape";s:0:"";s:14:"container_size";s:4:"84px";s:19:"container_size_unit";s:2:"px";s:9:"icon_size";s:4:"24px";s:14:"icon_size_unit";s:2:"px";s:7:"per_row";i:3;s:10:"responsive";b:1;s:12:"_sow_form_id";s:13:"57873dc4344d9";s:10:"title_link";b:0;s:9:"icon_link";b:0;s:10:"new_window";b:0;s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Features_Widget";s:3:"raw";b:0;s:4:"grid";i:2;s:4:"cell";i:0;s:2:"id";i:4;s:9:"widget_id";s:36:"9cfce0d0-9f38-47ab-930d-0f36248ba8e9";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}}s:5:"grids";a:3:{i:0;a:2:{s:5:"cells";i:1;s:5:"style";a:3:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:1;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"10px";s:5:"align";s:0:"";s:16:"background_image";b:0;s:14:"column_padding";s:0:"";}}i:2;a:2:{s:5:"cells";i:1;s:5:"style";a:0:{}}}s:10:"grid_cells";a:5:{i:0;a:2:{s:4:"grid";i:0;s:6:"weight";i:1;}i:1;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.226999999999999813038442653123638592660427093505859375;}i:2;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.69836738703339928946434156387113034725189208984375;}i:3;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.0746326129666009252527913986341445706784725189208984375;}i:4;a:2:{s:4:"grid";i:2;s:6:"weight";i:1;}}}
---
<h3 style="text-align: center;">Userguide</h3>
<h4>User Guide</h4>
<ol>
<li style="text-align: left;"><a href="/wordpress/2userguide/"> User Guide </a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/overview/"> Overview </a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/quickstart/"><strong> Quickstart</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/examples/"><strong> Examples</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/pipelines/"><strong> Pipelines</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/data/"><strong>Data</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/visualizationtools/"><strong> Visualization Tools</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/softwarebackend/"><strong> Software/Backend</strong></a></li>
</ol>
<p>Have a look at the already developed <a href="/wordpress/2userguide/examples/">examples</a>.</p>
<p>&nbsp;</p>
<h3>3D</h3>
<p>This is a guide to load 3D data into the Data Arena virtual machine.<br>
The format we consider here are object models in <a href="{filename}data.md">.ply,</a> .obj and other formats.<br>
A few examples are provided in <code>/local/examples</code>.</p>
<ol>
<li>Copy the file <code>/local/examples/box/LoadBox.py</code></li>
<li>Change the variable <code>fileToLoad</code> to the absolute path of your file</li>
<li>Load the object with <code>orun LoadBox.py</code> in your working directory</li>
</ol>
<p>To adjust your model, you can add several parameters, such as positioning of object and camera, adding a shader for textures or changing the navigation behavior.<br>
See other examples or the <a href="/wordpress/2userguide/examples/">API documentation</a> for more details.</p>
<h3>Motion Capture</h3>
<p>In order to visualize motion capture data, you first need to preprocess the data with Houdini and create a <a href="/wordpress/2userguide/data/">channel file</a>.<br>
Read more about Houdini <a href="/wordpress/2userguide/visualizationtools/">here</a>.</p>
<p>After that, you can load the motion capture OTL with <code>orun /loca/examples/mocap/LoadOTL.py</code>.<br>
In the menu, you can enter the file path to your .chan file.<br>
The other parameters specify frames, which are left out at start and end of the scene.</p>
<p>Now you can play (Space) the scene, jump between frames (f: forward, b:backward) or seconds (Shift+f, Shift+b).</p>
<h3>Parallel Coordinates</h3>
<p>This pipeline creates a parallel coordinates diagram from a CSV file.<br>
First, export your spreadsheet as CSV, include the column header and escape non numeric values. <em>Mind data values can be numeric or categorical.</em></p>
<p>With the command <code>python /local/examples/parallel/builder/builder.py PATH_TO_CSV GROUP_COLUMN</code> you create the diagram.<br>
The GROUP_COLUMN specifies the coloring in the diagram (values of this column are grouped and should appear in multiple rows).</p>
<p>If there are spaces in your column names, specify them using quotes. An example of this: ‘Market Share’, or ‘Year To Date Average’.</p>
<p>In the working directory, you will find a new directory named after the CSV file.<br>
You can view the website <code>index.html</code> locally or run <code>orun LoadParallel.py</code> to launch the Data Arena environment.</p>
<h3>drishti</h3>
<p>We also run visualizations developed with Drishti.<br>
This software creates 3D, textured models from image slices.<br>
You can download the program from <a href="https://github.com/AjayLimaye/drishti">GitHub</a> and create your model.<br>
In the Data Arena, we can open the project file and interact with the visualization.</p>
&nbsp;
<span class="sow-icon-fontawesome" data-sow-icon="" style="font-size: 24px; color: #3d3d3d"></span>			
<p class="sow-more-text">
Previous 											</p>
<span class="sow-icon-fontawesome" data-sow-icon="" style="font-size: 24px; color: #3d3d3d"></span>			
<p class="sow-more-text">
Next 											</p>