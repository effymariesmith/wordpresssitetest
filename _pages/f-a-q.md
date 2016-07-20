---
ID: 165
post_title: F.A.Q
author: davm
post_date: 2016-06-23 05:32:47
post_excerpt: ""
layout: page
permalink: http://localhost/wordpress/f-a-q/
published: true
---
[md]

#### What is the Data Arena Virtual Machine?
The Data Arena Virtual Machine is an emulation of the Data Arena software environment. It allows you to
use the same software available at the data arena from your home or office computer, independent of the
operating system that you are running.

#### What do I need to run the Data Arena Virtual Machine?
You will need a computer able to run [VirtualBox](https://www.virtualbox.org){:target="_blank"}, which is available for Windows, OSX and Linux.
Reserve at least 15GB of storage, 4GB of memory and a quad-core CPU.

#### How do I get my data in to the Data Arena Virtual Machine?
There are several ways to import your data:

* You can install [Virtualbox Guest Additions](https://www.virtualbox.org/manual/ch04.html) and create a shared folder.
Then you copy the data in the directory on your computer and can access it in the virtual machine.

* You can directly mount a network device in the virtual machine and transfer the data.

* When you connect the virtual machine to the internet, you can download the data from any webpage.

* Instead of just uploading the final visualization you can commit the only data first and checkout the repository.

#### What is a pipeline?
A pipeline is a semi-automated workflow to build a visualization for a category of data.
There are restrictions for the input data of each pipeline and a defined type of visualization as output.
Some parameters, such as coloring and size of the visualization can be changed.
#### What pipeline should I use?

#### What pipelines are available?
Currently, we provide the piplines in the [Quickstart]({filename}quickstart.md).
#### How can I contribute to the Data Arena Virtual Machine?
The entire software will be available on [GitHub](https://github.com/UTSDataArena) soon.
Make sure you contribute your changes, that

[/md]