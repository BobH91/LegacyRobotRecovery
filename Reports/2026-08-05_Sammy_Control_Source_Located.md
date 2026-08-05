# Sammy Control Source Located

Date: 2026-08-05

## Recovery Phase

The Sammy ROS workspace has been successfully recovered from:

sammy_backup_20191212

The extracted workspace is located at:

Recovered_Files/Sammy_Extracted/catkin_ws

## Package Discovery

Recovered ROS packages include:

- sammy
- ardros
- em7180_imu
- ntrip_ros
- rtcm_msgs
- sicktoolbox
- sicktoolbox_wrapper
- ublox_f9p

## Important Finding

The package:

catkin_ws/src/sammy

contains:

- launch files
- configuration files
- package metadata

The src directory is empty.

Therefore the primary robot behavior is not located in the sammy package.

## Primary Control Source Located

The main robot control source appears to be:

catkin_ws/src/ardros

Recovered nodes include:

- sammy.py
- DeadReckoning.py
- GoalsSequencer.py
- mini_tractor.py
- teleop.py
- arduino.py
- SerialDataGateway.py
- velocityLogger.py

## Current Recovery Rule

No source modification has been performed.

Current phase:

READ-ONLY SOURCE RECOVERY AND DOCUMENTATION

## Next Analysis Phase

Analyze:

1. ardros/package.xml
2. ardros/launch/sammy.launch
3. ardros/nodes/sammy.py
4. Arduino communication layer
5. Sensor integration
6. Navigation architecture
