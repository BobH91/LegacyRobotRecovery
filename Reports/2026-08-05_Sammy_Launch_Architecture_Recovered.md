# Sammy Launch Architecture Recovered

Date: 2026-08-05

## Source Evidence

Recovered from:

Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/launch/

Launch files analyzed:

* sammy.launch
* ardros_configuration.launch
* ardros_standalone.launch
* navigation.launch
* move_base.launch
* amcl_diff.launch
* slam.launch
* kinect_laser.launch
* teleop.launch
* teleopRobot.launch

---

# Launch Architecture Overview

Recovered system architecture:

```
Operator
 |
 | teleop / joystick
 |
 v
ROS cmd_vel
 |
 v
ardros serial driver
 |
 USB Serial
 |
 v
STM32 Motor Controller
 |
 Motors + Encoders
 |
 v
Odometry
```

Autonomous navigation path:

```
Navigation Stack

map / localization / planning

        |
        v

move_base

        |
        v

cmd_vel

        |
        v

ardros

        |
        v

STM32 controller
```

---

# Hardware Driver Launch

## sammy.launch

Starts:

```
node:
pkg="ardros"
type="sammy.py"
```

Loads:

```
info/ardros.yaml
```

Purpose:

Provides the ROS interface to the STM32 motor controller.

---

# Full Robot Configuration

## ardros_configuration.launch

Starts:

* ardros serial node
* Kinect sensor configuration
* static transform between robot and camera

Recovered transform:

```
base_link -> openni_camera
```

Static transform:

```
-0.215 0.055 0.226
```

This launch file represents the physical robot configuration.

---

# Sensor System

## kinect_laser.launch

Recovered sensor pipeline:

```
Kinect Camera

        |
        v

OpenNI Camera Driver

        |
        v

PointCloud

        |
        v

pointcloud_to_laserscan

        |
        v

LaserScan topic
```

Navigation sensor:

```
topic:
scan
```

Sensor frame:

```
openni_depth_frame
```

---

# Autonomous Navigation

## navigation.launch

Includes:

```
ardros_configuration.launch

move_base.launch
```

Starts:

```
rviz
```

Visualization:

```
rviz/navigation.vcg
```

---

# move_base.launch

Starts:

```
map_server
amcl
move_base
```

Loads:

```
costmap_common_params.yaml
local_costmap_params.yaml
global_costmap_params.yaml
base_local_planner_params.yaml
```

Recovered navigation stack:

```
map_server
 |
 v
AMCL localization
 |
 v
move_base planner
 |
 v
cmd_vel
 |
 v
STM32 controller
```

---

# Localization

## amcl_diff.launch

Recovered localization method:

```
AMCL
```

Robot model:

```
diff
```

Meaning:

Differential drive odometry model.

Uses:

* laser scan
* odometry
* map

to estimate robot position.

---

# Mapping

## slam.launch

Recovered mapping system:

```
gmapping
```

Inputs:

* laser scan
* odometry

Output:

```
map
```

Configuration confirms Sammy supported autonomous map creation.

---

# Manual Control

## teleop.launch

Starts:

```
joy_node
```

and:

```
teleop.py
```

Loads:

```
joystick.yaml
teleop.yaml
```

Control path:

```
PS3 Controller

      |

joy_node

      |

teleop.py

      |

cmd_vel

      |

STM32
```

---

# Combined Recovery

Recovered Sammy operating modes:

## Manual Driving

```
Joystick
 |
teleop
 |
cmd_vel
 |
ardros
 |
STM32
```

## Autonomous Navigation

```
Map
 |
AMCL
 |
move_base
 |
cmd_vel
 |
ardros
 |
STM32
```

## Mapping

```
Kinect/Laser
 |
gmapping
 |
map
```

---

# Recovery Significance

Confirmed:

* Complete ROS launch hierarchy
* Hardware driver startup
* Kinect sensor integration
* Laser scan generation
* AMCL localization
* SLAM capability
* Autonomous navigation pipeline
* Teleoperation pipeline

Remaining unknowns:

* Original STM32 firmware
* Original map files
* Original RViz configuration files
* Original robot URDF/model files


