# Sammy Launch Architecture

Date: 2026-08-05

## Main Launch File

Recovered:

ardros/launch/sammy.launch

## Primary ROS Node

Launch definition:

node name:
sammy

package:
ardros

type:
sammy.py

## Configuration

The node loads:

ardros/info/ardros.yaml

using rosparam.

## Architecture

Startup flow:

roslaunch ardros sammy.launch

        |
        v

ardros/nodes/sammy.py

        |
        v

ardros/info/ardros.yaml

        |
        v

Robot hardware interfaces

## Status

Primary Sammy control entry point identified.

No source files modified.

Next step:

Analyze sammy.py.

