---
ID: 1412
post_title: data
author: davm
post_date: 2016-08-09 08:31:45
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/2userguide/data/
published: true
panels_data:
  - |
    a:3:{s:7:"widgets";a:5:{i:0;a:6:{s:5:"title";s:0:"";s:4:"text";s:46:"<h3 style="text-align: center;">Userguide</h3>";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578723843cea2";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:0;s:9:"widget_id";s:36:"1ea35202-0ffb-4952-88db-1380842ca3f4";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:1;a:5:{s:8:"headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:4:"left";s:24:"so_field_container_state";s:4:"open";}s:12:"sub_headline";a:6:{s:4:"text";s:0:"";s:3:"tag";s:2:"h3";s:4:"font";s:7:"default";s:5:"color";b:0;s:5:"align";s:6:"center";s:24:"so_field_container_state";s:4:"open";}s:7:"divider";a:8:{s:5:"style";s:5:"solid";s:6:"weight";s:4:"thin";s:5:"color";b:0;s:11:"side_margin";s:4:"20px";s:16:"side_margin_unit";s:2:"px";s:10:"top_margin";s:4:"20px";s:15:"top_margin_unit";s:2:"px";s:24:"so_field_container_state";s:4:"open";}s:12:"_sow_form_id";s:13:"57871dc1b3fe7";s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Headline_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:1;s:9:"widget_id";s:36:"42c24578-cfd7-4dd5-8d52-e5b5178da0b8";s:5:"style";a:2:{s:7:"padding";s:3:"0px";s:18:"background_display";s:4:"tile";}}}i:2;a:6:{s:5:"title";s:0:"";s:4:"text";s:905:"<h4>User Guide</h4>
    <ol>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/"> User Guide </a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/overview/"> Overview </a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/quickstart/"><strong> Quickstart</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/examples/"><strong> Examples</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/pipelines/"><strong> Pipelines</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/data/"><strong> Data</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/visualizationtools/"><strong> Visualization Tools</strong></a></li>
     	<li style="text-align: left;"><a href="/wordpress/2userguide/softwarebackend/"><strong> Software/Backend</strong></a></li>
    </ol>";s:20:"text_selected_editor";s:4:"html";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"576b4c626e8f5";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:0;s:2:"id";i:2;s:9:"widget_id";s:36:"4a98973e-09c0-48a2-923d-fcbc887ca755";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:3;a:6:{s:5:"title";s:0:"";s:4:"text";s:4756:"<p>The number of 3D geometry data formats is endless.<br />We recommend <a href="http://meshlab.sourceforge.net/">MeshLab</a> to convert between a few standard formats.<br />If your data is not available in one of these, you find below the documentation of .ply, a very simple but powerful format.<br />This should allow you to transform your data yourself to make use of the available piplelines.</p><h5>PLY</h5><p>The PLY format provides a basic description of 3D objects. Data in this format can easily be displayed in the Data Arena.<br />Meta information and the data itself is represented in a plain text file with the following format:</p><pre><code>ply
    format ascii 1.0  
    element vertex 2
    property float x
    property float y
    element face 1 
    property list uchar int vertex_index
    end_header
    0 0
    0 1
    2 0 1</code></pre><p>The first two lines, as well as <em>end_header</em>, are mandatory for each file. The actual data is located after the header until the end of the file.</p><ul><li><em>element</em> introduces a data description, the example object has two vertices</li><li><em>property</em> describes the structure of one vertex data entry, each vertex consists of two float values (namely x and y)</li><li><em>face</em> elements are of type <em>list</em>, represented in the following structure<ul><li>the head of a list is of type <em>uchar</em> and specifies the list length</li><li>each list entry is of type <em>int</em></li><li>the list is named <em>vertex_index</em>, each value in the list represents the index of an earlier listed vertex</li><li>all vertices of a list describe one face of the object</li></ul></li></ul><p>After the header, the actual data follows. First all vertex elements, one each line, with its properties separated by a blank space.<br />As the number of vertices was specified before, the next elements (faces) follow without indication.</p><p>The most important property data types are: <em>char</em>, <em>uchar</em>, <em>int</em>, <em>float</em> and <em>double</em>.<br />An optional keyword to describe the data in the header is <em>comment</em> followed by any text.</p><p>Extensive documentation can be found <a href="http://paulbourke.net/dataformats/ply/">here</a>.</p><h5>OBJ</h5><p>Another popular geometery format is the old Wavefront .obj file format.<br />It’s about as simple as .ply format, which is why it’s still used today.<br />There’s a <a href="https://en.wikipedia.org/wiki/Wavefront_.obj_file">wikipedia entry</a> for .obj</p><p>This (below) is what a simple box looks like in .obj format.<br />The size of the box is 1 unit in X, 2 units high in Y, and 3 units deep in Z.<br />One corner of the box is at the origin (0,0,0). A box has 8 corners (vertices ‘v’)<br />and has 6 sides (faces ‘f’).</p><pre><code># File exported by Houdini 15.0.244.16 (www.sidefx.com)
    # 8 points
    # 24 vertices
    # 6 primitives
    # Bounds: [0, 0, 0] to [1, 2, 3]
    g
    v 0 0 0
    v 1 0 0
    v 1 0 3
    v 0 0 3
    v 0 2 0
    v 1 2 0
    v 1 2 3
    v 0 2 3
    g
    f 2 1 5 6
    f 3 2 6 7
    f 4 3 7 8
    f 1 4 8 5
    f 3 4 1 2
    f 6 5 8 7</code></pre><h4>Spreadsheet</h4><p>Data in form of tables is usually organized with Microsoft Excel or LibreOffice.<br />These programs allow export to the layout-free CSV format, which is easier to process.</p><h5>CSV</h5><p>Generally, CSV is a text-encoded file with separated values in rows.<br />Each row represents an entry with the columns as attributes.<br />Usually, the first row contains a name for each attribute encoded as text.<br />To allow consistent processing, we expect all string values be escaped in doulbe quotes ("String").<br />Further, the separation of values should be done with commas, even though other characters are allowed.<br />Find below a short example CSV to be visualized with the parallel coordinates pipeline:</p><pre><code>"City","Temperature","Rainfall","Month"
    "Sydney",25,0,10
    "Sydney",22,1,09
    "Melbourne",20,2,11
    "Melbourne",19,3,10
    ...</code></pre><p>The values of "City" come form a fixed set and repeat.<br />This indicates a good attribute for grouping within the parallel coordinates diagram.</p><h4>Houdini</h4><p>Houdini supports a range of geometry <a href="http://www.sidefx.com/docs/houdini15.0/io/formats/channel_formats">formats</a>, to import and export models and use the available piplines.<br />Data other than 3D can be imported to Houdini via channel files.</p><h5>CHAN</h5><p>The .chan file format comes from Houdini and allows to import your data and use it in Houdini to create geometry.<br />The format is similar to CSV, as it also represents data in a text file.<br />Each row represents data of one frame and attributes are separated by space.<br />In contrast to CSV, there is no header row and string string values are not supported at all.</p>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"57a99536f293b";s:11:"panels_info";a:6:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:4:"grid";i:1;s:4:"cell";i:1;s:2:"id";i:3;s:9:"widget_id";s:36:"cb19230b-f332-4ffe-b55a-ccd3868ff53c";s:5:"style";a:2:{s:27:"background_image_attachment";b:0;s:18:"background_display";s:4:"tile";}}}i:4;a:14:{s:8:"features";a:3:{i:0;a:9:{s:15:"container_color";b:0;s:4:"icon";s:31:"fontawesome-arrow-circle-o-left";s:10:"icon_color";s:7:"#3d3d3d";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:9:"Previous ";s:8:"more_url";s:0:"";}i:1;a:9:{s:15:"container_color";s:7:"#404040";s:4:"icon";s:0:"";s:10:"icon_color";s:7:"#FFFFFF";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:0:"";s:8:"more_url";s:0:"";}i:2;a:9:{s:15:"container_color";s:7:"#e8e8e8";s:4:"icon";s:32:"fontawesome-arrow-circle-o-right";s:10:"icon_color";s:7:"#3d3d3d";s:10:"icon_image";i:0;s:15:"icon_image_size";s:4:"full";s:5:"title";s:0:"";s:4:"text";s:0:"";s:9:"more_text";s:5:"Next ";s:8:"more_url";s:0:"";}}s:5:"fonts";a:4:{s:13:"title_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:12:"text_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:17:"more_text_options";a:5:{s:4:"font";s:7:"default";s:4:"size";b:0;s:9:"size_unit";s:2:"px";s:5:"color";b:0;s:24:"so_field_container_state";s:6:"closed";}s:24:"so_field_container_state";s:6:"closed";}s:15:"container_shape";s:0:"";s:14:"container_size";s:4:"84px";s:19:"container_size_unit";s:2:"px";s:9:"icon_size";s:4:"24px";s:14:"icon_size_unit";s:2:"px";s:7:"per_row";i:3;s:10:"responsive";b:1;s:12:"_sow_form_id";s:13:"57873dc4344d9";s:10:"title_link";b:0;s:9:"icon_link";b:0;s:10:"new_window";b:0;s:11:"panels_info";a:7:{s:5:"class";s:33:"SiteOrigin_Widget_Features_Widget";s:3:"raw";b:0;s:4:"grid";i:4;s:4:"cell";i:0;s:2:"id";i:4;s:9:"widget_id";s:36:"9cfce0d0-9f38-47ab-930d-0f36248ba8e9";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}}s:5:"grids";a:5:{i:0;a:2:{s:5:"cells";i:1;s:5:"style";a:3:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:1;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"10px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:2;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:3;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}i:4;a:2:{s:5:"cells";i:1;s:5:"style";a:0:{}}}s:10:"grid_cells";a:11:{i:0;a:2:{s:4:"grid";i:0;s:6:"weight";i:1;}i:1;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.226999999999999813038442653123638592660427093505859375;}i:2;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.69836738703339928946434156387113034725189208984375;}i:3;a:2:{s:4:"grid";i:1;s:6:"weight";d:0.0746326129666009252527913986341445706784725189208984375;}i:4;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.2312091503267995340475948751191026531159877777099609375;}i:5;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.6937117253778286585230716809746809303760528564453125;}i:6;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.07507912429537184906269686734958668239414691925048828125;}i:7;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.229575163398691384220029476637137122452259063720703125;}i:8;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.69444444444444408670591428744955919682979583740234375;}i:9;a:2:{s:4:"grid";i:3;s:6:"weight";d:0.07598039215686445968511719684101990424096584320068359375;}i:10;a:2:{s:4:"grid";i:4;s:6:"weight";i:1;}}}
---
<h3 style="text-align: center;">Userguide</h3>
<h4>User Guide</h4>
<ol>
<li style="text-align: left;"><a href="/wordpress/2userguide/"> User Guide </a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/overview/"> Overview </a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/quickstart/"><strong> Quickstart</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/examples/"><strong> Examples</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/pipelines/"><strong> Pipelines</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/data/"><strong> Data</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/visualizationtools/"><strong> Visualization Tools</strong></a></li>
<li style="text-align: left;"><a href="/wordpress/2userguide/softwarebackend/"><strong> Software/Backend</strong></a></li>
</ol>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<span class="sow-icon-fontawesome" data-sow-icon="" style="font-size: 24px; color: #3d3d3d"></span>			
<p class="sow-more-text">
Previous 											</p>
<span class="sow-icon-fontawesome" data-sow-icon="" style="font-size: 24px; color: #3d3d3d"></span>			
<p class="sow-more-text">
Next 											</p>