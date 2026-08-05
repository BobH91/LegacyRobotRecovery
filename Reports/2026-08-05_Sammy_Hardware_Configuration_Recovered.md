# Sammy Hardware Configuration Recovered

Date: 2026-08-05

## Source

Recovered from:

Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/info/ardros.yaml

This file is loaded by:

catkin_ws/src/ardros/launch/sammy.launch

using:

<rosparam file="$(find ardros)/info/ardros.yaml" command="load" />


## Serial Interface

Recovered configuration:

port: /dev/ttySTM32

baudRate: 115200


Interpretation:

The recovered ROS configuration expects communication with an embedded controller through a serial interface identified as:

/dev/ttySTM32


## Battery Monitoring Configuration

Recovered:

batteryStateParams:

- voltageLowlimit: 12.0
- voltageLowLowlimit: 11.7


Interpretation:

The recovered ROS node contained battery voltage warning thresholds.


## Drive Geometry

Recovered:

- wheelDiameter: 0.0763 m
- trackWidth: 0.379 m
- countsPerRevolution: 9750


Interpretation:

The recovered configuration defines a differential drive robot geometry.

The encoder resolution configured for odometry calculations was:

9750 counts per wheel revolution


## Speed Controller Configuration

Recovered:

- velocityPParam: 1.0
- velocityIParam: 0.2
- turnPParam: 0.05
- turnIParam: 0.05
- commandTimeout: 1.0


Interpretation:

The recovered ROS configuration contains parameters for a speed controller intended to communicate with the embedded controller.

The command timeout value indicates that velocity commands were expected to stop if no command was received for 1 second.


## Recovery Significance

This file documents the first recovered hardware-level configuration from the Sammy software image.

Confirmed:

- Serial interface configuration
- Embedded controller communication endpoint
- Differential drive geometry
- Encoder resolution
- Battery monitoring thresholds
- Speed controller parameters


## Next Investigation Target

Recover the embedded controller communication protocol from:

ardros/nodes/sammy.py

and related serial communication files.

