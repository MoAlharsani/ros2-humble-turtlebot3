# ROS2 Humble with TurtleBot3 
This repository is designed to familiarize you with key concepts such as the Navigation Stack, SLAM (Simultaneous Localization and Mapping), and the process of navigating and mapping environments using the TurtleBot3 Waffle model.

## Prerequisites

Before starting, ensure you have the following installed on your system:

- [ROS2 Humble](https://docs.ros.org/en/humble/Installation.html)
- [Gazebo](https://gazebosim.org/home)
- Install these packages,
  ```bash
  sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-turtlebot3*
  ```


## Run TurtleBot3 World in Gazeboo
1. export the turtlebot model, this line can be added to ~/.bashrc 
    ```bash
    export TURTLEBOT3_MODEL=waffle
    ```
2. Source gazebo workspace
    ```bash
    source /usr/share/gazebo/setup.bash
    ```
    
3. Run the turtlebot3 waffle world
   ```bash
   ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py 
    ```
   Gazebo will run with the turtlebot3 World as here,
![image](https://github.com/user-attachments/assets/eb9efde2-7df9-45b7-bc79-ab818050fcbe)

4. To control the turtlebot3 using keyboard, open another terminal, and export the variable and run the teleop_key node
   ```bash
   export TURTLEBOT3_MODEL=waffle
   ros2 run turtlebot3_teleop teleop_keyboard
   ```
![turtlebot3(3)](https://github.com/user-attachments/assets/333e41ab-22ab-4f1e-90ed-11044bc0f3b3)



## Create and Save a map using SLAM
1. export the turtlebot model, this line can be added to ~/.bashrc 
    ```bash
    export TURTLEBOT3_MODEL=waffle
    ```
2. Source gazebo workspace
    ```bash
    source /usr/share/gazebo/setup.bash
    ```
    
3. Run the turtlebot3 waffle world
   ```bash
   ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py 
    ```
4. Run teleop_key node
   ```bash
   export TURTLEBOT3_MODEL=waffle
   ros2 run turtlebot3_teleop teleop_keyboard
   ```
5. Run SLAM node, this node should open Rviz so the map can be seen, use the teleop_key node to move the turtlebot3 around until all area are covered
   This how it should be after moving the turlebot3 around the area
   ![image](https://github.com/user-attachments/assets/46147ffa-ff16-4fec-b2c5-d5c9f92e3df2)
6. Run this command to save the map
   ```bash
   ros2 run nav2_map_server map_saver_cli -f path/filename
   ```
   notice that there is no file extension, after running this command you will get two files,
   ![image](https://github.com/user-attachments/assets/7f927725-e4b1-4cb9-b2a2-ba1db3da02ab)
   
### Map Configuration (ROS)
what does map.yaml data means? 
   ![image](https://github.com/user-attachments/assets/51e6dd3b-5e7d-4c70-b4e6-d6c7d0d220bb)
   
   
- **Map Image**: `map.pgm`
  - Specifies the filename of the map image. `.pgm` format is commonly used for occupancy grid maps in ROS.

- **Mode**: Trinary (0 for free, 100 for occupied, -1 for unknown)
  - Defines the encoding mode of the map data. Each pixel in the map can represent free space (0), occupied space (100), or unknown (-1).

- **Resolution**: 0.05 meters/pixel
  - Indicates the size of each pixel in meters. In this case, each pixel on the map represents an area of 0.05 meters by 0.05 meters.

- **Origin**: (-1.28, -2.41, 0)
  - Specifies the position of the lower-left corner of the map image in the global coordinate system. The values represent coordinates (x, y) in meters and yaw in radians (0 for no rotation).

- **Negate**: No
  - Determines whether the map should be negated. A value of 0 means the map is not negated. Negating the map would invert the interpretation of free and occupied space.

- **Occupied Threshold**: 0.65
  - Defines the threshold above which cells in the occupancy grid are considered occupied. Any cell with a value greater than or equal to 0.65 in the map is considered occupied.

- **Free Threshold**: 0.25
  - Specifies the threshold below which cells in the occupancy grid are considered free. Any cell with a value less than or equal to 0.25 in the map is considered free.





