Steps:

1- First, I have downloaded on my windows 10 Virtual Box version 6.1 from Oracle: https://www.virtualbox.org/wiki/Downloads 

2- Then I have created a virtual machine.

3- After that, I have installed Ubuntu 18.04 from https://releases.ubuntu.com/18.04/

4- In the terminal, I have launched Robot Operating System melodic using the following commands:

sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

sudo apt-get update

sudo apt-get install ros-melodic-desktop-full

apt-cache search ros-melodic

echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc

sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential

sudo apt install python-rosdep

sudo rosdep init

rosdep update

5- Then, I have installed a work space that contains ROS packages, using the following commands:

sudo apt-get install ros-melodic-catkin

mkdir -p ~/catkin_ws/src

cd ~/catkin_ws/

catkin_make

cd ~/catkin_ws/src

6- After that, I have import the package that contains the robot arm usnig git:

git clone https://github.com/smart-methods/arduino_robot_arm.git 

cd ~/catkin_ws

rosdep install --from-paths src --ignore-src -r -y

7- Lunch Rviz simulator with joint state publisher.

![image](https://user-images.githubusercontent.com/85526390/126322123-a0880615-69b5-407f-8dcb-cb1cc10dbdf4.png)
