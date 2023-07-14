# About Repository:
This repository makes use of the Husarion Rosbot within simulated gazebo environments. As part of the JEMARO Days 2023 challenge, this repository is used to show a simulated take on the three outlayed challenges, rather than the in-person, real rosbot event. 

# Installation:
Prepare a repository using the following commands:

```
cd ~
mkdir ros_workspace
mkdir ros_workspace/src
cd ~/ros_workspace/src
catkin_init_workspace
cd ~/ros_workspace
catkin_make
```

You can then clone the Rosbot-Simulation repo into your newly created workspace:

```
cd ~/ros_workspace/src
git clone https://github.com/MackJackenna/Rosbot-Simulation.git
```
You will also then need to clone the the aruco_ros and rosbot_description repos for the markers and URDF model respectively:

```
cd ~/ros_workspace/src
git clone https://github.com/pal-robotics/aruco_ros.git
git clone https://github.com/husarion/rosbot_description.git
```
You shoukd then build the workspace:

```
cd ~/ros_workspace
catkin_make
```
And finally, source the repository:

```
cd ~/ros_workspace/devel
source setup.bash
```

# How to use:
If all steps above were successful, you may now run the gazebo challenges. Currently the robot is only controlled via Teleop, however future work will involve autonomous completion of the challenges. 

Please run roscore before initiating any challenge.

### Challenge One:

The objective of this challenge is to have the rosbot enter into a track, complete one lap and then exit the track.
```
roslaunch robot_description rosbot_ch1.launch
```
This should spawn the gazebo environment with the rosbot. This challenge does not require the use of the built in camera/marker detection. To move the rosbot around the environment, open a seperate terminal and run:

```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
This will give you control to move around the environment and complete the challenge via user input.

### Challenge Two:

This challenge makes use of the Aruco markers to give instructions to the bot. The environment is set-up in a way where it should be autonomous, but can be completed teleoped for now.
```
roslaunch robot_description rosbot_ch2.launch
```
Launch the file to bring up the challenge. To make use of the marker detection, run in a seperate terminal:
```
rosrun aruco_ros marker_publisher /image:=/camera/rgb/image_raw
```
This will display which marker is detected. Run again the teleop in a seperate terminal with:
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

### Challenge Three:

This challenge revolves around the rosbot autonmously finding 5 'tennis balls' around a maze-like environment.
```
roslaunch robot_description rosbot_ch3.launch
```
Same as above, in two seperate terminals run the marker detection and teleop:
```
rosrun aruco_ros marker_publisher /image:=/camera/rgb/image_raw
```
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
