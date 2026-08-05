# Sammy Navigation Recovery Checkpoint

Date: 2026-08-05

## Checkpoint Commit

Current verified repository state:

5a34267

Documented recovery layers:

- Sammy recovered architecture
- Sammy hardware configuration
- Sammy STM32 serial protocol
- Sammy navigation configuration

## Confirmed System Architecture

Recovered evidence shows:

Sensors
|
ROS Navigation Stack
|
move_base
|
cmd_vel
|
ardros ROS serial driver
|
ASCII serial protocol
|
STM32 motor controller
|
Motors and encoders
|
Odometry feedback
|
ROS

## Confirmed Recovery Evidence

Hardware layer:

- STM32-based motor controller
- Serial interface:
  - /dev/ttySTM32
  - 115200 baud
- Differential drive geometry
- Encoder resolution:
  - 9750 counts/revolution

Control layer:

- ROS cmd_vel input
- Twist conversion:
  - linear velocity
  - angular velocity
- Serial motion command:
  - s <velocity> <turn>

Feedback layer:

- STM32 odometry messages
- ROS odom publication
- TF:
  - odom -> base_link

Navigation layer:

- move_base recovered
- TrajectoryPlannerROS recovered
- global costmap recovered
- local costmap recovered
- laser scan obstacle handling recovered

## Remaining Unknowns

Not yet recovered:

- Full autonomous launch sequence
- Original map files
- Complete sensor launch configuration
- STM32 firmware source

## Next Recovery Target

Recover runtime startup architecture from:

Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/launch/

Focus files:

- navigation.launch
- ardros_configuration.launch
- slam.launch
- amcl_diff.launch
- kinect_laser.launch

