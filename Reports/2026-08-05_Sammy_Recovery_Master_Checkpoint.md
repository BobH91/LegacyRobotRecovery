# Sammy Recovery Master Checkpoint

Date: 2026-08-05

## Recovery Status

Sammy backup image recovery has reached a verified filesystem and ROS source recovery state.

Repository:
LegacyRobotRecovery

## Source Image Verified

Recovered image:

sammy_backup_20191212

Verification:

- 29 GB disk image
- DOS/MBR partition table
- Linux ext4 root partition
- FAT32 boot partition

Loop device verification:

/dev/loop33

Partitions:

/dev/loop33p1
/dev/loop33p2

## Root Filesystem Recovery

Verified mount:

Recovered_Files/Sammy_Image/rootfs

Recovered Linux structure:

- bin
- boot
- etc
- home
- lib
- opt
- usr
- var

## User Home Recovery

Recovered:

/home/ubuntu

Contains:

- ROS workspace
- configuration files
- robot logs
- calibration files
- historical data

## ROS Workspace Recovery

Recovered:

Recovered_Files/Sammy_Extracted/catkin_ws

Verified packages:

- ardros
- em7180_imu
- ntrip_ros
- rtcm_msgs
- sammy
- sicktoolbox
- sicktoolbox_wrapper
- ublox_f9p

## Sammy Control Software Recovery

Recovered package:

catkin_ws/src/ardros

Important recovered files:

nodes/sammy.py
nodes/arduino.py
nodes/SerialDataGateway.py

launch/sammy.launch

info/ardros.yaml

## Recovered Architecture

Verified architecture:

ROS Computer
    |
    | Serial connection
    |
STM32 Controller
    |
    |
Robot hardware


Evidence:

port: /dev/ttySTM32

baudRate: 115200


## Recovered Hardware Configuration

Differential drive parameters:

wheelDiameter:
0.0763 m

trackWidth:
0.379 m

countsPerRevolution:
9750


## Recovered Controller Configuration

Speed controller:

velocityPParam:
1.0

velocityIParam:
0.2

turnPParam:
0.05

turnIParam:
0.05

commandTimeout:
1.0


## Verified Recovery Milestones

Completed:

1. Backup image identified
2. Read-only loop mount verified
3. Root filesystem recovered
4. Home directory recovered
5. ROS workspace recovered
6. Source packages extracted
7. Sammy architecture documented
8. Hardware configuration documented


## Current Unknowns

Not yet recovered:

- STM32 serial command protocol
- Embedded firmware source
- Exact motor driver implementation
- Original hardware wiring


## Next Recovery Phase

Investigate communication protocol using:

- ardros/nodes/sammy.py
- ardros/nodes/arduino.py
- ardros/nodes/SerialDataGateway.py

No hardware reconstruction or modification should occur until the communication protocol is documented.

