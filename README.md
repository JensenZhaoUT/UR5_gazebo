### Detailed guidance of reproducing this repository
#### 1. image selection:
 ```
$ osrf/ros:kinetic-desktop-full
 ```
#### 2. build the container
 ```
$ docker pull osrf/ros:kinetic-desktop-full
$ docker run -it --name ur5_gazebo -e DISPLAY=host.docker.internal:0.0 -it osrf/ros:kinetic-desktop-full bash
 ```
#### 3. Run the xlaunch
###### set the port to 0 in order to match the display port number we used for the container
#### 4. Clone the repository
 ```
$ source /opt/ros/kinetic/setup.bash
$ cd catkin_ws/src
$ git clone https://github.com/JensenZhaoUT/UR5_gazebo.git
$ cd ..
$ catkin_make
$ source devel/setup.bash
 ```
#### 5. roslaunch
 ```
$ roslaunch ur5_notebook initialize.launch
 ```
#### 6. Potential Issues
##### 6.1 CMake Error(moveit_core)
 ```
$ sudo apt-get update
$ sudo apt-get install ros-kinetic-moveit
$ roslaunch moveit_setup_assistant setup_assistant.launch
 ```

1. Click on the "Create New MoveIt Configuration Package" button,click the "Browse" button, select the xacro file you created in the Previous Chapter, and click on the "Load Files" button.
PATH: /src/universal_robot/ur_description/urdf/ur5.urdf.xacro

2. Go to the "Self-Collisions" tab, and click on the "Regenerate Collision Matrix" button.

3. move to the "Virtual Joints" tab. Here, you will define a virtual joint for the base of the robot. Click the "Add Virtual Joint" button, and set the name of this joint to FixedBase, and the parent to world.

4. open the "Planning Groups" tab and click the "Add Group" button. Now, you will create a new group called manipulator, which uses the KDLKinematicsPlugin.

3. Move Group Python InterFace Tutorial[`Official tutorial`](http://docs.ros.org/indigo/api/moveit_tutorials/html/doc/pr2_tutorials/planning/scripts/doc/move_group_python_interface_tutorial.html)

##### 6.2 Missing ur_description or missing ur5
 ```
$ cd catkin_ws/src
$ git clone -b kinetic-devel https://github.com/ros-industrial/universal_robot.git
$ cd ..
$ rosdep install --from-paths src --ignore-src --rosdistro kinetic
$ catkin_make
$ source devel/setup.bash
 ```
