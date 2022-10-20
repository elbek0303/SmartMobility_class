#week 4

1. Installing turtlesim

```
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
```
#Starting and using 



```
Muhammadyusuf@ubuntu:~$ source /opt/ros/foxy/setup.sh
OS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~$ ros2 run turtlesim turtlesim_node
[INFO] [1663641213.835052574] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1663641213.843843646] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
[INFO] [1663641652.042988255] [turtlesim]: Spawning turtle [turtle2] at x=[1.000000], y=[1.000000], theta=[0.000000]
[WARN] [1663641958.871626326] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.941882, y=11.099703])
[WARN] [1663641958.886837813] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.933865, y=11.119869])
[WARN] [1663641958.903235761] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.925849, y=11.119869])
[WARN] [1663641958.919503554] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.917833, y=11.119869])
[WARN] [1663641958.935489939] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.909817, y=11.119869])
[WARN] [1663641958.950991549] [turtlesim]: Oh no! I hit the wall! (Clamping from [x=3.901801, y=11.11.......
....skipped.........

Muhammadyusuf@ubuntu:~$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~$ ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
```
#Nodes,services, topics, and actions
```
Muhammadyusuf@ubuntu:~$ ros2 node list
/teleop_turtle
Muhammadyusuf@ubuntu:~$ ros2 topic list
/parameter_events
/rosout
/turtle1/cmd_vel
Muhammadyusuf@ubuntu:~$ ros2 service list
/teleop_turtle/describe_parameters
/teleop_turtle/get_parameter_types
/teleop_turtle/get_parameters
/teleop_turtle/list_parameters
/teleop_turtle/set_parameters
/teleop_turtle/set_parameters_atomically
Muhammadyusuf@ubuntu:~$ ros2 action list
/turtle1/rotate_absolute
Muhammadyusuf@ubuntu:~$ 
```


#Using rqt function


#remapping
```
Muhammadyusuf@ubuntu:~$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~$ ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
```

## Week 5 activity
  #### 1.PACKAGE CREATION
