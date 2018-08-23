# **Finding Lane Lines on the Road** 

## Writeup Template
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image_gray]: ./test_images_output/grayout_whiteCarLaneSwitch.jpg "Grayscale"
[image_gaussian]: ./test_images_output/gaussianout_whiteCarLaneSwitch.jpg "Gaussian"
[image_canny]: ./test_images_output/cannyout_whiteCarLaneSwitch.jpg "Canny"
[image_regionofinterest]: ./test_images_output/regionofinterestout_whiteCarLaneSwitch.jpg "Region of interest"
[image_hough]: ./test_images_output/houghout_whiteCarLaneSwitch.jpg "Hough transform"
[image_polyfitline]: ./test_images_output/polyfitout_whiteCarLaneSwitch.jpg "Poly fit line"
[image_processed]: ./test_images_output/whiteCarLaneSwitch.jpg "Processed Image"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:
 - I converted the images to grayscale.
 ![alt text][image_gray]
 - I blurred the image using 7x7 gaussian filter.
 ![alt text][image_gaussian]
 - I found the edges in the image using canny edge detection that results in a binary image.
 ![alt text][image_canny]
 - I applied the region of interest so that we can only see only the region for the lane lines, not the whole image.
 ![alt text][image_regionofinterest]
 - I applied hough transform to connect the points result from canny detection into lines.
 ![alt text][image_hough]
 - I separated the lines resulting from hough transform into two segments. The first segment is the left lines segment, and the second one is the right lines segment. The segments are separated by the mid x point of the region of interest.
 ![alt text][image_gray]
 - I poly fit the lines result from hough transform to draw a full line of the two lanes.
 ![alt text][image_polyfitline]
 - I applied the drawn two lines on the original image.
 ![alt text][image_processed]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
