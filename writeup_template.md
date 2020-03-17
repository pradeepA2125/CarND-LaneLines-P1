# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

The pipeline consists of all the requiremnets specified in the ruberic.

you can see the total pipeline on executed cell IN 71..

the steps it takes are as follows:

1. Convert to HLS color space so that both white and yellow colors can be extracted accordingly using functions like cv2.inrange and bitwise or.

2. Later Gaussian filter has been used to smoothen the image and remove sharp unnecessary edges.

3. required region of interest has been extracted using the vertices defined which are sent through function call and the by the use of cv2.bitwise_and function .

4.Firstly we detect the lines using houghline which is a straight fowrward function. In the later part for drawing the lines, finding slope slope m = ((y2-y1)/(x2-x1)) helps in determing which line is it(left or right). From the slope we determine the intercept (#y = mx + b, b = y - mx). Now since we have both slope and intercept we will find x values for both top and bottom of line (# y = Ax + b, therefore x = (y - b) / A). These values are accumulated in the list left/right_lane accordingly. The mean of these points which represents the top and bottom of both lines are used to draw lines accordingly.

5.as a last step, with the help of weighted_img helper function, we impose the region of interest image on original image to get a annoated image.

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the curvy road comes ahead late detection goes wrong

Another shortcoming could be that the shadows can still mess with detection.




### 3. Suggest possible improvements to your pipeline

improvements which can be done are simply achieved by making the detection robust to above named shortcomings. detecting the curvature. or directly use deep learning (image segmentaion) to annotate the road.
