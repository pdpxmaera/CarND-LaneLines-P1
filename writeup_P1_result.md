#**Finding Lane Lines on the Road** 


### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

Step 1: Load image and convert to grayscale
Step 2: Check image size. Algorithm is made for 960x540. Resize to 960x540 as needed. (challenge video had to be resized first)
Step 3: Blur out image to reduce noise. gaussian_blur function is used here 
Step 4: Extract edge using Canny function
Step 5: Define area of interest to reduce unnecessary detection. Polygon is used to include left and right lane marking area. Sky, road background, and vehicle front hood area are all excluded. 
Step 6: Perform hough transformation and convert edges into lines.
Step 7: Select line to draw on the image. Calculate slope and intercept for each line. Group into left and right side. Collect array of slope and intercept which many represent left and lane markings. 
Select median of each then draw line from define position. 


###2. Identify potential shortcomings with your current pipeline

I could not smooth out the lane detection, as each frame is processed individually. The detection result is not shared between frames.
I did not account for curvature of the road. Road with smaller radius will have unstable detection with current algorithm.


###3. Suggest possible improvements to your pipeline

Track of lane marking between frames
Account for road curvature and camber
Dynamically edge detection threshold based on background road color
Use pare of edge to identify fine lane marking width.
Optimize image detection area. Two separate boxes for left and right lane
