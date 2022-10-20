Updated Readme file.

1.Installing turtle.

Muhammadyusuf@ubuntu:~$ sudo apt update
Hit:1 http://packages.microsoft.com/repos/code stable InRelease
Hit:2 http://packages.ros.org/ros/ubuntu focal InRelease                        
Hit:3 http://us.archive.ubuntu.com/ubuntu focal InRelease                       
Hit:4 http://packages.ros.org/ros2/ubuntu focal InRelease                       
Hit:5 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease               
Get:6 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:8 http://archive.canonical.com/ubuntu focal InRelease                
Fetched 222 kB in 5s (43.1 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
26 packages can be upgraded. Run 'apt list --upgradable' to see them.

Muhammadyusuf@ubuntu:~$ sudo apt install ros-foxy-turtlesim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ros-foxy-turtlesim is already the newest version (1.2.5-1focal.20220209.151154).
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.

Muhammadyusuf@ubuntu:~$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~$ ros2 pkg executables turtlesim
turtlesim draw_square
turtlesim mimic
turtlesim turtle_teleop_key
turtlesim turtlesim_node
