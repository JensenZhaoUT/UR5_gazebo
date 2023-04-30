### Detailed guidance of reproducing this repository
#### 1. image selection:
osrf: ros:kinetic-desktop-full
#### 2. build the container
docker pull osrf: ros:kinetic-desktop-full
docker run -it --name ur5_gazebo -e DISPLAY=host.docker.internal:0.0 -it osrf: ros:kinetic-desktop-full bash
#### 3. Run the xlaunch
##### change the port to 0 in order to match the display port number we used for the container
#### 4. Clone the repository
source /opt/ros/kinetic/setup.bash
cd catkin_ws/src
git clone https://github.com/lihuang3/ur5_ROS-Gazebo.git
source devel/setup.bash
#### 5. roslaunch
roslaunch ur5_notebook initialize.launch


