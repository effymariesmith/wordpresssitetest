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
panels_data:
  - |
    a:3:{s:7:"widgets";a:13:{i:0;a:4:{s:6:"frames";a:3:{i:0;a:9:{s:16:"background_image";i:0;s:25:"background_image_fallback";s:0:"";s:16:"background_color";b:0;s:21:"background_image_type";s:5:"cover";s:16:"foreground_image";i:725;s:25:"foreground_image_fallback";s:0:"";s:3:"url";s:0:"";s:17:"background_videos";a:0:{}s:10:"new_window";b:0;}i:1;a:9:{s:16:"background_image";i:0;s:25:"background_image_fallback";s:0:"";s:16:"background_color";b:0;s:21:"background_image_type";s:5:"cover";s:16:"foreground_image";i:717;s:25:"foreground_image_fallback";s:0:"";s:3:"url";s:0:"";s:17:"background_videos";a:0:{}s:10:"new_window";b:0;}i:2;a:9:{s:16:"background_image";i:0;s:25:"background_image_fallback";s:0:"";s:16:"background_color";b:0;s:21:"background_image_type";s:5:"cover";s:16:"foreground_image";i:724;s:25:"foreground_image_fallback";s:0:"";s:3:"url";s:0:"";s:17:"background_videos";a:0:{}s:10:"new_window";b:0;}}s:8:"controls";a:7:{s:5:"speed";i:800;s:7:"timeout";i:8000;s:13:"nav_color_hex";s:7:"#FFFFFF";s:9:"nav_style";s:4:"thin";s:8:"nav_size";i:25;s:5:"swipe";b:1;s:24:"so_field_container_state";s:4:"open";}s:12:"_sow_form_id";s:13:"5785be02d5332";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Slider_Widget";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:0;s:2:"id";i:0;s:9:"widget_id";s:36:"8b69698b-f74e-47d2-8d35-72f268418a3e";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:1;a:4:{s:5:"title";s:0:"";s:4:"text";s:536:"<h4><a href="http://localhost/wordpress/parallelcoordinates/"><strong>Parallel Coordinates </strong></a>Example</h4>
    <p> </p>
    <h6>
    <p>
    Parallel Coordinates is a powerful tool to map multiple variables. It assist you to drill down into your data set,
    notice relationships within your data and gain new insight from your data.
    </p>
    <p> 
    You can reorder columns, create constraints, interact with the constraints you have created.</h6>
    </p>
    <p> </p>
    <p> </p>
    <p> </p>
     <h4>Run Parallel Coordinates<a href=""><strong> Demo</strong></a></h4>";s:6:"filter";b:0;s:11:"panels_info";a:7:{s:5:"class";s:14:"WP_Widget_Text";s:3:"raw";b:0;s:4:"grid";i:0;s:4:"cell";i:1;s:2:"id";i:1;s:9:"widget_id";s:36:"fa9f1c94-74c1-4106-a290-9bcb34cde362";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:2;a:6:{s:5:"title";s:0:"";s:4:"text";s:51:"<h2 style="text-align: left;">Use this example</h2>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578333ef770d6";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:1;s:4:"cell";i:0;s:2:"id";i:2;s:9:"widget_id";s:36:"1ea35202-0ffb-4952-88db-1380842ca3f4";s:5:"style";a:2:{s:7:"padding";s:3:"5px";s:18:"background_display";s:4:"tile";}}}i:3;a:4:{s:5:"title";s:0:"";s:4:"text";s:799:"<h3>1 </h3><h8> Export your spreadsheet as CSV, include the column header and remove non numeric values. Data values can be numeric or categorical, then
     copy your .CSV file onto the DAVM(Data Arena Virtual Machine). (Ref LINK) </h8>
    
    <h3>2</h3> Using Dolphin or Konsole navigate too Root/local/examples/parallel and copy your .CSV file to this folder.
     
    <h3>3</h3> If you are using Dolphin right click in this folder and click on 'Open Terminal Here'. In Terminal run the python script that will load your data into parallel coordinates.
    <div class="highlight">
    <pre><code> python build.py</code>
    </pre>
    </div>
    After you run this script, it will print
    <div>
    <pre><code>Usage: build.py &lt;csv file&gt; &lt;group Column name&gt;
    Example: build.py Public.csv 'Institution'</code></pre>
    </pre>
    </div>
    ";s:6:"filter";b:0;s:11:"panels_info";a:7:{s:5:"class";s:14:"WP_Widget_Text";s:3:"raw";b:0;s:4:"grid";i:2;s:4:"cell";i:0;s:2:"id";i:3;s:9:"widget_id";s:36:"54851dee-99e3-4a0e-adda-373a231fe652";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:4;a:4:{s:5:"title";s:0:"";s:4:"text";s:801:"<h3>5</h3>  
    
    Enter this line of code into Konsole and press enter.
    
    <pre><code> ./build.py ../your_file_name.csv  'your group column name'  'remove column' </code> </pre>
    
    Change your_file_name.csv to the name of your file. 
    
    Change 'your group column name' to the column you would like to add colour to.
    Make sure the formatting is the same as in your CSV file.
    
    To remove a column change ' remove column' to the name of the column in your CSV file you would like to remove. Make sure the formatting is the same.
    
    This script will create a folder in this Directory with your_file_name inside this folder will be two more folders, files and index.html
    
    <h3>6</h3>  Open index.html with Firefox. Or copy this path into the firefox URL Bar file:///local/examples/parallel/your_file_name/index.html
    
    
    
    
    ";s:6:"filter";b:1;s:11:"panels_info";a:7:{s:5:"class";s:14:"WP_Widget_Text";s:3:"raw";b:0;s:4:"grid";i:2;s:4:"cell";i:1;s:2:"id";i:4;s:9:"widget_id";s:36:"7107df68-9d33-4eb6-9aa3-46f20a2e72c7";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:5;a:6:{s:5:"title";s:0:"";s:4:"text";s:46:"<h3 style="text-align: center;">More Info</h3>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"5783373b80d08";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:3;s:4:"cell";i:0;s:2:"id";i:5;s:9:"widget_id";s:36:"1ea35202-0ffb-4952-88db-1380842ca3f4";s:5:"style";a:2:{s:7:"padding";s:4:"20px";s:18:"background_display";s:4:"tile";}}}i:6;a:6:{s:5:"title";s:0:"";s:4:"text";s:264:"<h6 style="text-align: center;">./build.py</h6><p style="text-align: center;"><strong>'./'</strong> Your current directory</p><p style="text-align: center;"><strong>'build.py'</strong> Runs the python script that will import your data into parallel coordinates</p>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"5783316b5f235";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:4;s:4:"cell";i:0;s:2:"id";i:6;s:9:"widget_id";s:36:"8afd5cda-189c-4f4b-ae2e-cf11e2f8723e";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:7;a:6:{s:5:"title";s:0:"";s:4:"text";s:319:"<h6 style="text-align: center;">../your_file_name.csv</h6><p style="text-align: center;">Is the path to your file.</p><p style="text-align: center;"><strong>'../'</strong> Your current location/path</p><p style="text-align: center;"><strong>your_file_name.csv</strong> Your file</p><p style="text-align: center;"> </p>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578331a31995a";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:4;s:4:"cell";i:1;s:2:"id";i:7;s:9:"widget_id";s:36:"8afd5cda-189c-4f4b-ae2e-cf11e2f8723e";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:8;a:6:{s:5:"title";s:0:"";s:4:"text";s:150:"<h6 style="text-align: center;">your group column name</h6><p style="text-align: center;">Specifies what column will be coloured in the diagram. </p>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578331a5c8445";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:4;s:4:"cell";i:2;s:2:"id";i:8;s:9:"widget_id";s:36:"8afd5cda-189c-4f4b-ae2e-cf11e2f8723e";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:9;a:6:{s:5:"title";s:0:"";s:4:"text";s:189:"<h6 style="text-align: center;">remove column</h6><p style="text-align: center;">This is used for cleaning up your visualisation. 'remove column' can remove any column in your .CSV file</p>";s:20:"text_selected_editor";s:4:"tmce";s:5:"autop";b:1;s:12:"_sow_form_id";s:13:"578331a83cc6a";s:11:"panels_info";a:7:{s:5:"class";s:31:"SiteOrigin_Widget_Editor_Widget";s:3:"raw";b:0;s:4:"grid";i:4;s:4:"cell";i:3;s:2:"id";i:9;s:9:"widget_id";s:36:"8afd5cda-189c-4f4b-ae2e-cf11e2f8723e";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:10;a:13:{s:5:"image";i:689;s:14:"image_fallback";s:0:"";s:4:"size";s:6:"medium";s:5:"align";s:7:"default";s:5:"title";s:5:"Caves";s:14:"title_position";s:5:"below";s:3:"alt";s:0:"";s:3:"url";s:64:"http://localhost/wordpress/data-type/point-cloud/wombeyan-caves/";s:5:"bound";b:1;s:12:"_sow_form_id";s:13:"576b6f04ed198";s:10:"new_window";b:0;s:10:"full_width";b:0;s:11:"panels_info";a:7:{s:5:"class";s:30:"SiteOrigin_Widget_Image_Widget";s:3:"raw";b:0;s:4:"grid";i:5;s:4:"cell";i:0;s:2:"id";i:10;s:9:"widget_id";s:36:"7ff25a31-f542-4a04-a44f-2c8cea53f183";s:5:"style";a:1:{s:18:"background_display";s:4:"tile";}}}i:11;a:13:{s:5:"image";i:693;s:14:"image_fallback";s:0:"";s:4:"size";s:6:"medium";s:5:"align";s:7:"default";s:5:"title";s:17:"Fashion Turntable";s:14:"title_position";s:6:"hidden";s:3:"alt";s:0:"";s:3:"url";s:64:"http://localhost/wordpress/data-type/geometry/fashion-turntable/";s:5:"bound";b:1;s:12:"_sow_form_id";s:13:"576b6f262e8f8";s:11:"panels_info";a:6:{s:5:"class";s:30:"SiteOrigin_Widget_Image_Widget";s:4:"grid";i:5;s:4:"cell";i:1;s:2:"id";i:11;s:9:"widget_id";s:36:"7ff25a31-f542-4a04-a44f-2c8cea53f183";s:5:"style";a:2:{s:27:"background_image_attachment";b:0;s:18:"background_display";s:4:"tile";}}s:10:"new_window";b:0;s:10:"full_width";b:0;}i:12;a:13:{s:5:"image";i:841;s:14:"image_fallback";s:0:"";s:4:"size";s:6:"medium";s:5:"align";s:7:"default";s:5:"title";s:10:"Water Pipe";s:14:"title_position";s:6:"hidden";s:3:"alt";s:0:"";s:3:"url";s:60:"http://localhost/wordpress/data-type/point-cloud/water-pipe/";s:5:"bound";b:1;s:12:"_sow_form_id";s:13:"576b6f29382de";s:11:"panels_info";a:6:{s:5:"class";s:30:"SiteOrigin_Widget_Image_Widget";s:4:"grid";i:5;s:4:"cell";i:2;s:2:"id";i:12;s:9:"widget_id";s:36:"7ff25a31-f542-4a04-a44f-2c8cea53f183";s:5:"style";a:2:{s:27:"background_image_attachment";b:0;s:18:"background_display";s:4:"tile";}}s:10:"new_window";b:0;s:10:"full_width";b:0;}}s:5:"grids";a:6:{i:0;a:2:{s:5:"cells";i:2;s:5:"style";a:3:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:1;a:2:{s:5:"cells";i:1;s:5:"style";a:3:{s:7:"padding";s:4:"10px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:2;a:2:{s:5:"cells";i:2;s:5:"style";a:3:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:3;a:2:{s:5:"cells";i:1;s:5:"style";a:3:{s:7:"padding";s:4:"10px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:4;a:2:{s:5:"cells";i:4;s:5:"style";a:3:{s:7:"padding";s:3:"0px";s:5:"align";s:0:"";s:14:"column_padding";s:0:"";}}i:5;a:2:{s:5:"cells";i:3;s:5:"style";a:4:{s:7:"padding";s:4:"20px";s:5:"align";s:0:"";s:11:"row_stretch";s:4:"full";s:14:"column_padding";s:0:"";}}}s:10:"grid_cells";a:13:{i:0;a:2:{s:4:"grid";i:0;s:6:"weight";d:0.5;}i:1;a:2:{s:4:"grid";i:0;s:6:"weight";d:0.5;}i:2;a:2:{s:4:"grid";i:1;s:6:"weight";i:1;}i:3;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.5;}i:4;a:2:{s:4:"grid";i:2;s:6:"weight";d:0.5;}i:5;a:2:{s:4:"grid";i:3;s:6:"weight";i:1;}i:6;a:2:{s:4:"grid";i:4;s:6:"weight";d:0.25;}i:7;a:2:{s:4:"grid";i:4;s:6:"weight";d:0.25;}i:8;a:2:{s:4:"grid";i:4;s:6:"weight";d:0.25;}i:9;a:2:{s:4:"grid";i:4;s:6:"weight";d:0.25;}i:10;a:2:{s:4:"grid";i:5;s:6:"weight";d:0.333333333333333314829616256247390992939472198486328125;}i:11;a:2:{s:4:"grid";i:5;s:6:"weight";d:0.333333333333333314829616256247390992939472198486328125;}i:12;a:2:{s:4:"grid";i:5;s:6:"weight";d:0.333333333333333314829616256247390992939472198486328125;}}}
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
<a href="http://localhost/wordpress/data-type/point-cloud/wombeyan-caves/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/cave02-300x248.jpg" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/cave02-300x248.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/cave02-230x190.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/cave02-350x289.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/cave02.jpg 400w" title="Caves" class="so-widget-image" height="248" width="300">
</a>
<h3 class="widget-title">Caves</h3>
<a href="http://localhost/wordpress/data-type/geometry/fashion-turntable/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-300x248.jpg" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-300x248.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-230x190.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02-350x289.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/fashionTurntable02.jpg 400w" title="Fashion Turntable" class="so-widget-image" height="248" width="300">
</a>
<a href="http://localhost/wordpress/data-type/point-cloud/water-pipe/">	<img src="http://localhost/wordpress/wp-content/uploads/2016/07/pipe1-300x248.jpg" srcset="http://localhost/wordpress/wp-content/uploads/2016/07/pipe1-300x248.jpg 300w, http://localhost/wordpress/wp-content/uploads/2016/07/pipe1-230x190.jpg 230w, http://localhost/wordpress/wp-content/uploads/2016/07/pipe1-350x289.jpg 350w, http://localhost/wordpress/wp-content/uploads/2016/07/pipe1.jpg 400w" title="Water Pipe" class="so-widget-image" height="248" width="300">
</a>