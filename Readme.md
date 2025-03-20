---

# **Dynamic Mapping and Path Planning for Autonomous Navigation Using ROS 2**  

The purpose of this project is to design, simulate, and evaluate an autonomous navigation system capable of dynamic
mapping and path planning. Using ROS 2, this project will simulate a robot navigating through a complex environment
while dynamically mapping the surroundings and calculating optimal paths. The project emphasizes the integration of
mapping, path planning, and cost analysis to achieve efficient and obstacle-free navigation.

---

## **Setup Instructions**

### Environment Setup

### Make sure you have a locale which supports UTF-8. If you are in a minimal environment (such as a docker container), the locale may be something minimal like POSIX. We test with the following settings. However, it should be fine if you’re using a different UTF-8 supported locale.

```bash
locale  # check for UTF-8
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
locale  # verify settings
```

### Enable required repositories
You will need to add the ROS 2 apt repository to your system.

First ensure that the Ubuntu Universe repository is enabled.

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```

### Now add the ROS 2 GPG key with apt.

```bash
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

### Then add the repository to your sources list.

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

### Install development tools

```bash
sudo apt update && sudo apt install ros-dev-tools
```

## Install ROS 2
### Update your apt repository caches after setting up the repositories.

```bash
sudo apt update
```

### ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.

```bash
sudo apt upgrade
```

Desktop Install (Recommended): ROS, RViz, demos, tutorials.

```bash
sudo apt install ros-jazzy-desktop
```

## Clone the repository

```bash
mkdir -p /ros2_ws/Autonomous-Mobile-Robot/src;
cd ~/ros2_ws/Autonomous-Mobile-Robot/src;
git clone https://github.com/saleque143/Dynamic-Mapping-and-Path-Planning-for-Autonomous-Navigation-Using-ROS2.git
```

## Install Dependencies
- Install the required by running these command

```bash
sudo apt-get install ros-jazzy-joint-state-publisher
sudo apt-get install ros-jazzy-joint-state-publisher-gui
sudo apt-get install ros-jazzy-ros-gz
sudo apt-get install ros-jazzy-ros-gz-bridge
sudo apt-get install ros-jazzy-gz-ros2-control
sudo apt-get install ros-jazzy-ros2-control
sudo apt-get install ros-jazzy-ros2-controllers
sudo apt-get install ros-slam-toolbox
sudo apt-get install ros-jazzy-navigation2
```

### **1. Build the Workspace**  
Open a terminal and navigate to the root directory of the workspace:  

```bash
cd ~/ros2_ws/Autonomous-Mobile-Robot/;
colcon build
```

---

### **2. Launch the Gazebo Simulation**  
Open a **new terminal**, navigate to the project root, and launch the simulation:  

```bash
cd ~/ros2_ws/Autonomous-Mobile-Robot/;
. install/setup.bash;
ros2 launch mobile_robot_bringup mobile_robot_sim.launch.py
```

---

### **3. Launch Navigation**  
Open **another terminal**, navigate to the root folder, and launch the navigation stack:  

```bash
cd ~/ros2_ws/Autonomous-Mobile-Robot/;
. install/setup.bash;
ros2 launch mobile_robot_bringup navigation.launch.py
```

---

## **Running the Simulation in RViz2**  

Once all components have started **without errors**, follow these steps:

1. **Set the Robot’s Initial Pose**  
   - In the **RViz2** window, click on the **"2D Pose Estimate"** button (top toolbar).  
   - Click and drag the mouse at the **robot's origin** (center of the white robot).  
   - Ensure the arrow points in the correct orientation.  

2. **Send a Navigation Goal**  
   - Click the **"2D Goal Pose"** button in RViz2.  
   - Click on the desired destination for the robot.  
   - The robot will autonomously move toward the target.  

---

## **Additional Notes**  
- Ensure ROS 2 (Humble or later) and all dependencies are properly installed.  
- If you encounter missing dependencies, install them using:  
  ```bash
  rosdep install --from-paths src --ignore-src -r -y
  ```  
   - If Gazebo or RViz2 does not launch properly, try **sourcing the workspace** again:  
  ```bash
  source install/setup.bash
  ```

---
