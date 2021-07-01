# Create-and-save-map-using-Turtlebot3-with-SLAM
This repository shows the steps taken to use Turtlebot3 with SLAM approach to create and save a map.

These packages were tested under ROS Melodic and Ubuntu 18.04.

# Dependencies

-Make sure you already have a running VM with ubuntu 18.04 OS, and already installed ROS Melodic inside it.

-type in the commands down below in the terminal


**1-Install TurtleBot3 Packages**
```
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3
 ```
**2-Set TurtleBot3 Model Name**
  - In case of TurtleBot3 Burger
  ```
$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
```
  - In case of TurtleBot3 Waffle Pi
 ```
$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
```
**Gazebo Simulation**



  **1- Install Simulation Package**
  ```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```
  **2- Launch Simulation World**
  
  
Three simulation environments are prepared for TurtleBot3. Please select one of these environments to launch Gazebo.
    
1-Empty World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch    
```
2-TurtleBot3 World
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

 3- TurtleBot3 House
  ```
$ export TURTLEBOT3_MODEL=waffle_pi
$ roslaunch turtlebot3_gazebo turtlebot3_house.launch
```
   **3- Operate TurtleBot3**
   ```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
**SLAM Simulation**


For every step Open a new terminal from Remote PC with Ctrl + Alt + T 

 **1- Launch Simulation World**
   ```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
  ```
 **2-	Run SLAM Node**
  ```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
  **3-	Run Teleoperation Node**
  ```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
  **4-	Save Map**
  ```
$ rosrun map_server map_saver -f ~/map
```

**Results**
![4](https://user-images.githubusercontent.com/86648269/124053310-b11dcf80-da28-11eb-8757-52785c93c184.png)


![5](https://user-images.githubusercontent.com/86648269/124053323-b5e28380-da28-11eb-9452-1ad56ccdfbcf.png)


![6](https://user-images.githubusercontent.com/86648269/124053352-c0048200-da28-11eb-8ac8-06189d533800.png)


![7](https://user-images.githubusercontent.com/86648269/124053361-c2ff7280-da28-11eb-835f-e39bc4b843e5.png)


![8](https://user-images.githubusercontent.com/86648269/124064380-4c20a480-da3d-11eb-92d3-2fa777dcfbd1.png)