```
Muhammadyusuf@ubuntu:~$ mkdir ros2_ws
Muhammadyusuf@ubuntu:~$ cd ros2ws/
Muhammadyusuf@ubuntu:~/ros2_ws$ ls
Muhammadyusuf@ubuntu:~/ros2_ws$ mkdir src
Muhammadyusuf@ubuntu:~/ros2_ws$ cd src/
Muhammadyusuf@ubuntu:~/ros2_ws/src$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.

Muhammadyusuf@ubuntu:~/ros2_ws/src$ ros2 pkg create --build-type ament_cmake --node-name my_node my_package
going to create a new package
package name: my_package
destination directory: /home/user/ros2_ws/src
package format: 3
version: 0.0.0
description: TODO: Package description
maintainer: ['<name> <email>']
licenses: ['TODO: License declaration']
build type: ament_cmake
dependencies: []
node_name: my_node
creating folder ./my_package
creating ./my_package/package.xml
creating source and include folder
creating folder ./my_package/src
creating folder ./my_package/include/my_package
creating ./my_package/CMakeLists.txt
creating ./my_package/src/my_node.cpp

Muhammadyusuf@ubuntu:~/colcon build
Muhammadyusuf@ubuntu:~/ros2_ws$ colcon build --packages-select my_package
Starting >>> my_package
Finished <<< my_package [4.24s]                     

Summary: 1 package finished [4.85s]

Muhammadyusuf@ubuntu:~/. install/setup.bash
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 run my_package my_node
hello world my_package package
Muhammadyusuf@ubuntu:~/ros2_ws/src/my_package$ ls
CMakeLists.txt  include  package.xml  src

%%% update CMakeLists.txt

<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>py_pubsub</name>
  <version>0.0.0</version>
  <description>Examples of minimal publisher/subscriber using rclpy</description>
  <maintainer email="khalilovasadbek27@gmail.com">Asadbek</maintainer>
  <license>Apache License 2.0</license>
  <exec_depend>rclpy</exec_depend>
  <exec_depend>std_msgs</exec_depend>

  <test_depend>ament_copyright</test_depend>
  <test_depend>ament_flake8</test_depend>
  <test_depend>ament_pep257</test_depend>
  <test_depend>python3-pytest</test_depend>

  <export>
    <build_type>ament_python</build_type>
  </export>
</package>

PUBLISHER AND SUBSCRIBER IN PYTHON


Muhammadyusuf@ubuntu:~/ros2_ws/src$ ros2 pkg create --build-type ament_python py_pubsub
going to create a new package
package name: py_pubsub
destination directory: /home/asadbek/ros2_ws/src
package format: 3
version: 0.0.0
description: TODO: Package description
maintainer: ['Muhammadyusuf <kobuljon1979@gmail.com>']
licenses: ['TODO: License declaration']
build type: ament_python
dependencies: []
creating folder ./py_pubsub
creating ./py_pubsub/package.xml
creating source folder
creating folder ./py_pubsub/py_pubsub
creating ./py_pubsub/setup.py
creating ./py_pubsub/setup.cfg
creating folder ./py_pubsub/resource
creating ./py_pubsub/resource/py_pubsub
creating ./py_pubsub/py_pubsub/__init__.py
creating folder ./py_pubsub/test
creating ./py_pubsub/test/test_copyright.py
creating ./py_pubsub/test/test_flake8.py
creating ./py_pubsub/test/test_pep257.py
Muhammadyusuf@ubuntu:~/ros2_ws/src$ cd py_pubsub/py_pubsub/
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ wget   <---------------- https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
--2022-09-29 14:52:18--  https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.110.133, 185.199.109.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.110.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1576 (1.5K) [text/plain]
Saving to: ‘publisher_member_function.py’

publisher_member_fun 100%[===================>]   1.54K  --.-KB/s    in 0.005s  

2022-09-29 14:17:20 (336 KB/s) - ‘publisher_member_function.py’ saved [1576/1576]

Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ ls
__init__.py  publisher_member_function.py
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ code publisher_member_function.py 

%%%%%% Examine the code and Add dependencies
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub$ ls
package.xml  py_pubsub  resource  setup.cfg  setup.py  test
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub$ code package.xml 
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub$ code setup.py 
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub$ code setup.cfg


WRITING SUBSCRIBTION NODE


Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ wget https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_subscriber/examples_rclpy_minimal_subscriber/subscriber_member_function.py
--2022-09-28 14:15:56--  https://raw.githubusercontent.com/ros2/examples/foxy/rclpy/topics/minimal_subscriber/examples_rclpy_minimal_subscriber/subscriber_member_function.py
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.110.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1469 (1.4K) [text/plain]
Saving to: ‘subscriber_member_function.py’
.....

Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ ls
__init__.py  publisher_member_function.py  subscriber_member_function.py

Muhammadyusuf@ubuntu:~/ros2_ws$ rosdep install -i --from-path src --rosdistro foxy -y
#All required rosdeps installed successfully

Muhammadyusuf@ubuntu:~/ros2_ws$ colcon build --packages-select py_pubsub
Starting >>> py_pubsub
Finished <<< py_pubsub [2.51s] 

Muhammadyusuf@ubuntu:~/ros2_ws$ . install/setup.bash
ROS_DISTRO was set to 'foxy' before. Please make sure that the environment does not mix paths from different distributions.
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 run py_pubsub talker
[INFO] [1664344782.588203197] [minimal_publisher]: Publishing: "Hello World: 0"
[INFO] [1664344783.051984102] [minimal_publisher]: Publishing: "Hello World: 1"
[INFO] [1664344783.551810507] [minimal_publisher]: Publishing: "Hello World: 2"
[INFO] [1664344784.052709914] [minimal_publisher]: Publishing: "Hello World: 3"
[INFO] [1664344784.552510784] [minimal_publisher]: Pu.....

Muhammadyusuf@ubuntu:~/ros2_ws$ . install/setup.bash
ROS_DISTRO was set to 'foxy' before. Please make sure that the environment does not mix paths from different distributions.
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 run py_pubsub listener
[INFO] [1664344794.599405944] [minimal_subscriber]: I heard: "Hello World: 24"
[INFO] [1664344795.052560275] [minimal_subscriber]: I heard: "Hello World: 25"
[INFO] [1664344795.552365233] [minimal_subscriber]: I heard: "Hello World: 26"
[INFO] [1664344796.052530783] [minimal_subscriber]: I heard: ......

```

