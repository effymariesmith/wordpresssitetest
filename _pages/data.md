---
ID: 1412
post_title: Data
author: davm
post_date: 2016-08-09 08:31:45
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/2userguide/data/
published: true
panels_data:
  - |
    a:3:{s:7:"widgets";a:1:{i:0;a:6:{s:5:"title";s:0:"";s:4:"text";s:4756:"<p>The number of 3D geometry data formats is endless.<br />We recommend <a href="http://meshlab.sourceforge.net/">MeshLab</a> to convert between a few standard formats.<br />If your data is not available in one of these, you find below the documentation of .ply, a very simple but powerful format.<br />This should allow you to transform your data yourself to make use of the available piplelines.</p><h5>PLY</h5><p>The PLY format provides a basic description of 3D objects. Data in this format can easily be displayed in the Data Arena.<br />Meta information and the data itself is represented in a plain text file with the following format:</p><pre><code>ply
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
    ...</code></pre><p>The values of "City" come form a fixed set and repeat.<br />This indicates a good attribute for grouping within the parallel coordinates diagram.</p><h4>Houdini</h4><p>Houdini supports a range of geometry <a href="http://www.sidefx.com/docs/houdini15.0/io/formats/channel_formats">formats</a>, to import and export models and use the available piplines.<br />Data other than 3D can be imported to Houdini via channel files.</p><h5>CHAN</h5><p>The .chan file format comes from Houdini and allows to import your data and use it in Houdini to create geometry.<br />The format is similar to CSV, as it also represents data in a text file.<br />Each row represents data of one frame and attributes are separated by space.<br />In contrast to CSV, there is no header row and string string values are not supported at all.</p>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"57a99536f293b";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:0;s:9:"widget_id";s:36:"cb19230b-f332-4ffe-b55a-ccd3868ff53c";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}}s:5:"grids";a:1:{i:0;a:2:{s:5:"cells";i:1;s:5:"style";a:4:{s:7:"padding";s:4:"10px";s:5:"align";s:0:"";s:16:"background_image";b:0;s:14:"column_padding";s:0:"";}}}s:10:"grid_cells";a:1:{i:0;a:2:{s:4:"grid";i:0;s:6:"weight";i:1;}}}
---
The number of 3D geometry data formats is endless.
We recommend <a href="http://meshlab.sourceforge.net/">MeshLab</a> to convert between a few standard formats.
If your data is not available in one of these, you find below the documentation of .ply, a very simple but powerful format.
This should allow you to transform your data yourself to make use of the available piplelines.
<h5>PLY</h5>
The PLY format provides a basic description of 3D objects. Data in this format can easily be displayed in the Data Arena.
Meta information and the data itself is represented in a plain text file with the following format:
<pre><code>ply
format ascii 1.0  
element vertex 2
property float x
property float y
element face 1 
property list uchar int vertex_index
end_header
0 0
0 1
2 0 1</code></pre>
The first two lines, as well as <em>end_header</em>, are mandatory for each file. The actual data is located after the header until the end of the file.
<ul>
 	<li><em>element</em> introduces a data description, the example object has two vertices</li>
 	<li><em>property</em> describes the structure of one vertex data entry, each vertex consists of two float values (namely x and y)</li>
 	<li><em>face</em> elements are of type <em>list</em>, represented in the following structure
<ul>
 	<li>the head of a list is of type <em>uchar</em> and specifies the list length</li>
 	<li>each list entry is of type <em>int</em></li>
 	<li>the list is named <em>vertex_index</em>, each value in the list represents the index of an earlier listed vertex</li>
 	<li>all vertices of a list describe one face of the object</li>
</ul>
</li>
</ul>
After the header, the actual data follows. First all vertex elements, one each line, with its properties separated by a blank space.
As the number of vertices was specified before, the next elements (faces) follow without indication.

The most important property data types are: <em>char</em>, <em>uchar</em>, <em>int</em>, <em>float</em> and <em>double</em>.
An optional keyword to describe the data in the header is <em>comment</em> followed by any text.

Extensive documentation can be found <a href="http://paulbourke.net/dataformats/ply/">here</a>.
<h5>OBJ</h5>
Another popular geometery format is the old Wavefront .obj file format.
It’s about as simple as .ply format, which is why it’s still used today.
There’s a <a href="https://en.wikipedia.org/wiki/Wavefront_.obj_file">wikipedia entry</a> for .obj

This (below) is what a simple box looks like in .obj format.
The size of the box is 1 unit in X, 2 units high in Y, and 3 units deep in Z.
One corner of the box is at the origin (0,0,0). A box has 8 corners (vertices ‘v’)
and has 6 sides (faces ‘f’).
<pre><code># File exported by Houdini 15.0.244.16 (www.sidefx.com)
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
f 6 5 8 7</code></pre>
<h4>Spreadsheet</h4>
Data in form of tables is usually organized with Microsoft Excel or LibreOffice.
These programs allow export to the layout-free CSV format, which is easier to process.
<h5>CSV</h5>
Generally, CSV is a text-encoded file with separated values in rows.
Each row represents an entry with the columns as attributes.
Usually, the first row contains a name for each attribute encoded as text.
To allow consistent processing, we expect all string values be escaped in doulbe quotes ("String").
Further, the separation of values should be done with commas, even though other characters are allowed.
Find below a short example CSV to be visualized with the parallel coordinates pipeline:
<pre><code>"City","Temperature","Rainfall","Month"
"Sydney",25,0,10
"Sydney",22,1,09
"Melbourne",20,2,11
"Melbourne",19,3,10
...</code></pre>
The values of "City" come form a fixed set and repeat.
This indicates a good attribute for grouping within the parallel coordinates diagram.
<h4>Houdini</h4>
Houdini supports a range of geometry <a href="http://www.sidefx.com/docs/houdini15.0/io/formats/channel_formats">formats</a>, to import and export models and use the available piplines.
Data other than 3D can be imported to Houdini via channel files.
<h5>CHAN</h5>
The .chan file format comes from Houdini and allows to import your data and use it in Houdini to create geometry.
The format is similar to CSV, as it also represents data in a text file.
Each row represents data of one frame and attributes are separated by space.
In contrast to CSV, there is no header row and string string values are not supported at all.