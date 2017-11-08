# **Finding Lane Lines on the Road** 

##Eric Cheng's Writeup 

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

My pipeline consisted of 5 steps. 
1. I converted the images to grayscale using "cv2.cvtColor". 
2. Apply Gaussian smooth using "cv2.GaussianBlur"
3. Apply Cannyedge using "cv2.Canny"
4. Apply hough tranform to draw lines on ablank image using"cv2.HoughLinesP" and "cv2.line"
5. Define a trapesoide mask and draw it on the original images and adjust the mask. "cv2.polylines"
6. Keep area of interest and black out others. "cv2.fillPoly" and "cv2.bitwise_and"
7. The lines of interest is left on a blank image. I did not know how to obtain these lines of interest with other methord. So I did a second Hough transform to obtain them as a list of end points.
8. Then use these end points to average/extrapolate left lane and right lane. Slopes and Y axis intercepts were calculated using the end points. Highest Y position (smallest y value) was identified. Lowest Y position("img.shape[0]") is the bottom of the image. A line is defined by y=ax+b. With a,b, and highest and lowest Y position, two end points of a lane line are able to get.
9. Draw transparent lane lines on the original images using "cv2.addWeighted"
10. save output images using "mpimg.imsave". Had to slice the image name during this step.
11. Using given code to apply my image process pipline onto the videos. 



![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
