fetch\_moveit\_melodic
======================
The purpose of this package is to use source version `MoveIt!` with `fetch_gazebo` in ROS melodic.

## Install
```bash
cd ~
mkdir -p fetch_moveit_ws/src
cd fetch_moveit_ws/src  # same directory as .rosinstall
git clone https://github.com/708yamaguchi/fetch_moveit_melodic.git
cp fetch_moveit_melodic/.rosinstall .rosinstall # you can use symbolic link
wstool update -t .
rosdep install --from-paths . --ignore-src -y -r
source /opt/ros/melodic/setup.bash
cd ../
catkin build fetch_moveit_melodic
source ~/fetch_moveit_ws/devel/setup.bash
```

## Use MoveIt! with fetch\_gazebo
```bash
source /opt/ros/melodic/setup.bash
source ~/fetch_moveit_ws/devel/setup.bash
roslaunch fetch_moveit_ws start.launch
```
Or individual execution like below:
```bash
source /opt/ros/melodic/setup.bash
source ~/fetch_moveit_ws/devel/setup.bash
# Terminal 1
roslaunch fetch_gazebo playground.launch
# Terminal 2
roslaunch fetch_moveit_config move_group.launch info:=true # launch only MoveIt!
# roslaunch fetch_gazebo_demo demo.launch # launch navigation, perception and Moveit!
# Terminal 3
cd ~/fetch_moveit_ws/src
rviz -d fetch_moveit_melodic/fetch_moveit_melodic.rviz
```
