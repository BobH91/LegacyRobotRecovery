# Sammy System Architecture Checkpoint

Date: 2026-08-05

## Recovery Status

Sammy recovery has reached a stable architecture checkpoint.

Recovered components:

- Robot software architecture
- ROS launch structure
- Hardware configuration
- STM32 serial communication protocol
- Differential drive configuration
- Navigation stack configuration

## Recovered System Architecture

Overall control path:

ROS Applications

|
| cmd_vel
v

ardros ROS driver

|
| ASCII serial protocol
| 115200 baud
v

STM32 Motor Controller

|
| motor commands
| encoder feedback
v

Robot Drive Hardware

|
| odometry
v

ROS Navigation Stack


## Software Layers Recovered

### Application Layer

Recovered ROS capabilities:

- Teleoperation
- Autonomous navigation
- SLAM mapping
- Localization
- RViz visualization


### Navigation Layer

Recovered:

- move_base
- AMCL localization
- gmapping SLAM
- TrajectoryPlannerROS
- Global costmap
- Local costmap


### Robot Interface Layer

Recovered:

- ardros package
- serial gateway
- cmd_vel interface
- odometry publishing
- TF broadcasting


### Hardware Interface Layer

Recovered:

- STM32 motor controller communication
- Differential drive geometry
- Encoder configuration
- Closed-loop speed controller parameters


## Confirmed Hardware Parameters

Serial:

port:
 /dev/ttySTM32

baud:
115200


Drive geometry:

wheel diameter:
0.0763 m

track width:
0.379 m

encoder counts:
9750 counts/revolution


Speed controller:

velocity P:
1.0

velocity I:
0.2

turn P:
0.05

turn I:
0.05

command timeout:
1.0 seconds


## Launch Architecture

Recovered launch modes:

- teleopRobot.launch
- navigation.launch
- slam.launch
- move_base.launch
- sammy.launch
- ardros_configuration.launch


Operational modes identified:

Manual control:

PS3 joystick
|
teleop
|
cmd_vel
|
STM32


Autonomous navigation:

map
|
AMCL
|
move_base
|
cmd_vel
|
STM32


Mapping:

laser data
|
gmapping
|
map creation


## Remaining Unknowns

Not yet recovered:

- STM32 firmware source
- Original map files
- Complete robot hardware wiring
- Original build environment


## Recovery Milestone

This checkpoint establishes the recovered Sammy software architecture baseline.

Future recovery work should proceed from:

Recovered ROS configuration
+
Recovered serial protocol
+
Recovered launch structure

without modifying recovered evidence.