```
#### 3. Writing a simple service and client using Python
##### Creating a package
```

```
Muhammadyusuf@ubuntu:~/ros2_ws/src$ ros2 pkg create --build-type ament_python py_srvcli --dependencies rclpy example_interfaces
going to create a new package
package name: py_srvcli
destination directory: /home/Muhammadyusuf/ros2_ws/src
package format: 3
version: 0.0.0
description: TODO: Package description
maintainer: ['Muhammadyusuf <kobuljon1979@gmail.com>']
licenses: ['TODO: License declaration']
build type: ament_python
dependencies: ['rclpy', 'example_interfaces']
creating folder ./py_srvcli
creating ./py_srvcli/package.xml
creating source folder
creating folder ./py_srvcli/py_srvcli
creating ./py_srvcli/setup.py
creating ./py_srvcli/setup.cfg
creating folder ./py_srvcli/resource
creating ./py_srvcli/resource/py_srvcli
creating ./py_srvcli/py_srvcli/__init__.py
creating folder ./py_srvcli/test
creating ./py_srvcli/test/test_copyright.py
creating ./py_srvcli/test/test_flake8.py
creating ./py_srvcli/test/test_pep257.py
Muhammadyusuf@ubuntu:~/ros2_ws/src$
```
##### Update package.xml and setup.py
```
%%% package.xml
<description>Python client server tutorial</description>
<maintainer email="kobuljon1979@email.com">Muhammadyusuf</maintainer>
<license>Apache License 2.0</license>
%%% setup.py
maintainer='Muhammadyusuf',
maintainer_email='khalilovasadbek27@email.com',
description='Python client server tutorial',
license='Apache License 2.0',
```

##### Write the service node, client node and add entry points
```


Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$ code package.xml
...opens Visual studio
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$ 
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$ code setup.py
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli/py_srvcli$ ls
client_member_function.py  __init__.py  service_member_function.py
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli/py_srvcli$ cd ..
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$ code setup.py
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$ 

```
#####  Building and running
```
Muhammadyusuf@ubuntu:~/ros2_ws$ rosdep install -i --from-path src --rosdistro foxy -y
WARNING: given --rosdistro foxy but ROS_DISTRO is "noetic". Ignoring environment.
#All required rosdeps installed successfully
Muhammadyusuf@ubuntu:~/ros2_ws$ colcon build --packages-select py_srvcli
Starting >>> py_srvcli
Finished <<< py_srvcli [2.61s]          

Summary: 1 package finished [3.14s]
Muhammadyusuf@ubuntu:~/ros2_ws$ 
%%% run the service node:
Muhammadyusuf@ubuntu:~/ros2_ws$ . install/setup.bash
Muhammadyusuf@ubuntu:~/ros2_ws$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 run py_srvcli service
[INFO] [1665454325.211773313] [minimal_service]: Incoming request
a: 4 b: 6
..
%%% Start the client node,
Muhammadyusuf@ubuntu:~/ros2_ws$ . install/setup.bash
Muhammadyusuf@ubuntu:~/ros2_ws$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusufk@ubuntu:~/ros2_ws$ ros2 run py_srvcli client 4 6
[INFO] [1665454325.250957140] [minimal_client_async]: Result of add_two_ints: for 4 + 6 = 10
Muhammadyusuf@ubuntu:~/ros2_ws$ 
```
#### 4. Creating custom msg and srv files
##### Creating a package and custom defitions (msg,srv, CMakeLists.txt and package.xml)
```
Muhammadyusuf@ubuntu:~/ros2_ws/src$ source /opt/ros/foxy/setup.sh
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~/ros2_ws/src$ ros2 pkg create --build-type ament_cmake tutorial_interfaces
going to create a new package
package name: tutorial_interfaces
destination directory: /home/asadbek/ros2_ws/src
package format: 3
version: 0.0.0
description: TODO: Package description
maintainer: ['Muhammadyusuf <kobuljon1979@gmail.com>']
licenses: ['TODO: License declaration']
build type: ament_cmake
dependencies: []
creating folder ./tutorial_interfaces
creating ./tutorial_interfaces/package.xml
creating source and include folder
creating folder .... %%skipped
Muhammadyusuf@ubuntu:~/ros2_ws/src$ cd tutorial_interfaces/
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ mkdir msg
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ mkdir srv
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ cd msg/
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces/msg$ code Num.msg
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces/msg$ ls
Num.msg
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces/msg$ code Sphere.msg
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces/msg$ cd ..
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ cd srv
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces/srv$ code AddThreeInts.srv
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces/srv$ ls
AddThreeInts.srv
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces/srv$ 

Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces/srv$ cd ..
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ ls
CMakeLists.txt  include  msg  package.xml  src  srv
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ code CMakeLists.txt
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ ls
CMakeLists.txt  include  msg  package.xml  src  srv
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ code package.xml 
Muhammadyusuf@ubuntu:~/ros2_ws/src/tutorial_interfaces$ cd ..
Muhammadyusuf@ubuntu:~/ros2_ws/src$
```
##### Build the tutorial_interfaces package and Confirm msg and srv creation
```
Muhammadyusuf@ubuntu:~/ros2_ws$ colcon build --packages-select tutorial_interfaces
Starting >>> tutorial_interfaces
Finished <<< tutorial_interfaces [25.5s]                       

Summary: 1 package finished [26.2s]
Muhammadyusuf@ubuntu:~/ros2_ws$ 

Muhammadyusuf@ubuntu:~/ros2_ws$ . install/setup.bash
ROS_DISTRO was set to 'noetic' before. Please make sure that the environment does not mix paths from different distributions.
Muhammadyusuf@ubuntu:~/ros2_ws$ source /opt/ros/foxy/setup.bash
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 interface show tutorial_interfaces/msg/Num
int64 num
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 interface show tutorial_interfaces/msg/Sphere
geometry_msgs/Point center
float64 radius
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 interface show tutorial_interfaces/srv/AddThreeInts
int64 a
int64 b
int64 c
---
int64 sum
Muhammadyusuf@ubuntu:~/ros2_ws$ 
```

