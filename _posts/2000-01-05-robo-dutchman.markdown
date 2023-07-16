---
layout: project
title:  "RoboDutchman"
picture-url: "/assets/images/robodutchman/robodutchman-picture.jpg"
type: "project"
publish: yes
---

<h2>Overview</h2>

RoboDutchman is a robotics project developed for 24-778 (Mechatronic Design). Each year, Leidos challenges CMU students in 24-778 to create an autonomous robot to assist with maintenance on different components on the ship, including reading/updating the state of valves and breakers and navigating autonomously in a fixed environment. 

For this capstone project, the environment was simplified to help focus our efforts on the primary concerns of the application - navigating autonomously in a fixed environment and reading/updating the states of breakers and valves. As a result, we made the decision to use a fixed mobile robot base with a 4 DOF robot arm. After researching prior end effector designs and comparing our options, we created a spring-loaded multi-pin end effector, allowing us to more easily grasp and manipulate different shaped valves. An overview video is provided below:

<div style="position: relative; width: 100%; padding-bottom: 75%; margin-bottom: 1.85625rem">
    <iframe style="position: absolute" width="100%" height="100%" src="https://www.youtube.com/embed/sI3vM6nMyZc;&mute=1" allowfullscreen></iframe>
</div>

The development of this project was interrupted with the sudden move to virtual class due to the Covid-19 pandemic. As a result, we utilized Discord video calls and SSH capabilities on the robot to remotely test and debug the robot software.

<h2>Mechanical Design</h2>

<h3>Locomotion</h3>

After researching prior team's robots, there were two prevalent drive mechanisms - omnidirection drive and differential drive. Due to the complex software and debugging required for this task as well as power requirements, we made the decision to utilize a tried and tested navigation base - a two wheel differential drive with two passive casters. This additionally gave us the ability to accurately rotate in place to quickly fine tune arm trajectories.

<figure><img src="{{'/assets/images/robodutchman/robodutchman.jpg' | relative_url}}"></figure>

<h3>Manipulator</h3>

For the manipulator, we decided to use a 4 DOF robotic arm to interact with the valves/switches. The arm had a shoulder joint, an elbow joint, and two wrist joints. 

<figure><img src="{{'/assets/images/robodutchman/manipulator.jpg' | relative_url}}"></figure>

<h3>End-Effector</h3>

From prior designs, we noted two popular end effector designs: a granular jammer and a multi-pin spring-loaded end effector. Both of these end effectors seemed quite effective for the task of manipulating the valves/switches, so our team utilized a trade study to ultimately select the multi-pin spring-loaded end effector.

<figure><img src="{{'/assets/images/robodutchman/end-effector.jpg' | relative_url}}"></figure>

<h2>Software Design</h2>

<h3>Localization</h3>

To localize and map the robot in it's fixed space, we utilized two primary sources of information: wheel odometry and 2D LIDAR scans. The odometry data was calculated from the Hebi actuators we were using as our wheels while the 2D LIDAR is received from an RPLIDAR A1 mounted to the chassis. 

Since we used ROS as our robotics backend, we were able to utilize the large repository of mapping/localization packages others have created. To create the map, we utilized <a href="http://wiki.ros.org/gmapping" target="_blank">gmapping</a>. This allowed us to generate an occupancy grid of our space utilizing a Rao-Blackwellized particle filter based SLAM implementation.

<figure><img src="{{'/assets/images/robodutchman/mapping.jpg' | relative_url}}"></figure>

To localize within this map, we utilized <a href="http://wiki.ros.org/amcl" target="_blank">AMCL</a>, an adaptive particle filter, to localize the robot given the robot's odometry estimate and 2D LIDAR scans.

<figure><img src="{{'/assets/images/robodutchman/amcl.jpg' | relative_url}}"></figure>

<h3>Valve/Switch State Identification</h3>

Properly manipulating the switches and valves required us to identify the specific pose and state of them relative to our robot arm. To solve this problem, we utilized the D435i RGB-D camera to identify the position of the valves/switches and get the position to them.

To identify the position of the valves/switches, we re-trained YOLOv3 for our specific use case. The retraining of the network for our valves/switches allowed for consistent (~98% precision) segmentation and identification of the valves and switches.

<figure><img src="{{'/assets/images/robodutchman/classification.jpg' | relative_url}}"></figure>

<h2>Report</h2>

To culminate the project, our team wrote a final report describing all of our efforts to develop RoboDutchman. This report can be found <a href="{{'/assets/files/robodutchman-report.pdf' | relative_url}}" target="_blank">here</a>.