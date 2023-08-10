---
layout: project
title:  "PipeDream"
picture-url: "/assets/images/pipedream/pipedream-picture.jpg"
type: "robot"
publish: yes
---

PipeDream was part of a DOE-funded initiative to use robotic platforms to characterize and map pipes at nuclear enrichment facilities. It is an eight-foot-long autonomous robot designed to traverse 30 inch diameter pipes with six flexible drive motors. My role in this project was to initialize a simulation of the robot and it's sensors and GUI to visualize the simulated data.

<!--more-->
 
<figure><img src="{{'/assets/images/pipedream/pipedream-robot.jpg' | relative_url}}"></figure>

<h2>Sensors</h2>

In order to measure the thickness of deposits on the wall, PipeDream utilized two sensors to get an estimate: an inductive proximity sensor to get the distance to the pipe surface and an optical triangulation displacement sensor to measure the distance to the deposit surface. The difference of these two measurements would represent the thickness of the deposit.

<figure><img src="{{'/assets/images/pipedream/sensor-array.jpg' | relative_url}}"></figure>

Additionally, a classical sensor suite of encoders, IMU, and 2D LIDAR were utilized for mapping and localization purposes.

<h2>Simulation</h2>

My primary role in this project was to set up a simulated environment for the robot and create a GUI to visualize this data. To accomplish this task, I utilized Gazebo to create a sparse model of PipeDream as well as its sensor array. For each sensor, I wrote up a separate Gazebo plugin to emulate data received by each sensor.

For the GUI, I utilized PyQT to create data visualizations for the inductive and displacement sensors over time. After I left this project, this GUI was updated and utilized to visualize post processed data from live tests.

<figure><img src="{{'/assets/images/pipedream/gui.jpg' | relative_url}}"></figure>

<h2>Publications</h2>

PipeDream was part of a larger effort by CMU in collaboration with DOE to evaluate holdup deposits in deactivated gaseous diffusion piping. This effort consisted of two robots: PipeDream (for volumetric deposit characterization/mapping) and RadPiper (for radiation-based assay). For more information, check out the publications <a href="https://www.ri.cmu.edu/robot/radpiper/" target="_blank">here</a>. 