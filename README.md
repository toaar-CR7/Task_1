# Task_1
## Task 1 of the mars rover software recruitment. 

## Problem statement
- Performing autonomous navigation using a robot in a
Gazebo world by first creating a map of the environment and then
navigating from point A to point B.

## System Requirements

Ubuntu 22.04
ROS2 Humble
Gazebo Classic
TurtleBot3 Packages
Cartographer SLAM
Nav2
Rviz (Nav2 Goal tool) 

## Workflow
Clone the given git hub repos.
Spawn TurtleBot3 in your chosen world (I have used small_house.world)
Perform SLAM mapping manually
Save the generated map
Reload the saved map
Navigate your bot from A to B using Nav2 Goal tool in Rviz

# Main task work
## Cloning the git hub repos
- mkdir -p ~/turtlebot3_ws/src
- cd ~/turtlebot3_ws/src
- git clone https://github.com/mlherd/Dataset-of-Gazebo-Worlds-Models-and-Maps.git
- git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
- cd ..
- colcon build

### Then clone the git repos and copyt the worlds
- mkdir -p ~/.gazebo/models
- mkdir -p ~/.gazebo/worlds
- cp -r /models/* ~/.gazebo/models/
- cp /worlds/* ~/.gazebo/worlds/
## Launch file creation/editing
- You can create your own launch file for launching the bot inside the small_house.world
OR
- You can change the launch file of the map (like I changed the launch file of turtlebot3_world to launch the turtlebot3 model burger into the small_house.world instead)
## launching gazebo
- ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
## SLAM
- ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
## Teleoperation Control
ros2 run turtlebot3_teleop teleop_keyboard
## Save the Map
ros2 run nav2_map_server map_saver_cli -f ~/my_map
## Navigation in RViz
Click 2D Pose Estimate

    Click robot position and direction
    Click Nav2 Goal
    Click any free space on the map
    Robot moves autonomously to target.





