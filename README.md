# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="test_images_output/myWhiteCarLaneSwitchOutput.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.

In this project we will detect lane lines in images using Python and OpenCV.   

---

### The following techniques are used in the project.

### Grayscaling

This is an important first step in differentiating the lane lines from other objects on the road. I first converted the image to grayscale using "cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)". An example is below:

<img src="test_images_output/myWhiteCarLaneSwitchgrayImageOutput.jpg" width="480" alt="Combined Image" />

### Gaussian Smoothing (Gaussian Blur)

The above grayscale images have many rough edges which causes numerous noisy edges to be detected. I used "cv2.GaussianBlur" to smooth out edges.

<img src="test_images_output/myWhiteCarLaneSwitchBlurGrayOutput.jpg" width="480" alt="Combined Image" />

### Canny Edge Detection

Now I applied the Canny transform on the grayscale image with gaussian smoothing. We apply this transform in order to obtain the sharp edges of different objects in the image. 

<img src="test_images_output/myWhiteCarLaneSwitchCannyImageOutput.jpg" width="480" alt="Combined Image" />

### Region of Interest Selection

We need to isolate the edges for the left and right lanes from other objects in the image. In order to do this, we use "cv2.fillPoly" along with "cv2.bitwise_and" to isolate the portion of the image which is of interest to us. 

<img src="test_images_output/myWhiteCarLaneSwitchmaskedImageOutput.jpg" width="480" alt="Combined Image" />

### Hough Transform Line Detection

I used Hough transform on the lane edge images to detect the lane lines.

<img src="test_images_output/myWhiteCarLaneSwitchHoughLinesImageOutput.jpg" width="480" alt="Combined Image" />

### Extrapolating Lane Lines

In the previous image, we see that multiple lines are detected. In order to draw a single line on the left and right lanes, we need to average and extrapolate over the detected line segments. We seperate line segments by their slope ((y2-y1)/(x2-x1)) to decide which segments are part of the left line vs. the right line and take the averages.

<img src="test_images_output/myWhiteCarLaneSwitchOutput.jpg" width="480" alt="Combined Image" />

### Video Clips

The resultant video clips can be found in [SDCND-finding-lane-lines/test_videos_output/] folder.


### Conclusion

A possible improvement would be to ...

Another potential improvement could be to ...
