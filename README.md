#**Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

This is first project for the Self-Driving Car Nanodegree (SDCND), finding lanes on several roads in images and videos.


Lane Finding Pipeline
---

To identify and indicate the relevant lines I used the following pipeline.
<img src="test_images_output/initial.png" width="480" alt="Combined Image" />

1. Convert the image to greyscale. First I used the provided function averaging over the 3 channels RGB. Due to the reason, that the yellow lines weren't correctly detected (especially in challenge) I switched to just use the red channel.

<img src="test_images_output/gray.png" width="480" alt="Combined Image" />

2. Apply a Gaussian blur to smoothen the picture.

<img src="test_images_output/blur.png" width="480" alt="Combined Image" />

3. Apply Canny edges to detect edges in the picture.

<img src="test_images_output/canny.png" width="480" alt="Combined Image" />

4. Apply a mask over the designated area of lines in front of the vehicle.

<img src="test_images_output/mask.png" width="480" alt="Combined Image" />

5. Run Hough transformation and run the revised draw_lines(). There the lines are classified into right and left lines. For each class the average of slope and offset (or intercept) is calculated and handed over to the equation for a line. To handle the increased size of the challenge video the image.shape() is also handed over to this function to get the boundaries of the picture correctly.

<img src="test_images_output/lines.png" width="480" alt="Combined Image" />

6. Finally the lines are shown in an overlay with the inital picture / video.

<img src="test_images_output/final.png" width="480" alt="Combined Image" />

