# **Finding Lane Lines on the Road** 

## First SDNCD assignment

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "Input image"

[image2]: ./test_images_output/solidWhiteCurve.jpg "Output image"

---

### Reflection

The pipeline performs the following steps in the given order.

1) Read images from a given directory. For each image read, performs the below steps.
2) Identifies and retains only white and yellow pixels.
3) Converts the image to grayscale.
4) Performs Gaussian blur (kernel size 5).
5) Runs Canny edge detection.
6) Masks a selective region (calculated as a preset % of image. tuned to example dataset).
7) Calculates houghlines and extrapolates the lines to cover the selected region in step 6.

### draw_lines() code

This is the function which had changes not covered in the course material. Given a list of lines output from HoughLinesP, I calculated the slope of each line and separated them into two lists of left_lines and right_lines. I then calculated the average of points in these lists and then used polyfit function to determine the ideal line equation. Using the slope, intercept from polyfit, I calculated the points to be extrapolated in region of interest.

!["input image goes here"][image1]
!["output image goes here"][image2]

### 2. Identify potential shortcomings with your current pipeline

1) Lack of error checks. This poses the biggest risk.
2) The pipeline is tuned to the given dataset. Haven't performed tests outside the dataset.
3) The input pics portray good weather. No idea how the pipeline performs on poor weather conditions dataset.

### 3. Suggest possible improvements to your pipeline

1) Testing the pipeline on challenge video shows glitches. Need to handle edge cases.
2) Add feedback from one frame to another so the line follows intended path.
