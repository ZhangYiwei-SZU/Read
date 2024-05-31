# Object Detection and Bounding Boxes
:label:`sec_bbox`
In earlier sections (e.g., :numref:`sec_alexnet`--:numref:`sec_googlenet`),
we introduced various models for image classification.
In image classification tasks,
we assume that there is only *one*
major object
in the image and we only focus on how to 
recognize its category.
However, there are often *multiple* objects
in the image of interest.
We not only want to know their categories, but also their specific positions in the image.
In computer vision, we refer to such tasks as *object detection* (or *object recognition*).
Object detection has been
widely applied in many fields.
For example, self-driving needs to plan 
traveling routes
by detecting the positions
of vehicles, pedestrians, roads, and obstacles in the captured video images.
Besides,
robots may use this technique
to detect and localize objects of interest
throughout its navigation of an environment.
Moreover,
security systems
may need to detect abnormal objects, such as intruders or bombs.
In the next few sections, we will introduce 
several deep learning methods for object detection.
We will begin with an introduction
to *positions* (or *locations*) of objects.
```{.python .input}
#@tab pytorch
%matplotlib inline
from d2l import torch as d2l
import torch
```
We will load the sample image to be used in this section. We can see that there is a dog on the left side of the image and a cat on the right.
They are the two major objects in this image.
## Bounding Boxes
In object detection,
we usually use a *bounding box* to describe the spatial location of an object.
The bounding box is rectangular, which is determined by the $x$ and $y$ coordinates of the upper-left corner of the rectangle and the such coordinates of the lower-right corner. 
Another commonly used bounding box representation is the $(x, y)$-axis
coordinates of the bounding box center, and the width and height of the box.
Here we define functions to convert between these two
representations: 
`box_corner_to_center` converts from the two-corner
representation to the center-width-height presentation,
and `box_center_to_corner` vice versa.
The input argument `boxes` can be either a tensor of length 4,
or a two-dimensional tensor of shape ($n$, 4), where $n$ is the number of bounding boxes.
We will define the bounding boxes of the dog and the cat in the image based
on the coordinate information.
The origin of the coordinates in the image
is the upper-left corner of the image, and to the right and down are the
positive directions of the $x$ and $y$ axes, respectively.
We can verify the correctness of the two
bounding box conversion functions by converting twice.
Let us draw the bounding boxes in the image to check if they are accurate.
Before drawing, we will define a helper function `bbox_to_rect`. It represents the bounding box in the bounding box format of the  `matplotlib` package.
After adding the bounding boxes on the image,
we can see that the main outline of the two objects are basically inside the two boxes.
## Summary
* Object detection not only recognizes all the objects of interest in the image, but also their positions. The position is generally represented by a rectangular bounding box.
* We can convert between two commonly used bounding box representations.
## Exercises
1. Find another image and try to label a bounding box that contains the object. Compare labeling bounding boxes and categories: which usually takes longer?
1. Why is the innermost dimension of the input argument `boxes` of `box_corner_to_center` and `box_center_to_corner` always 4?
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/369)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/1527)
:end_tab: