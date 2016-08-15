---
ID: 1539
post_title: User Guide
author: davm
post_date: 2016-08-12 04:00:51
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/2userguide/user-guide/
published: true
---
<?php // this will display the post tree so acts as our navigation
                
          
                if(!$post->post_parent){
                        $children = wp_list_pages("title_li=&child_of=".$post->ID."&echo=");
                }else{
 
                        if($post->ancestors)
                        {
                                $ancestors = end($post->ancestors);
                                $children = wp_list_pages("title_li=&child_of=".$ancestors."&echo=0&depth=3");
                        }
                }
 
                if ($children) { ?>
                   <h7> <ol> 
                                <?php echo $children; ?>
                      
                  </h7> </ol>
                    
                <?php }  ?>