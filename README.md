# vision_master
IGVC 2020 - Wayne State <br>
Completed lane detection pipeline with lanes converted to laser scans and merged with LIDAR.

### Converting lanes to laser scan
Change the index of the usb camera in /lane_laser_scan/lane_laser_scan.py
`ls -l /dev |grep ttyUSB` for rplidar or `ls -l /dev |grep ttyACM` for Hokuyo lidar to get the name of the LiDAR
`sudo chmod 666 /dev/ttyACM0` to change permission
`roslaunch lane_laser_scan lane_hokuyo` will launch the lane detection pipeline and convert image frames to laser scans and merge with the LiDAR's laser scans.
![annotated](media/lidar_merge.jpg)
