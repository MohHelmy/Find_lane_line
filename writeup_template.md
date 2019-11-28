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

The pipeline consists of the following steps

Color Selection (Yellow and white lanes)
Convert image to grayscale
Canny Edge Detection
Region of Interest Selection
Hough Transform Line Detection 

The above mentioned pipeline is used to process the video , the video is being looked at at single image where each image goes throught he pipe line.

Below a detailed description of each step of the pipe line:

1.Color selection:
We first run color selection on the input frame to select only the yellow and white shades of color and mask all other colors. To do this, we convert the input image to HSV (hue, saturation, value) color space. This makes it easier to select required colors using OpenCV's in Range function.

image  needed

[//]: # (Image References)

[image1]: ./images/image of interest.png "whiteCarLaneSwitch"

2.Convert image to grayscale:
Then we transform the color selected frame to a grayscale frame to obtian better results for canny edge To normalize any noise and sharpness, we perform a Gaussian blur on the grayscale image

[//]: # (Image References)

[image1]: ./images/gray scal.png "whiteCarLaneSwitch"

3.Canny Edge Detection:
Then we run the Canny Edge Detection algorithm to detect edges in the frames

[//]: # (Image References)

[image1]: ./images/Canny.png "whiteCarLaneSwitch"

4.Gaussian blur:
To make the edges more smoother.

[//]: # (Image References)

[image1]: ./images/Gauss.png "whiteCarLaneSwitch"

5.Region of Interest Selection:
We apply a Region of Interest mask which is a fixed polygon area to only retain the road lanes.

[//]: # (Image References)

[image1]: ./images/image of interest.png "whiteCarLaneSwitch"


6.Hough Transform Line Detection:
Using probabilistic Hough transform we find line segments in the frame. Then, using draw_lines() function we draw the lines which represnts the road lanes.

[//]: # (Image References)

[image1]: ./images/drawing lines.png "whiteCarLaneSwitch"


The function draw_lines() follows the below the steps to obtain/Draw the correct lines:
takes all the lines found by the Hough transform.
filtering the lines and ignore verical lines , we conside them as noise.


7.Merging Images:
now we merge our images, to obtain the final result

[//]: # (Image References)

[image1]: ./images/final image.png "whiteCarLaneSwitch"

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


The pipeline relies on a restricted region of interest based on several iteration.

I belive the algorithm won't work as expected if the road was going up or down , as we have a constant region of interest.

I have constant limits for color detections , i think the pipeline will perfom badly on darker , foggy road , sharp turns , tunnels or under bridges


### 3. Suggest possible improvements to your pipeline

Dynamic selection of the region of interest as it shall be based of road curvature.
Identify a better method to detect curves.
Identify better method to detect colors in differnt enviroment ,this should be dynamic.
