# **Finding Lane Lines on the Road** 

## Writeup 

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

My pipeline consisted of 6 steps. 
1. I converted the images to grayscale.
2. smooth the image with GaussianBlur function.
3. pick up the points which is bigger than the high_threshold.
4. define a quadangle to filter useless points.
5. pick up potential lines use hough_lines function.
6. merge the lines to the original image.

In order to draw a single line on the left and right lanes, I modified the parameters of hough_lines():
	
	rho = 1
    theta = np.pi*2/180
    threshold =20
    min_line_length = 1
    max_line_gap =200
	
In order to eliminate the shadow of tree,i modified the parameters of gaussian_blur() function:

	kernel_size = 17
	

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be that when contrast of shadow and beside place is very large,it will pick up some useless lines.

Another shortcoming could be that in the light place,the yellow lines would not be recognized.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to filter the points that is made of the color of the road or shadow.
