# Overview
IGVC 2020 - Wayne State <br>
ROS workspace for the Auto-Nav challenge. Completed lane detection pipeline with lanes converted to laser scans and merged with LIDAR.

### Lane Detection Pipeline
/lane_laser_scan/pipeline_test.py serves as the integration test for all the operations. Just change the source file image.
![annotated](media/lanes.jpg)
#### Outline
Forked from [George Sung](https://github.com/georgesung/advanced_lane_detection)
Get distortion matrix > Correct distortion > Binary Threshold > Perspective transform > Detect lane and curve fit > Draw area back on origianl

### Converting lanes to laser scan
Change the index of the usb camera in /lane_laser_scan/lane_laser_scan.py. <br>
`ls -l /dev |grep ttyUSB` for rplidar or `ls -l /dev |grep ttyACM` for Hokuyo lidar to get the name of the LiDAR <br>
`sudo chmod 666 /dev/ttyACM0` to change permission <br>
`roslaunch lane_laser_scan lane_hokuyo` will launch the lane detection pipeline and convert image frames to laser scans and merge with the LiDAR's laser scans. <br>
![annotated](media/lidar_merge.jpg)

