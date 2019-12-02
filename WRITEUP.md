# SFND Project 3, Camera/Lidar Fusion

## FP.1 Match 3D Objects

Function to match the bounding boxes is implemented in camera_fusion_student.cpp around line 289. The approach is to loop through each pair of bounding boxes (with and inner and outer loop), and for each pair track how keypoint matches between the two images are within both bounding boxes. Whichever pair of bounding boxes has most matches is called the best match, with a low cutoff of 5 matches.

## FP.2 Compute Lidar Based TTC

Function to compute lidar based TTC is located in camera_fusion_student.cpp around line 222. The approach is look at all the x distances between ego car and front car, and try to filter by both low reflectivity, and having a x which is far outside of the distribution of x values across all the points. Then the mean of all the distances from ego car are computed in both images, and then the TTC is computed under the constant velocity assumption using the distances and the frame rate.

## FP.3 & FP.4 Compute Camera TTC

Function to compute camera based TTC is located in camera_fusion_student.cpp around line 135 and 156. First the function clusterKptMatchesWithROI keeps only those points within the bounding boxes. Second, all the distance ratio matches are computed. Then again, poor matches are filtered if their predictions of distance to ego car is well outside of the distribution of values of other points (in the function computeTTCCamera).

## FP.5 Lidar Analysis

![lidar_video](lidar_series.gif)

![lidar_graph]('FAST_FREAK.png')
