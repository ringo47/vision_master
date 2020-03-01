# Overview
IGVC 2020 - Wayne State <br>
ROS workspace for the Auto-Nav challenge. Completed lane detection pipeline with lanes converted to laser scans and merged with LIDAR.

### Lane Detection Pipeline
/lane_laser_scan/pipeline_test.py serves as the integration test for all the operations. Just change the source file image.
![annotated](media/lane.jpg)
#### Outline
Forked from [George Sung](https://github.com/georgesung/advanced_lane_detection)
* Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Apply a distortion correction to raw images.
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view").
* Detect lane pixels and fit to find the lane boundary.
* Determine the curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

### Converting lanes to laser scan
Change the index of the usb camera in /lane_laser_scan/lane_laser_scan.py
`ls -l /dev |grep ttyUSB` for rplidar or `ls -l /dev |grep ttyACM` for Hokuyo lidar to get the name of the LiDAR
`sudo chmod 666 /dev/ttyACM0` to change permission
`roslaunch lane_laser_scan lane_hokuyo` will launch the lane detection pipeline and convert image frames to laser scans and merge with the LiDAR's laser scans.
![annotated](media/lidar_merge.jpg)

