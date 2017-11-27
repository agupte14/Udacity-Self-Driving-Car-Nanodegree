# **Finding Lane Lines on the Road** 

----
**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report
----

### Reflection

### 1. Description of the Pipeline
The pipeline begins with converting the original (RGB) images to Grayscale and YUV respectively. The Grayscale image is used to extract the white pixels and the Y-channel of the YUV scale is used to extract the yellow pixels. Through trial and error, I found that the Y-channel perfectly singles out the yellow color. The threshold mask of white and yellow pixels is then applied to a copy of the original image such that all points other than the points in the mask are set to zero.
We then apply Gaussian blur and Canny Edge Detection on the above generated images to give us a clear gradient along the edges of the lanes.
We then apply a trapezoidal region of interest mask to single out the points we need. This image is then used to generate a set of points to draw continuous lane lines. These set of points and the region of interest masked images are used to perform Hough transform and draw the appropriate lines.
A weighted function is then to draw these lane lines on the original image, giving us the desired result.


### 2. Shortcomings in the current pipeline
The lane lines tend to flicker as the framerate of the video increases. Also, it doesn't handle lane curvature very well.

### 3. Suggested improvements to the current pipeline
A generic pipeline to work on both straight lanes and curved lanes. Also, a way to normalize the extrapolated points so that the lane flickering reduces to some extent.