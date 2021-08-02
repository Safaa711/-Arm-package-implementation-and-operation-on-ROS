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

sudo apt-get install ros-melodic-moveit

sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui

sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher

sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control

The last step, was to enter ther following line in the bashrc file:

source /home/safaa/catkin_ws/devel/setup.bash

Note: for inserting we use i, and for exiting we use Ctrl+o then Enter then Ctrl+x

source ~/.bashrc

7- Finally, I have Launched Rviz simulator with joint state publisher using the following command:

roslaunch robot_arm_pkg check_motors.launch

![image](https://user-images.githubusercontent.com/85526390/126322123-a0880615-69b5-407f-8dcb-cb1cc10dbdf4.png)

6- Then in a new terminal, I have controlled the arm in a real simulator called gazebo, using the following commands:

cd catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts

sudo chmod +x joint_states_to_gazebo.py

roslaunch robot_arm_pkg check_motors_gazebo.launch

Then I have typed in a new terminal the following command:

rosrun robot_arm_pkg joint_states_to_gazebo.py

![Screenshot from 2021-08-01 02-28-54](https://user-images.githubusercontent.com/85526390/127754691-24414f61-4e37-4c90-b885-3f8ec890a299.png)


7- Finally, to run the arm in Moveit, I have used the following command:

roslaunch moveit_pkg demo.launch

![Screenshot from 2021-08-02 19-29-57](https://user-images.githubusercontent.com/85526390/127901235-f7c1a13b-4457-4104-9715-a149e3bb478c.png)





