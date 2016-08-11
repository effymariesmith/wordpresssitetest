---
ID: 1479
post_title: Custompaget2
author: davm
post_date: 2016-08-11 02:03:06
post_excerpt: ""
layout: page
permalink: http://localhost/wordpress/custompaget2/
published: true
---
<!--?php $mypages = get_pages( array( 'child_of' =&gt; $post-&gt;ID, 'sort_column' =&gt; 'post_date', 'sort_order' =&gt; 'desc' ) );&lt;/p&gt; &lt;p&gt; foreach( $mypages as $page ) {&lt;br ?--> $content = $page-&gt;post_content;
if ( ! $content ) // Check for empty page
continue;

$content = apply_filters( 'the_content', $content );
?&gt;
<h2></h2>
<div class="entry"></div>
&nbsp;