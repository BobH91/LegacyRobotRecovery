# Sammy Architecture Recovered Checkpoint

Date: 2026-08-05

## Recovery State

The Sammy backup image has been successfully mounted read-only and extracted.

Recovered workspace:

Recovered_Files/Sammy_Extracted/catkin_ws

The ROS catkin workspace contains the original Sammy robot software.

## Recovered ROS Package

Primary robot package:

ardros

Location:

catkin_ws/src/ardros

Recovered files include:

- package.xml
- CMakeLists.txt
- launch files
- nodes
- configuration files

## Launch Architecture

Recovered launch file:

ardros/launch/sammy.launch

This launches:

ardros/nodes/sammy.py

The Sammy node is the ROS hardware interface.

## Main Control Node

Recovered file:

ardros/nodes/sammy.py

Identified functions:

- Serial communication with embedded controller
- Odometry processing
- ROS topic publishing
- TF transform broadcasting

## Serial Communication

The recovered code uses:

SerialDataGateway

The embedded controller sends odometry messages in this format:

odomw,x,y,theta,vx,omega

Recovered fields:

- x position
- y position
- heading angle
- linear velocity
- angular velocity

## ROS Outputs

The node publishes:

/odom

/serial

It broadcasts:

odom -> base_link

This indicates a standard ROS mobile robot architecture.

## Recovered Architecture Model

ROS Computer

    |
    | serial communication
    |
Embedded Controller

    |
    |
Motor Drivers + Encoders

The ROS computer handled high-level robot functions.

The embedded controller handled low-level motor and encoder functions.

## Recovery Rules

- Source files have not been modified.
- Recovery remains read-only.
- Findings are based only on recovered evidence.

## Next Investigation

Future investigation will identify:

1. Embedded controller hardware
2. Motor driver hardware
3. Firmware source
4. Serial protocol details
5. Hardware configuration files
