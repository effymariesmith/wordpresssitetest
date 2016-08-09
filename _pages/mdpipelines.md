---
ID: 1397
post_title: mdpipelines
author: davm
post_date: 2016-08-09 07:00:02
post_excerpt: ""
layout: page
permalink: http://localhost/wordpress/mdpipelines/
published: true
---
[md]
This page gives an idea of the Data Arena pipelines and how we use them to easily create data visualizations.

## What is a pipeline?
A pipeline is a semi-automated workflow to build a visualization for a category of data.
There are restrictions for the input data of each pipeline and a defined type of visualization as output.
Some parameters, such as coloring and size of the visualization can be changed.

## What pipelines are available?
Currently, we provide the piplines in the [Quickstart]({filename}quickstart.md).

## How do I use a pipeline?
If your data is compliant with one of the pipelines, you can use one of the examples in `/local/examples`.
Copy the `LoadX.py` and adjust the parameters and start the visualization with `orun LoadYOURDATA.py`.


## How can I share my pipeline changes?
In order to create more pipelines for different data or visualizations, we encourage you to contribute your results to our public [repository](https://github.com/UTSDataArena).


## Example of a pipeline

Parrallel Coordinates is one of the pipelines we use at the Data Arena. [Example of Parrallel Coordinates](http://127.0.0.1:8002).

To load your data into Parrallel Coordinates or another pipeline, take a look at the information in our [Quickstart guide,]({filename}quickstart.md)

[/md]