##### testing Num.msg with pub/sub
```
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub$ cd py_pubsub/
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ ls
__init__.py  publisher_member_function.py  subscriber_member_function.py
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ code publisher_member_function.py 
...%%%% UPDATE SOME PARTS
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ code subscriber_member_function.py 
....%%%%% UPDATE SOME PARTS
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_pubsub/py_pubsub$ 

Muhammadyusuf@ubuntu:~/ros2_ws$ colcon build --packages-select py_pubsub
Starting >>> py_pubsub
Finished <<< py_pubsub [2.56s]          

Summary: 1 package finished [3.22s]
Muhammadyusuf@ubuntu:~/ros2_ws$
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 run py_pubsub talker
[INFO] [1665459164.361655668] [minimal_publisher]: Publishing: "0"
[INFO] [1665459166.298111030] [minimal_publisher]: Publishing: "4"
[INFO] [1665459166.800637375] [minimal_publisher]...skipped
Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 run py_pubsub listener
[INFO] [1665459416.413502702] [minimal_subscriber]: I heard: "15"
[INFO] [1665459417.842113339] [minimal_subscriber]: I heard: "18"
[INFO] [1665459418.339504899] [minimal_subscriber]:...skipped
```

##### Testing AddThreeINts.srv with service and client
```
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$ cd py_srvcli/
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli/py_srvcli$ ls
client_member_function.py  __init__.py  service_member_function.py
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli/py_srvcli$ code service_member_function.py 
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli/py_srvcli$ code client_member_function.py 
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli/py_srvcli$
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$ code package.xml 
Muhammadyusuf@ubuntu:~/ros2_ws/src/py_srvcli$ 

Muhammadyusuf@ubuntu:~/ros2_ws$ colcon build --packages-select py_srvcli
Starting >>> py_srvcli
Finished <<< py_srvcli [2.52s]          

Summary: 1 package finished [3.07s]
Muhammadyusuf@ubuntu:~/ros2_ws$

Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 run py_srvcli service
[INFO] [1665459784.262448801] [minimal_service]: Incoming request
a: 2 b: 3 c: 1

Muhammadyusuf@ubuntu:~/ros2_ws$ ros2 run py_srvcli client 2 3 1
[INFO] [1665459784.296955573] [minimal_client_async]: Result of add_three_ints: for 2 + 3 + 1 = 6
Muhammadyusuf@ubuntu:~/ros2_ws$ 
```

