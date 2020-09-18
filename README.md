# ros-slam

A ROS Implementation of Simultaneous Localization and Mapping using navbase and amcl.

The bag file is not included in the repository, use a bag and modify the TF tree accordingly.

The following map was obtained using gmapping_visual.launch:

![map_visual](https://user-images.githubusercontent.com/12733113/93635821-fc1fa680-fa03-11ea-96d8-c24e2d13a71e.png)

------------------------------------------------------------------------------------------
## Description of the files: 
------------------------------------------------------------------------------------------

Folder /cfg contains the configuration files for move_base package

Folder /launch contains:
  gmapping_optitrack.launch: Launch file for gmapping with gmapping_optitrack
  gmapping_visual.launch: Launch file for gmapping with visual odometry
  nav_stack.launch: Launch file for the navigation stack
  amcl.launch.xml: Configuration file for amcl, called from nav_stack.launch

Folder /maps contains the map created with optitrack (map_optitrack.pgm) and the 
      map created with visual odometry (map_visual.pgm)

------------------------------------------------------------------------------------------
##  Structure of the tf tree for gmapping_optitrack.launch 	 
------------------------------------------------------------------------------------------
     map_global
         +
         |
         |
         v
       world
         +
         |
         |
         v
  Robot_1/base_link
         +
         |
         |
         v
     os1_sensor
     +        +
     |        |
     |        |
     v        v
os1_lidar  pixhawk_imu

------------------------------------------------------------------------------------------
## Structure of the tf tree for gmapping_visual.launch 	 
------------------------------------------------------------------------------------------
     map_global
         +
         |
         |
         v
  camera_odom_frame
         +
         |
         |
         v
  camera_pose_frame
         +
         |
         |
         v
     os1_sensor
     +        +
     |        |
     |        |
     v        v
os1_lidar  pixhawk_imu
 

------------------------------------------------------------------------------------------
## Structure of the tf tree for nav_stack.launch 	 
------------------------------------------------------------------------------------------
          map_global
              +
              |
              |
              v
       camera_odom_frame
              +
              |
              |
              v
       camera_pose_frame
              +
              |
              |
              v
          os1_sensor
     +        +            +
     |        |            |
     |        |            |
     v        v            v
os1_lidar  pixhawk_imu  os1_imu

     

------------------------------------------------------------------------------------------
## How to start/use the nodes 	 
------------------------------------------------------------------------------------------

For gmapping: roslaunch project_two gmapping_optitrack.launch  or
    roslaunch project_two gmapping_visual.launch
 

For move_base: roslaunch project_two nav_stack.launch
