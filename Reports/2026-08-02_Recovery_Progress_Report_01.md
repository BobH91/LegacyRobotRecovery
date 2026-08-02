# Raspberry Pi Image Recovery Progress Report

**Date:** August 2, 2026

## Objective

Recover and document the contents of a legacy Raspberry Pi SD card image, identify historical robotics projects, preserve valuable engineering work, and determine whether any components are useful references for the current NanoBot project.

---

# Progress Summary

## 1. SD Card Successfully Mounted

Successfully mounted the Raspberry Pi filesystem and verified the Ubuntu home directory.

Major directories identified:

* `catkin_ws`
* `Downloads`
* `Desktop`
* `imu`
* `sick_workspace`
* Linux kernel source tree
* historical logs
* archived kernel tarball

The image appears to be a working robotics development system from approximately 2019.

---

## 2. ROS Workspace Recovered

Recovered a complete ROS Catkin workspace.

Workspace structure:

* build/
* devel/
* src/

Source packages recovered:

* ardros
* sammy
* em7180_imu
* rtcm_msgs
* ublox_f9p
* ntrip_ros
* sicktoolbox
* sicktoolbox_wrapper

The workspace is intact and contains both source code and build products.

---

## 3. Sammy Package Investigated

The package named `sammy` was examined.

Findings:

* contains launch files
* contains configuration
* contains package metadata
* contains no application source code

Conclusion:

`sammy` is a launch/coordination package rather than the robot controller itself.

---

## 4. Main Robot Controller Identified

The actual robot controller resides in:

`catkin_ws/src/ardros`

Recovered launch files include:

* sammy.launch
* mini_tractor.launch

Recovered executable nodes include:

* arduino.py
* mini_tractor.py
* sammy.py
* DeadReckoning.py
* GoalsSequencer.py
* teleop.py
* velocityLogger.py

This package represents the primary control software for the robot.

---

## 5. Robot Hardware Architecture Recovered

Configuration files reveal the robot communicated with an STM32 controller over serial.

Recovered configuration:

* serial device: `/dev/ttySTM32`
* baud rate: 115200

Recovered robot geometry:

* wheel diameter: 0.0763 m
* track width: 0.379 m
* encoder resolution: 9750 counts/revolution

Recovered controller tuning:

* Velocity PI controller
* Turn PI controller
* 1 second command timeout

---

## 6. Motor Control Protocol Recovered

Recovered the serial protocol used between ROS and the STM32 controller.

High-level ROS Twist commands were converted into serial commands of the form:

`s linear_velocity angular_velocity`

The STM32 handled:

* wheel PID
* odometry
* encoder processing
* motor control

This represents a mature closed-loop control architecture.

---

## 7. Sensor Suite Recovered

The launch files identify the original robot sensor configuration.

Recovered components:

* dual u-blox ZED-F9P GPS receivers
* EM7180 IMU
* SICK LMS200 laser scanner
* rosbag recorder

The robot was designed for autonomous navigation with sensor logging.

---

## 8. Historical Data Located

Located historical rosbag recording:

`2019-10-01-20-48-17.bag`

Although currently only 8 KB in size, it indicates that sensor recording was part of the original workflow.

---

## 9. Linux Source Archive

Recovered:

* complete Linux kernel source tree
* compressed kernel archive

These appear unrelated to robot application software but may document kernel modifications made during development.

---

## 10. Relationship to NanoBot

Comparison indicates that the historical robot and NanoBot share a similar layered architecture.

Historical robot:

Linux computer
→ Serial
→ STM32 controller
→ Motors

NanoBot:

Browser
→ Orin Nano
→ TCP
→ Raspberry Pi
→ PCA9685
→ MMD10A
→ Motors

The historical design delegated deterministic motor control to dedicated hardware while the high-level computer handled navigation and planning.

This architectural pattern remains relevant as a reference for future NanoBot evolution.

---

# Items Preserved for Future Reference

High-value directories identified:

* ardros
* em7180_imu
* ublox_f9p
* sicktoolbox_wrapper

These represent the most significant engineering work recovered so far.

---

# Current Assessment

The recovered image is not simply an operating system backup.

It is a complete robotics development environment containing:

* source code
* ROS packages
* launch configuration
* hardware interface software
* navigation sensor integration
* motor controller interface
* engineering parameters

The recovery effort has successfully identified the software architecture, hardware interfaces, and major subsystems of the historical robot.

---

# Recommended Next Steps

1. Inventory the remaining files outside the ROS workspace.
2. Search for STM32 firmware or Arduino source corresponding to the serial protocol.
3. Determine whether CAD files, wiring diagrams, PCB designs, or documentation are present.
4. Preserve the recovered workspace in a read-only archive.
5. Create a historical reference section within the NanoBot documentation while keeping the recovered code separate from the active NanoBot codebase.
