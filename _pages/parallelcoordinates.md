---
ID: 12
post_title: Parallel Coordinates
author: effy
post_date: 2016-06-09 05:45:48
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/data-type/speedsheet/parallelcoordinates/
published: true
sq_sidebar_layout:
  - 'a:1:{i:0;s:10:"no_sidebar";}'
---
<ul class="sow-slider-images" data-settings="{&quot;pagination&quot;:true,&quot;speed&quot;:800,&quot;timeout&quot;:8000,&quot;swipe&quot;:true}">		<li class="sow-slider-image" style="">
<img src="http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1.jpg" class="attachment-full size-full" alt="parallelCoordinates02" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1.jpg 2552w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1-300x200.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1-768x512.jpg 768w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1-1024x683.jpg 1024w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1-830x553.jpg 830w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1-230x153.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1-350x233.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1-480x320.jpg 480w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates02-1-272x182.jpg 272w" sizes="(max-width: 2552px) 100vw, 2552px" height="1701" width="2552">				
</li>
<li class="sow-slider-image" style="">
<img src="http://localhost/wordpress/wp-content/uploads/2016/07/controller01.jpg" class="attachment-full size-full" alt="controller01" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/controller01.jpg 2552w, http://localhost/wordpress/wp-content/uploads/2016/07/controller01-300x200.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/controller01-768x512.jpg 768w, http://localhost/wordpress/wp-content/uploads/2016/07/controller01-1024x683.jpg 1024w, http://localhost/wordpress/wp-content/uploads/2016/07/controller01-830x553.jpg 830w, http://localhost/wordpress/wp-content/uploads/2016/07/controller01-230x153.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/controller01-350x233.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/controller01-480x320.jpg 480w, http://localhost/wordpress/wp-content/uploads/2016/07/controller01-272x182.jpg 272w" sizes="(max-width: 2552px) 100vw, 2552px" height="1701" width="2552">				
</li>
<li class="sow-slider-image" style="">
<img src="http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates.jpg" class="attachment-full size-full" alt="parallelCoordinates" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates.jpg 2552w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates-300x200.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates-768x512.jpg 768w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates-1024x683.jpg 1024w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates-830x553.jpg 830w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates-230x153.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates-350x233.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates-480x320.jpg 480w, http://localhost/wordpress/wp-content/uploads/2016/07/parallelCoordinates-272x182.jpg 272w" sizes="(max-width: 2552px) 100vw, 2552px" height="1701" width="2552">				
</li>
</ul>				<ol class="sow-slider-pagination">
<li><a href="#" data-goto="0">1</a></li>
<li><a href="#" data-goto="1">2</a></li>
<li><a href="#" data-goto="2">3</a></li>
</ol>
<a href="#" data-goto="next" data-action="next">
<em class="sow-sld-icon-thin-right"></em>
</a>
<a href="#" data-goto="previous" data-action="prev">
<em class="sow-sld-icon-thin-left"></em>
</a>
<h4><a href="http://localhost/wordpress/parallelcoordinates/"><strong>Parallel Coordinates </strong></a>Example</h4>
<p> </p>
<h6>
<p>
Parallel Coordinates is a powerful tool to map multiple variables. It assist you to drill down into your data set,
notice relationships within your data and gain new insight from your data.
</p>
<p> 
You can reorder columns, create constraints, interact with the constraints you have created.</p></h6>
<p></p>
<p> </p>
<p> </p>
<p> </p>
<h4>Run Parallel Coordinates<a href=""><strong> Demo</strong></a></h4>
<h2 style="text-align: left;">Use this example</h2>
<h3>1 </h3><h8> Export your spreadsheet as CSV, include the column header and remove non numeric values. Data values can be numeric or categorical, then
copy your .CSV file onto the DAVM(Data Arena Virtual Machine). (Ref LINK) </h8>
<h3>2</h3> Using Dolphin or Konsole navigate too Root/local/examples/parallel and copy your .CSV file to this folder.
<h3>3</h3> If you are using Dolphin right click in this folder and click on 'Open Terminal Here'. In Terminal run the python script that will load your data into parallel coordinates.
<pre><code> python build.py</code>
</pre>
After you run this script, it will print
<pre><code>Usage: build.py &lt;csv file&gt; &lt;group Column name&gt;
Example: build.py Public.csv 'Institution'</code></pre>
<h3>5</h3>
<p>Enter this line of code into Konsole and press enter.</p>
<pre><code> ./build.py ../your_file_name.csv  'your group column name'  'remove column' </code> </pre>
<p>Change your_file_name.csv to the name of your file. </p>
<p>Change 'your group column name' to the column you would like to add colour to.<br>
Make sure the formatting is the same as in your CSV file.</p>
<p>To remove a column change ' remove column' to the name of the column in your CSV file you would like to remove. Make sure the formatting is the same.</p>
<p>This script will create a folder in this Directory with your_file_name inside this folder will be two more folders, files and index.html</p>
<h3>6</h3>
<p>  Open index.html with Firefox. Or copy this path into the firefox URL Bar file:///local/examples/parallel/your_file_name/index.html</p>
<h3 style="text-align: center;">More Info</h3>
<h6 style="text-align: center;">./build.py</h6>
<p style="text-align: center;"><strong>'./'</strong> Your current directory</p>
<p style="text-align: center;"><strong>'build.py'</strong> Runs the python script that will import your data into parallel coordinates</p>
<h6 style="text-align: center;">../your_file_name.csv</h6>
<p style="text-align: center;">Is the path to your file.</p>
<p style="text-align: center;"><strong>'../'</strong> Your current location/path</p>
<p style="text-align: center;"><strong>your_file_name.csv</strong> Your file</p>
<p style="text-align: center;">&nbsp;</p>
<h6 style="text-align: center;">your group column name</h6>
<p style="text-align: center;">Specifies what column will be coloured in the diagram.&nbsp;</p>
<h6 style="text-align: center;">remove column</h6>
<p style="text-align: center;">This is used for cleaning up your visualisation. 'remove column' can remove any column in your .CSV file</p>
<h3 style="text-align: center;">Explore More Examples</h3>
<a href="http://localhost/wordpress/data-type/point-cloud/wombeyan-caves/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/cave02-300x248.jpg" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/cave02-300x248.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/cave02-230x190.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/cave02-350x289.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/cave02.jpg 400w" title="Caves" class="so-widget-image" height="248" width="300">
</a>
<a href="http://localhost/wordpress/data-type/geometry/fashion-turntable/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-300x248.jpg" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-300x248.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-230x190.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-350x289.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02.jpg 400w" title="Fashion Turntable" class="so-widget-image" height="248" width="300">
</a>
<a href="http://localhost/wordpress/data-type/point-cloud/water-pipe/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/pipe1-300x248.jpg" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/pipe1-300x248.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/pipe1-230x190.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/pipe1-350x289.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/pipe1.jpg 400w" title="Water Pipe" class="so-widget-image" height="248" width="300">
</a>