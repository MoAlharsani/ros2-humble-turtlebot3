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
