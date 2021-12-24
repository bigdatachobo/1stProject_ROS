# 1stProject_ROS
![flow chart](https://user-images.githubusercontent.com/61238033/147212101-818e5f6f-77fc-419c-ad1f-c0022275a7ad.png)

# JTS
## 프로젝트 경과
### 1. alias 설정
명령어 입력하는 시간 줄이기 위해 alias 설정함.

### Remote PC
```
alias robot="ssh ubuntu@192.168.0.45"
alias slam_gmapping='roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping'
alias slam_carto='roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=cartographer'
alias slam_karto='roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=karto'
alias mapsave='rosrun map_server map_saver -f ~/map'
alias joystick='roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch'
alias navigation='roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml'
alias gazebo_empty_world='roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch'
alias gazebo_turtle_world='roslaunch turtlebot3_gazebo turtlebot3_world.launch'
alias gazebo_house='roslaunch turtlebot3_gazebo turtlebot3_house.launch'
alias gazebo_simulation='roslaunch turtlebot3_gazebo turtlebot3_simulation.launch'
alias gazebo_rviz='roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch'
alias fake_turtle_node='roslaunch turtlebot3_fake turtlebot3_fake.launch'
alias pi_camera_calibration='roslaunch turtlebot3_autorace_camera intrinsic_camera_calibration.launch mode:=calibration'
```

### SBC
```
alias bringup='roslaunch turtlebot3_bringup turtlebot3_robot.launch'
alias pi_camera='roslaunch turtlebot3_autorace_camera raspberry_pi_camera_publish.launch'
```
### 2. SLAM
### Run SLAM Node
### Remote PC
```
# 터미널 1
$ roscore
```
### SBC
```
# 터미널 2
# robot
$ ssh pi@192.168.0.45

# bringup
$ roslaunch turtlebot3_bringup turtlebot3_robot.launch
```
### Remote PC
```
# 터미널 3
$ export TURTLEBOT3_MODEL=burger

# slam
$ roslaunch turtlebot3_slam turtlebot3_slam.launch
```
```
# 터미널 4
$ export TURTLEBOT3_MODEL=burger

# joystick
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
### map 저장
```
rosrun map_server map_saver -f ~/map
```

### 3. Navigation
### Run Navigation Node
### Remote PC
```
# 터미널 1
$ roscore
```
### SBC
```
# 터미널 2
# robot
$ ssh pi@192.168.0.45

# bringup
$ roslaunch turtlebot3_bringup turtlebot3_robot.launch
```

### Remote PC
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```

### navigation 사용법
### 시작점 설정
![2D Pose Estimate](https://emanual.robotis.com/assets/images/platform/turtlebot3/navigation/2d_pose_button.png)

### 목표점 설정
![2D Goal Setting](https://emanual.robotis.com/assets/images/platform/turtlebot3/navigation/2d_nav_goal_button.png)
![Example](https://emanual.robotis.com/assets/images/platform/turtlebot3/navigation/2d_nav_goal.png)

## 4.Simulation
## Gazebo Simulation
### 패키지 설치
```
$ cd ~/catkin_ws/src/
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```

### 시뮬레이션 3 종류
### 4-1-1 Empty World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```
### 4-1-2 TurtleBot3 World
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
### 4-1-3 TurtleBot3 House
```
$ export TURTLEBOT3_MODEL=waffle_pi
$ roslaunch turtlebot3_gazebo turtlebot3_house.launch
```

### 터틀봇3 작동
```
# joystick
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

## SLAM Simulation
### 시뮬레이션 시작
```
$ export TURTLEBOT3_MODEL=burger

# gazebo_world
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

### SLAM Node 시작
```
$ export TURTLEBOT3_MODEL=burger

# slam_gmapping
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```

### 조작부 Node 시작
```
$ export TURTLEBOT3_MODEL=burger

# joystick
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

### MAP 저장
```
$ rosrun map_server map_saver -f ~/map
```