# bot_ws
Workshop Instructions

FOR THE FIRST TIME ROS2 users, source the ROS2 with your own ROS2 distro name. Here, since we have installed ROS2 Humble, we are using "humble" in the echo command.

```
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
> [!NOTE]
> Always remember to build the workspace whenever you make changes in the code. It is assumed that, this is done everytime the file structure or the code is changes or copied.

*** Go into your Workspace Folder first and then build i.e. use the below command ***

```
colcon build
```

Now start with the creation of workspace. To proceed with this we will first will make a folder with "bot_ws" as its name. Then create a "src" folder in it.

```
cd
mkdir bot_ws
cd bot_ws
mkdir src
cd src
```

Now we will create a ros2 package folder named as "bot_description".

```
ros2 pkg create --build-type ament_cmake bot_description
```

Now to have a basic file structure ready to be used in the VS Code, follow the below commands or steps to build your workspace for the first time.

```
cd ..
colcon build
```

Now open up the VS code and make the file structure same as given in the repository.

When the fresh terminal is opened up for running the simulation or Rviz, first source the workspace using the below command.

```
cd
source bot_ws/install/setup.bash
```

After having the launch files of rviz ready in your bot_ws/src, use the following command to launch the bot with Rviz2.

```
ros2 launch bot_description display.launch.py
```

When launching the robot in simulaiton or Gazebo World use the following.

```
ros2 launch bot_description gazebo.launch.py
```

After testing the spawning of the robot into the Gazebo Sim, now we will make a controller package.

```
cd
cd bot_ws/src/
ros2 pkg create --build-type ament_cmake bot_controller
cd ..
colcon build
```

After comparing and matching with the repository files in the controller package. Now run both the gazebo and the controller in seperate terminal tabs or windows.
```
ros2 launch bot_description gazebo.launch.py
```
```
ros2 launch bot_controller controller.launch.py
```

Then to combine the above commands (i.e. to Run the robot in one command) we will make a bringup package.

```
cd
cd bot_ws/src/
ros2 pkg create --build-type ament_cmake bot_bringup
cd ..
colcon build
```

Copy the file structure from the repository, and now we will run the whole simulation with just one launch file.
```
ros2 launch bot_bringup simulation.launch.py
```

