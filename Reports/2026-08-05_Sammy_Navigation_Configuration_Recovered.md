# Sammy Navigation Configuration Recovered

Date: 2026-08-05

## Source Evidence

Recovered from:

- Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/info/base_local_planner_params.yaml
- Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/info/costmap_common_params.yaml
- Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/info/global_costmap_params.yaml
- Recovered_Files/Sammy_Extracted/catkin_ws/src/ardros/info/local_costmap_params.yaml

## Navigation Stack

The recovered configuration confirms Sammy was configured to use the ROS navigation stack:

- move_base
- TrajectoryPlannerROS local planner
- global costmap
- local costmap
- laser scan obstacle detection

Architecture:

ROS Navigation
|
move_base
|
TrajectoryPlannerROS
|
cmd_vel
|
ardros serial driver
|
STM32 motor controller


## Local Planner Configuration

Recovered planner:

TrajectoryPlannerROS

Maximum velocity:

max_vel_x:
0.5 m/s

Minimum velocity:

min_vel_x:
0.02 m/s

Maximum rotational velocity:

max_rotational_vel:
1.0 rad/s

Minimum in-place rotation:

min_in_place_rotational_vel:
0.2 rad/s


Acceleration limits:

acc_lim_x:
0.2

acc_lim_y:
0.2

acc_lim_th:
1.0


Robot model:

holonomic_robot:
false

Interpretation:

Sammy was configured as a differential drive robot.

## Goal Tolerance

Recovered:

yaw_goal_tolerance:
0.1 radians

xy_goal_tolerance:
0.2 meters

latch_xy_goal_tolerance:
true


Interpretation:

The robot could accept a goal when within approximately:

20 cm position tolerance

and

5.7 degree heading tolerance


## Trajectory Simulation

Recovered:

sim_time:
1.5 seconds

vx_samples:
10

vtheta_samples:
20


The planner simulated possible trajectories before selecting motion commands.

## Obstacle Avoidance

Recovered costmap parameters:

obstacle_range:
2.5 meters

raytrace_range:
3.0 meters

inflation_radius:
0.4 meters


Sensor:

laser_scan_sensor

Frame:

openni_depth_frame

Topic:

scan


Interpretation:

Sammy used laser scan data for obstacle marking and clearing.

## Robot Footprint

Recovered footprint polygon:

x/y coordinates define the physical robot boundary used by the navigation stack.

The costmap used this footprint for:

- collision checking
- obstacle inflation
- path planning


## Global Costmap

Recovered:

global_frame:
/map

robot_base_frame:
base_link

update_frequency:
2 Hz

static_map:
true


Interpretation:

Sammy used a stored map for global navigation.

## Local Costmap

Recovered:

global_frame:
/odom

robot_base_frame:
/base_link

update_frequency:
5 Hz

rolling_window:
true

width:
4 meters

height:
4 meters

resolution:
0.05 meters


Interpretation:

Sammy maintained a local moving obstacle map around the robot.

## Recovery Significance

Confirmed:

- Autonomous navigation capability
- Differential drive configuration
- Laser-based obstacle avoidance
- Static map navigation
- Local rolling obstacle avoidance
- ROS move_base integration

Combined with previous recovery:

ROS Navigation
|
cmd_vel
|
ardros
|
STM32 serial protocol
|
motor controller
|
encoders
|
odometry


Remaining unknown:

- Original map files
- ROS launch sequence for full autonomous navigation
- STM32 firmware

