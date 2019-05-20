---
title: Communication Base Station
date: 2019-05-03
tags: [C++, ROS, Gazebo, RVIZ, SolidWorks, Arduino, Raspberry Pi, motor, controller, mechanical, electrical, software]
header:
    image:
---

As part of the University of Waterloo Robotics Student Design Team, I undertook a project to construct a communication base station capable of tracking a moving rover robot and transmitting information via antenna to it. This was a multidisciplinary project combining aspects of mechanical, electrical and software engineering into one. 

## Mechanical 

The mechanical side of the project involved designing the base station from scratch using SolidWorks. The mechanical system functioned on the principle of using a worm-gear system to rotate the antenna in either direction. Below is a screenshot of the finished SolidWorks model: 
<br /><br />
![SolidWorks 3D Model](/images/cbs.png)

In addition to making the design, I also sourced all the parts required to complete the device. After ordering all the parts, I physically machined all the pieces and assembled the final product. 

## Software

In terms of software, I programmed the algorithms that rotated the antenna to continually point in the direction of the rover robot as it moved around in the field. The code was written in C++ and hosted on the ROS system to interface with the rest of the robot's code. The location of the rover was acquired through GPS, IMU and encoder data fused using an EKF filter. 

In order to test and troubleshoot the logic, I imported the CAD model of the base station into a Gazebo/RVIZ simulator and was able to fine-tune the algorithm for the rover. A video demonstrating this simulation is feature below (the choppiness of the video is due to the sheer strain put on my laptop from running video capture software at the same time as a complex simulation):
<div align="center">
<iframe src="https://drive.google.com/file/d/1D0DC3AFCta3nRObb6diKicVJ1_wvgWAL/preview" width="640" height="480"></iframe>
</div>

## Electrical

The final element of the project was to power the worm-gear system using a DC gear motor. Furthermore, the gear motor was controlled by an Arduino coupled with an H-Bridge intergrated circuit to be able to send specific commands to the motor based on the instructions being delivered from the tracking algorithm. The Arduino also had to communicate with a Raspberry Pi running a ROS Node which was done through a serial connection. Lastly, the entire system had to be powered which was done through a 12V lithium polymer battery. 







