---
ID: 1313
post_title: Overview
author: davm
post_date: 2016-08-08 07:47:32
post_excerpt: ""
layout: page
permalink: >
  http://localhost/wordpress/2userguide/overview/
published: true
---
[md]
This guide will walk you through the Data Arena Virtual Machine.
After that, you can start prototyping your visualization.

## What is the Data Arena Virtual Machine?
The Data Arena Virtual Machine is an emulation of the Data Arena software environment. It allows you to
use the same software available at the data arena from your home or office computer, independent of the
operating system that you are running.

## What do I need to run the Data Arena Virtual Machine?
You will need a computer able to run [VirtualBox](https://www.virtualbox.org){:target="_blank"}, which is available for Windows, OSX and Linux.
Reserve at least 15GB of storage, 4GB of memory and a quad-core CPU.

## What is in the Data Arena Virtual Machine?
The virtual machine runs the [Gentoo Linux](https://www.gentoo.org/){:target="_blank"} operating system.
On top of that, we run the [software environment]({filename}software.md) of the Data Arena.
It also includes [example visualizations](http://127.0.0.1:8002), to get an impression of the capabilities.
To easily get started, we provide different visualization [pipelines]({filename}pipelines.md) for different kinds of data.

## What is the workflow?
1. Get the lates .ova image
2. Import it to [Virtualbox](https://www.virtualbox.org/)
3. Start the virtual machine
4. A browser with the Data Arena documentation will open. If it is not open, open firefox and type http://127.0.0.1:8000 into the address bar.
5. Select a [pipeline]({filename}quickstart.md) that suits your data
6. Transform your data to the pipeline input requirements
7. View your visualization in the virtual machine
8. Tune the parameters
9. Upload your visualization TODO 
10. Come to the Data Arena and we start your visualization as you prototyped it

## How do I get my data into the Data Arena Virtual Machine?
There are several ways to import your data:

* You can install [Virtualbox Guest Additions](https://www.virtualbox.org/manual/ch04.html) and create a shared folder.
  Then you copy the data into the directory on your computer and can access it in the virtual machine.

* You can directly mount a network device in the virtual machine and transfer the data.

* When you connect the virtual machine to the internet, you can download the data from any web page. 

* Instead of just uploading the final visualization you can commit the only data first and checkout the repository.

## How can I contribute to the Data Arena Virtual Machine?
The entire software will be available on [GitHub](https://github.com/UTSDataArena)  soon.
Make sure you contribute your changes, that we can create new pipelines and make data visualization easier.

[/md]