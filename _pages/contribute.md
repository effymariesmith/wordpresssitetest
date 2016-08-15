---
ID: 1667
post_title: Contribute
author: davm
post_date: 2016-08-15 07:10:34
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/2userguide/contribute/
published: true
---
<h3>Getting Started</h3>
Contribute to the documentation.

To get set up check out our github page (link) and follow the instructions on installing WordPress on your local computer.

Once you have WordPress installed follow the instructions below to contribute to the documentation.

&nbsp;
<h3>Adding a new page</h3>
Adding a new page to the user guide,

Click here to add a new page <a href="http://localhost/wordpress/wp-admin/post-new.php?post_type=page">click here </a> to the user guide or tutorial sections, this will ask you to log in.
<h4>Logging in</h4>
The login username and password are

Username: Contribute

Password: Contribute
<h4>Edit the page Attribute section</h4>
<img class="alignnone size-medium wp-image-1669" src="http://localhost/wordpress/wp-content/uploads/2016/08/Screen-Shot-2016-08-15-at-4.52.32-PM-259x300.png" alt="Screen Shot 2016-08-15 at 4.52.32 PM" width="259" height="300" /> <img class="alignnone size-medium wp-image-1671" src="http://localhost/wordpress/wp-content/uploads/2016/08/Screen-Shot-2016-08-15-at-4.53.53-PM-257x300.png" alt="Screen Shot 2016-08-15 at 4.53.53 PM" width="257" height="300" /> <img class="alignnone size-medium wp-image-1670" src="http://localhost/wordpress/wp-content/uploads/2016/08/Screen-Shot-2016-08-15-at-4.53.34-PM-258x300.png" alt="Screen Shot 2016-08-15 at 4.53.34 PM" width="258" height="300" />
<h5><strong>Edit the Parent </strong></h5>
Change the Parent to the name of the section you would like to contribute too. For example, if you would like to add a page to the User Guide, change the parent to User Guide. This will make the User Guide section the Parent to your page and ensure it will be adding to the menu inside the page template.
<h5><strong>Edit the Template</strong></h5>
Change the Template to the name of the section you would like to contribute too. For example, if you would like to add a page to the User Guide, change the Template to User Guide. This will make sure you are using the correct page template for the page you wish to add.
<h5><strong>Edit the Order</strong></h5>
Change the order number to change where your page will display within the navigation system. We are currently using increments of 10 for our page numbering system.

The first page to display is set to 1, the next set to 1o, the next 20 and so on. If you want your page to display between page 1 and page 2 set your page number to 5. If you want to add your page to the end of the list, count how many pages are already created, for example, if there are 10 pages already created, then make your page 110.
<h3></h3>
<h3>Creating your own page template for a new tutorial series</h3>
Have you written your own tutorial series or have an idea for a new section on the site. You can create your own page template by following the steps below.

Navigate to the correct folder, /xamppfiles/apps/wordpress/htdocs/wp-content/themes/sydney-child/page-templates

Duplicate page_Your_Tutorial_Name_tutorial_series.php to get you started.

Edit the file name to the name of your tutorial.

<img class="alignnone wp-image-1679 size-full" src="http://localhost/wordpress/wp-content/uploads/2016/08/Screen-Shot-2016-08-15-at-5.26.24-PM.png" alt="Screen Shot 2016-08-15 at 5.26.24 PM" width="724" height="85" />

Then open the file and change Your_Tutorial_Name on line 1 to the name of your tutorial.

<img class="wp-image-1678 size-full alignleft" src="http://localhost/wordpress/wp-content/uploads/2016/08/Screen-Shot-2016-08-15-at-5.26.14-PM.png" alt="Screen Shot 2016-08-15 at 5.26.14 PM" width="706" height="118" />

&nbsp;

&nbsp;

&nbsp;

&nbsp;

Change Your_Tutorial_Name on line 29 to the name of your tutorial.

For more advanced changes have a look at the Wordpress User Guide Template Page.
<h4>Using your new template</h4>
&nbsp;