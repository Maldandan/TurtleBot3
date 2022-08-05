# TurtleBot3
obstacle avoiding and SLAM mapping with TurtleBot3 using Rviz and Gazebo

## ROS
If you don't have you ROS ready, you can follow the installation guide I have made in my other repository [here](https://github.com/Maldandan/Installing-ROS)

## Rviz, Gazebo and Moveit
If its your first time working with simulations, chances are you don't have Rviz nor Gazebo installed.
Follow these guides to have everything prepared:

### Moveit
**Follow this** [Guide](http://docs.ros.org/en/melodic/api/moveit_tutorials/html/index.html)

### Rviz
**Follow this** [Guide](https://installati.one/ubuntu/20.04/rviz/)

### Gazebo
**Follow this** [Guide](https://classic.gazebosim.org/tutorials?tut=ros_installing&cat=connect_ros)

## TurtleBot3
Let’s install the TurtleBot3 simulator now.

Open a terminal window and install the dependent packages. **Enter the following commands**
```
cd ~/catkin_ws/src/
```
```
git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
```
```
git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
```
```
cd ~/catkin_ws && catkin_make
```

Before starting TurtleBot3, you must decide which of the three models—Burger, Waffle, and Waffle Pi—you wish to employ. To add this setting, **enter the following command to open the bashrc file:**
```
gedit ~/.bashrc
```
**Add this line at the bottom of the file:**
export TURTLEBOT3_MODEL=burger

![49-update-bash-settingsJPG](https://user-images.githubusercontent.com/109004035/183121631-90ba4188-3712-4409-a0f5-307e847c13fc.jpg)

**Close the file after saving it.**

Reload.bashrc right away to avoid having to log out and back in.

```
source ~/.bashrc
```
**Now, we need to download the TurtleBot3 simulation files.**
```
cd ~/catkin_ws/src/
```
```
git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
```
```
cd ~/catkin_ws && catkin_make
```
### Simulate TurtleBot3 Using RViz
Let's start the TurtleBot3 simulator using RViz now that it has been installed. **In the terminal window, enter the following command:**
```
roslaunch turtlebot3_fake turtlebot3_fake.launch
```

![Screenshot 2022-08-05 194540](https://user-images.githubusercontent.com/109004035/183123648-937c3be1-7ac0-459c-9bdc-2f2668f127c6.jpg)

**If you want to move TurtleBot3 around the screen**
 open a new terminal window, and type the following command:

```
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

```
The keys listed can be used to direct your TurtleBot's movement once you click the terminal window (e.g. press W key to move forward, X key to move backward and S to stop).

![Screenshot 2022-08-05 194644](https://user-images.githubusercontent.com/109004035/183123693-cee9068d-8e27-43c6-9770-ff10aa5e78b8.jpg)

### Simulate TurtleBot3 Using Gazebo
**Now let's run the TurtleBot3 simulation using Gazebo**.

Let's start by launching **TurtleBot3 in a blank space**. Fill in these commands:

```
roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```

![Screenshot 2022-08-05 195105](https://user-images.githubusercontent.com/109004035/183124324-2949e00b-3752-4690-aa72-2b944c60b163.jpg)

### How to Change the Simulation Environment for TurtleBot3

Let's examine our TurtleBot3 in a new setting. A lot of SLAM and navigation algorithm testing takes place in this area. The challenge of a robot creating or updating a map of an uncharted area while concurrently monitoring its location inside is known as simultaneous localization and mapping, or SLAM.

**Type into a new terminal window:**
```
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

![Screenshot 2022-08-05 195544](https://user-images.githubusercontent.com/109004035/183125216-6d0d5684-242f-47a9-901a-86128c84412b.jpg)

![Screenshot 2022-08-05 195630](https://user-images.githubusercontent.com/109004035/183125408-eebbc395-5548-4b98-8399-71beae430c97.jpg)

**We can also simulate TurtleBot3 inside a house**. 
Type this command and wait a few minutes for the environment to load. Type into a new terminal window:

```
roslaunch turtlebot3_gazebo turtlebot3_house.launch
```

![Screenshot 2022-08-05 200324](https://user-images.githubusercontent.com/109004035/183126206-555519f9-0055-415d-bd17-c220a83ea96c.jpg)

**To move the TurtleBot with your keyboard**, use this command in another terminal tab:
```
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
### Autonomous Navigation and Obstacle Avoidance With TurtleBot3

Let's now integrate **TurtleBot3's ability to avoid obstacles**. The objective is to make TurtleBot3 move about a space on its own while avoiding obstructions.

**Open a new terminal and type:**
```
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
**In another terminal window type:**

```
roslaunch turtlebot3_gazebo turtlebot3_simulation.launch
```
witness the TurtleBot3 exploring the environment on its own while dodging obstacles.

![Screenshot 2022-08-05 200803](https://user-images.githubusercontent.com/109004035/183127032-5f5ddf5c-0394-43d2-bccc-83b81df1db3f.jpg)
![Screenshot 2022-08-05 200904](https://user-images.githubusercontent.com/109004035/183127051-58f24dfe-8b7a-4601-8aeb-9d28d4642867.jpg)

### Simulating SLAM With TurtleBot3

Let's see how TurtleBot3 may be used to replicate SLAM.
Simultaneous localization and mapping (SLAM), is the challenge of a robot creating or updating a map of an uncharted area while simultaneously maintaining awareness of its location inside that environment.

**In a new terminal window, install the SLAM module.**
```
sudo apt install ros-melodic-slam-gmapping
```
**Start Gazebo in a new terminal window.**

```
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
**Start SLAM in a new terminal tab.**

```
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

```
**Start autonomous navigation in a new terminal tab:**

```
roslaunch turtlebot3_gazebo turtlebot3_simulation.launch
```
Watch the robot create a map of the environment as it autonomously moves from place to place!

![Screenshot 2022-08-05 201416](https://user-images.githubusercontent.com/109004035/183128365-52ad7cae-cf8a-47c4-90e8-008368315c39.jpg)
![Screenshot 2022-08-05 201527](https://user-images.githubusercontent.com/109004035/183128372-425e4ea9-9012-4b4b-9b91-910c76ee4127.jpg)
![Screenshot 2022-08-05 201740](https://user-images.githubusercontent.com/109004035/183128396-b0dded54-f0d5-4304-90ec-ed1f68a0181b.jpg)

And that's all about it! you can experiment and navigate between Automation and controlling the Turtlebot3 using SLAM Mapping !
Enjoy! :)
