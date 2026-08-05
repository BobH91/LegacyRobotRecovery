# Sammy Image Extraction Plan

Goal:
Recover readable files from sammy_backup_20191212.

Rules:

- Original image remains unchanged.
- No read-write mounts.
- No filesystem repair on original image.
- All recovered files go into LegacyRobotRecovery.
- Recovery failures are logged separately.

Target:

Recover:
- /home/ubuntu/catkin_ws
- ROS packages
- robot source code
- configuration files

Method:

1. Mount partitions read-only.
2. Inspect filesystem.
3. Copy readable files.
4. Record errors.
5. Verify recovered content.

