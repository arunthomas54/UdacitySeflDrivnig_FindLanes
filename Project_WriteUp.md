# **Uadcity Self Driving Car Nanodegree Program Project : Finding Lane Lines on the Road** 

Detecting the lane lines is one of the first step perfromed in the approach for a self driving car. In this project we are trying to detect the lane markings on road.

The goal of the project is to make a pipeline that finds the lane on the road.

[//]: # (Image References)

### Steps performed in detecting lanes on a image

1. First the image is converted into grayscale image

[image1]: ./test_images_output/output_gray_solidYellowLeft.jpg "Grayscale Image"
![alt text][image1]

2. On the grayscale image the Gaussian blur effect is performed

[image2]: ./test_images_output/output_gaussian_solidYellowLeft.jpg "Grayscale image with Gaussian Blur"
![alt text][image2]

3. On the grayscale image with Gaussian blur the canny edge detetion is performed

[image3]: ./test_images_output/output_canny_solidYellowLeft.jpg "Canny Edge Detected image"
![alt text][image3]

4. In the next step the region of interest is defined and the other parts are removed

[image4]: ./test_images_output/output_region_solidYellowLeft.jpg "Image cropped to region of interest"
![alt text][image4]

5. Next the Hough transform is performed and the weighted image is obtained in the defined region of interest

[image5]: ./test_images_output/output_weighted_solidYellowLeft.jpg "Hough transformed image"
![alt text][image5]

---

### Draw Line function modification

The next step was to enhance the draw_lines() function.
#### Approach to the algorithm development of enhanching draw_lines() function
a) The idea was to use the line equation y = mx + b , m= slope and b= intercepts to draw the lines
b) Keeping this in mind from the hough transformed image was going to make 2 arrays of slopes and intercepts for both left and right side.
c) The left side and right side was differentiated by calculated slope vales less than 0 and right side greater than 0 
d) Average of slopes and intercepts for both left and right side was calculated
e) Then 2 lines would be drawn using the slope and intercepts for both sides.
f) One point was fixed as the y-axis max and the next point was tuned to be almost and 50% of y-axis max
g) Based on the equation x= (y-b)/m , the x-axis points were calculted
h) Using the abov calcualted x and y values 2 lines are drawn on left and right side

[image6]: ./test_images_output/output_final_solidYellowLeft.jpg "Solid Lines image"
![alt text][image6]


### Pipe line function
Using the above methods a pipeline function was created `lane_finding_pipeline` and into this pipe line function an image can be passed and the lanes detected would be the output

This pipeline was was also used to find the lanes on a video and it suuccessfully detected the lanes


### 2. Potential shortcomings with your current pipeline

1. Even though the lanes are detected succesfully the lanes are little bit jumping mostly at curves 
2. Currently the test images have good lighting the solution might not work for very dark images

### 3. Possible improvements to your pipeline

1. Increase the accuraccy of the lane detection and work well for the curve roads
2. Increse the efficiency to detect in very dark images also
