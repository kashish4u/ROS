**Note**: *This repository contains programs and instructions around c++,python,ROS,Gazebo,URDF,RVIZ.*

## **Setup**

### Installation

    Install ROS2 from the official ROS website: [ROS Website](https://docs.ros.org/)

    Note: The instructions are clear and comprehensive. It is highly recommended to follow them.

### Visual Studio Plugins [*Recommended*]

    + ROS by microsoft
    + ROS Snippets
    + XML by RedHat
    + XML tools by Josh Johnson
    + ROS Snippets by Liews Wuttipat

#

### Starting Setup

    1. Create Workspace folder: mkdir ros2_ws
    2. Create src folder inside workspace folder: mkdir ros2_ws/src
    3. Create python package inside the src: 
                                            cd ros2_ws/src
                                            ros2 pkg create "package_name"
    4. Build the first package in workspace: 
                                            cd ros2_ws
                                            colcon build
    Note:   To build all packages: colcon build
            To build single package: colcon build --packages-select package name

## **ROS2 Framework**

### Important Details

### WorkSpace Structure

```
# This is the recommended hierarchy for ROS2 C++ package.
# Remember to replace my_robot with the name you want and put it in lowercase.

../ros2_ws/src/my_robot
                        package.xml
                        CMakeLists.txt
                        setup.py
                        /urdf
                        /meshes
                        /materials
                        /cad
                        /config
                        /launch
                        /src
```

### **ROS2 Elements**

#### *Packages*

#### *Colcon*

#### *Nodes*

#### *Topic*

#### *Publisher*

#### *Client*

#### *Services*

#### *Actions*

#

## **URDF :**

### **Link**

    Specifications:
<center>
<div style="width: 50%; height: 10%">

![Link](img/link.png "ROS2 Link")
</div>
</center>

### **Joint**

    Specifications:
<center>
<div style="width: 50%; height: 10%">

![Joint](img/joint.png "ROS2 Joint")
</div>
</center>

**Running URDF files:**

```
Example:
ros2 launch urdf_tutorial display.launch.py model:=src/ros_navigation/urdf/01-myfirst.urdf
ros2 launch urdf_tutorial display.launch.py model:=`ros2 pkg prefix --share urdf_tutorial`/urdf/01-myfirst.urdf
This does three things:
Loads the specified model and saves it as a parameter
Runs nodes to publish sensor_msgs/msg/JointState and transforms.
Starts Rviz with a configuration file

Collision:
 Mass and Inertia
 If unsure what to put, a matrix with ixx/iyy/izz=1e-3 or smaller is often a reasonable default for a mid-sized link (it corresponds to a box of 0.1 m side length with a mass of 0.6 kg). The identity matrix is a particularly bad choice, since it is often much too high (it corresponds to a box of 0.1 m side length with a mass of 600 kg!).

```

#

## **Gazebo**

### **Important**

```
There are alot of examples on web around ROS1.

Please refer to run things on ROS2: <https://github.com/ros-simulation/gazebo_ros_pkgs/wiki/ROS-2-Migration:-Spawn-and-delete>

```

### Steps to Launch Model in Gazebo

```

1. Publish ROS structure via Launch files
2. Spawn the URDF model via Launch File to Gazebo
3. Make sure to Connect Gazebo services and ROS nodes via URDF.

```

### Tips

    1. Make sure Inertia in URDF is following the basic law of physics.
    2. Make sure to define the collision tags in URDF.
    3. Make sure to add the publisher for each joint to be able to use in your algorithm.
