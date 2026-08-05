# Sammy STM32 Serial Protocol Recovered

Date: 2026-08-05

## Source Evidence

Recovered from:

- Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/nodes/SerialDataGateway.py
- Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/nodes/mini_tractor.py
- Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/nodes/sammy.py

## Serial Transport

Recovered configuration:

- Port: /dev/ttySTM32
- Baud rate: 115200

Communication method:

ROS computer
|
| USB serial connection
|
STM32 motor controller

The serial transport uses ASCII text messages.

Messages are terminated using carriage return:

\r

Received messages are line based and terminated by newline:

\n

## STM32 Initialization Handshake

The STM32 controller requests configuration from the ROS computer.

Recovered sequence:

STM32:

InitializeDriveGeometry

ROS responds:

dg <wheelDiameter> <trackWidth> <countsPerRevolution>\r


STM32:

InitializeSpeedController

ROS responds:

sc <velocityP> <velocityI> <turnP> <turnI> <commandTimeout>\r


STM32:

initialized

The ROS node then considers the controller ready.

## Drive Geometry Command

Recovered command format:

dg <wheelDiameter> <trackWidth> <encoderCounts>\r

Recovered values:

wheelDiameter:
0.0763 meters

trackWidth:
0.379 meters

countsPerRevolution:
9750

## Speed Controller Command

Recovered command format:

sc <velocityP> <velocityI> <turnP> <turnI> <timeout>\r

Recovered values:

velocityP:
1.0

velocityI:
0.2

turnP:
0.05

turnI:
0.05

commandTimeout:
1.0 seconds

## Motion Command

ROS receives:

geometry_msgs/Twist

Recovered conversion:

linear velocity:

v = twistCommand.linear.x

turn command:

omega = twistCommand.angular.z * 400

Outgoing serial command:

s <velocity> <turn_command>\r

Example:

s 0.25 40.00\r

## Odometry Feedback

STM32 sends odometry messages back to ROS.

Recovered message identifier:

odomw

The ROS node publishes:

- nav_msgs/Odometry
- TF transform:

odom -> base_link

## Recovered Architecture

Complete communication path:

ROS cmd_vel

|

v

ROS serial driver

|

s <velocity> <turn>\r

|

STM32 controller

|

motors and encoders

|

odometry feedback

|

ROS /odom


## Recovery Significance

Confirmed:

- STM32 based motor controller architecture
- ASCII serial protocol
- Initialization handshake
- Differential drive parameter loading
- Closed-loop speed controller configuration
- Velocity command format
- Odometry feedback path

Remaining unknown:

The STM32 firmware source code has not yet been recovered.

