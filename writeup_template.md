# **Finding Lane Lines on the Road** 

## Writeup Template
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road


[//]: # (Image References)

[image_gray]: ./test_images_output/grayout_whiteCarLaneSwitch.jpg "Grayscale"
[image_gaussian]: ./test_images_output/gaussianout_whiteCarLaneSwitch.jpg "Gaussian"
[image_canny]: ./test_images_output/cannyout_whiteCarLaneSwitch.jpg "Canny"
[image_regionofinterest]: ./test_images_output/regionofinterestout_whiteCarLaneSwitch.jpg "Region of interest"
[image_hough]: ./test_images_output/houghout_whiteCarLaneSwitch.jpg "Hough transform"
[image_polyfitline]: ./test_images_output/polyfitout_whiteCarLaneSwitch.jpg "Poly fit line"
[image_processed]: ./test_images_output/whiteCarLaneSwitch.jpg "Processed Image"
[image_processed_with_polyfit]: ./test_images_output/polyfitline_whiteCarLaneSwitch.jpg "Processed Image with polyfit"

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
 - I poly fit the lines result from hough transform to draw a full line of the two lanes.
 ![alt text][image_polyfitline]
 - I applied the drawn two lines on the original image.
 ![alt text][image_processed]
 and when drawing the full two lines using poly fitting its output is:
 ![alt text][image_processed_with_polyfit]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the left of the right of the lane line has an obvious edge and it is within the region of interest so it will be mis treated as a lane line.

Another shortcoming could be in the gray areas where the lane color is not obvious so it may fail finding the lane line because the contrast difference is not so high.


### 3. Suggest possible improvements to your pipeline

 - A possible improvement would be to find another color space that represents the lane lines better than RGB.
 - We can also make the region of interest more tigh.
 - We can generalize the idea to find not only straight lines, but also curves, as the lane lines are curves in the real world.

