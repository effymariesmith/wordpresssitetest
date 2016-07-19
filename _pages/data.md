---
ID: 354
post_title: Data
author: davm
post_date: 2016-06-27 07:20:05
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/userguide/data/
published: true
---
[md]

####  Geometry

The number of 3D geometry data formats is endless.
We recommend [MeshLab](http://meshlab.sourceforge.net/) to convert between a few standard formats.
If your data is not available in one of these, you find below the documentation of .ply, a very simple but powerful format.
This should allow you to transform your data yourself to make use of the available piplelines.

#####  PLY

The PLY format provides a basic description of 3D objects. Data in this format can easily be displayed in the Data Arena.
Meta information and the data itself is represented in a plain text file with the following format:

	ply
	format ascii 1.0  
	element vertex 2
	property float x
	property float y
	element face 1 
	property list uchar int vertex_index
	end_header
	0 0
	0 1
	2 0 1

The first two lines, as well as *end_header*, are mandatory for each file. The actual data is located after the header until the end of the file.

* *element* introduces a data description, the example object has two vertices
* *property* describes the structure of one vertex data entry, each vertex consists of two float values (namely x and y)
* *face* elements are of type *list*, represented in the following structure
	- the head of a list is of type *uchar* and specifies the list length
	- each list entry is of type *int*
	- the list is named *vertex_index*, each value in the list represents the index of an earlier listed vertex
	- all vertices of a list describe one face of the object

After the header, the actual data follows. First all vertex elements, one each line, with its properties separated by a blank space.
As the number of vertices was specified before, the next elements (faces) follow without indication.

The most important property data types are: *char*, *uchar*, *int*, *float* and *double*.
An optional keyword to describe the data in the header is *comment* followed by any text.

Extensive documentation can be found [here](http://paulbourke.net/dataformats/ply/).

#####  OBJ

Another popular geometery format is the old Wavefront .obj file format.
It's about as simple as .ply format, which is why it's still used today.
There's a [wikipedia entry](https://en.wikipedia.org/wiki/Wavefront_.obj_file) for .obj

This (below) is what a simple box looks like in .obj format.
The size of the box is 1 unit in X, 2 units high in Y, and 3 units deep in Z.
One corner of the box is at the origin (0,0,0). A box has 8 corners (vertices 'v')
and has 6 sides (faces 'f').

	# File exported by Houdini 15.0.244.16 (www.sidefx.com)
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
	f 6 5 8 7


####  Spreadsheet

Data in form of tables is usually organized with Microsoft Excel or LibreOffice.
These programs allow export to the layout-free CSV format, which is easier to process.

#####  CSV

Generally, CSV is a text-encoded file with separated values in rows.
Each row represents an entry with the columns as attributes.
Usually, the first row contains a name for each attribute encoded as text.
To allow consistent processing, we expect all string values be escaped in doulbe quotes ("String").
Further, the separation of values should be done with commas, even though other characters are allowed.
Find below a short example CSV to be visualized with the parallel coordinates pipeline:

	"City","Temperature","Rainfall","Month"
	"Sydney",25,0,10
	"Sydney",22,1,09
	"Melbourne",20,2,11
	"Melbourne",19,3,10
	...

The values of "City" come form a fixed set and repeat.
This indicates a good attribute for grouping within the parallel coordinates diagram.

####  Houdini

Houdini supports a range of geometry [formats](http://www.sidefx.com/docs/houdini15.0/io/formats/channel_formats), to import and export models and use the available piplines.
Data other than 3D can be imported to Houdini via channel files.

#####  CHAN

The .chan file format comes from Houdini and allows to import your data and use it in Houdini to create geometry.
The format is similar to CSV, as it also represents data in a text file.
Each row represents data of one frame and attributes are separated by space.
In contrast to CSV, there is no header row and string string values are not supported at all.

[/md]