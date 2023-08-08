# Installing-Robot-Arm-Packages-in-ROS
Follow these step-by-step instructions for a smooth installation process of the Robot Operating System (ROS Noetic version 1.16.0) and packages for a robot arm.
### 1. Create and Configure the Virtual Machine:
- VirtualBox is a popular virtualization software that enables you to run virtual operating systems on your computer. Begin by creating a virtual machine (VM) to host Ubuntu 20.04 and ROS [To install use this link](https://www.virtualbox.org/wiki/Downloads).
- Open VirtualBox and create a new VM:
  - Name: (e.g., Ros2023-VM)
  - Type: Linux
  - Version: Ubuntu (64-bit)
  - Memory: Allocate an appropriate amount of RAM (e.g., 2048 MB)
  - Hard disk: Create a virtual hard disk now (VDI)
  - Storage: Choose a suitable size for the virtual hard disk (e.g., 20 GB)
- After creating the VM, access its settings and make the following adjustments:
  - In the "System" section, allocate sufficient CPU cores and adjust the display settings as needed.
  - In the "Network" section, configure the network adapter to use "Bridged Adapter" for enhanced connectivity.
### 2. Install Ubuntu 20.04 on the VM:
-  Download the Ubuntu 20.04 from the official Ubuntu website [This link](https://releases.ubuntu.com/20.04/).
- Launch the Ros2023-VM in VirtualBox and initiate the installation process:
  - Attach the downloaded Ubuntu ISO to the VM's virtual optical drive.
  - Follow the on-screen instructions to install Ubuntu 20.04 within the virtual machine.
- This action establishes a virtual environment that allows you to proceed with the ROS installation and setup.

### 3. Running Commands in Terminal on Ubuntu :
Launch a terminal in Ubuntu and execute the following commands:

3.1 Update and Upgrade Ubuntu:
```
sudo apt update
sudo apt upgrade
```
3.2 Install ROS Noetic

  3.2.1 Set up sources and keys for ROS:
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl  # Install curl if not already installed
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
  3.2.2 Install ROS Noetic Desktop Full:
```
sudo apt update
sudo apt install ros-noetic-desktop-full
```
3.3 Initialize rosdep and Update:
```
sudo apt install python3-rosdep
sudo rosdep init
rosdep update
```
3.4 Environment Setup:
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
3.5 Install Additional Dependencies:

```
sudo apt install python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
3.6 Create a Catkin Workspace:
```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
```
3.7 Clone the Arduino Robot Arm Repository:
```
cd ~/catkin_ws/src
git clone https://github.com/smart-methods/arduino_robot_arm.git
```

3.8 Install Package Dependencies and Build:
```
cd ~/catkin_ws
rosdep install --from-paths src --ignore-src -r -y
catkin_make
```
3.9 Install MoveIt! and Additional Packages:

```
sudo apt-get install ros-noetic-moveit
sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
sudo apt-get install ros-noetic-gazebo-ros-control ros-noetic-ros-controllers
```
3.10 Update Environment Setup:
```
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

3.11 Launch the Robot Arm Demo:
```
roslaunch robot_arm_pkg check_motors.launch
```

![image1](https://github.com/LatifahAbuhamamah/Installing-Robot-Arm-Packages-in-ROS/blob/main/Robot%20Arm.jpeg)
![Robot Arm](https://github.com/LatifahAbuhamamah/Installing-Robot-Arm-Packages-in-ROS/assets/139233344/6ffaa860-01ed-4b85-aea9-d00424fc5dba)






