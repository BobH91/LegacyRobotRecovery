# Legacy Robot Recovery Status Report

Date: 2026-08-02

## Purpose

This project is a recovery investigation of an older robot system.
It is completely separate from NanoBot.

No files, code, documentation, or conclusions from this investigation
are to modify or influence the NanoBot project.

---

# Current Recovery Source

Original recovery source:

External USB drive backup image

Mounted location:

/media/bob/PI_ROOT

Filesystem:

ext4

Mount status:

Read-only

Observed mount:

/dev/loop36p2 on /media/bob/PI_ROOT type ext4
(ro,nosuid,nodev,relatime,errors=remount-ro,emergency_ro)

---

# Recovered Information

Recovered directory:

/home/ubuntu/catkin_ws

ROS workspace identified:

catkin_ws

ROS packages identified:

- sammy
- ardros
- em7180_imu
- sicktoolbox
- sicktoolbox_wrapper
- ublox_f9p
- ntrip_ros
- rtcm_msgs

---

# Important Findings

The workspace appears to be a ROS differential-drive robot project.

Evidence:

sammy.launch:
- starts ardros
- starts ublox GPS nodes
- records rosbag data

ardros package:
- communicates with embedded controller
- serial port:
  /dev/ttySTM32
- baud:
  115200

Drive geometry:

wheel diameter:
0.0763 m

track width:
0.379 m

encoder counts:
9750

---

# Software Architecture Observed

ROS node:

ardros/nodes/sammy.py

Purpose:
- serial communication
- odometry publishing
- TF broadcasting

Additional controllers:

arduino.py
mini_tractor.py

These contain:
- cmd_vel handling
- speed controller initialization
- PID configuration

---

# Current Problem

Attempted recovery:

cp -a /media/bob/PI_ROOT/home/ubuntu/catkin_ws \
~/LegacyRobotRecovery/Recovered_Files/

Result:

Input/output error

The filesystem is no longer reliably readable.

---

# Current Decision

STOP ACTIVE RECOVERY.

Preserve evidence first.

Do not:
- repair filesystem
- modify files
- run ROS builds
- alter NanoBot repositories
- copy damaged data repeatedly

---

# Next Actions

1. Verify USB image health.
2. Make a sector-level image if possible.
3. Work only from copies.
4. Preserve recovered documentation.
5. Store this report separately.

---

# Separation Rule

LegacyRobotRecovery is independent from:

~/NanoBot

No shared repositories.
No shared documentation.
No shared Syncthing folders.
No shared Obsidian vault.
