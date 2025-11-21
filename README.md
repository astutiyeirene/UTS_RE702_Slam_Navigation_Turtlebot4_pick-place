![WhatsApp Image 2025-11-20 at 00 07 43 (1)](https://github.com/user-attachments/assets/0c985190-ef89-468e-be77-1ba27dc3b11f)# UTS_RE702_Slam_Navigation_Turtlebot4(pick-place)
"Integrasi SLAM, map generation, dan autonomous navigation pada TurtleBot4 untuk tugas UTS. Robot melakukan misi pick &amp; place dari Ruang 203 ke Lobby BRAIL dengan indikator buzzer ."

## case study

The robot is tasked with delivering goods from:
- **Room 203 → Lobby BRAIL**  
  (2nd Floor, Main Building, Batam State Polytechnic)

The robot must be able to:
1. **Localization** using AMCL  
2. **Mapping** using SLAM (gmapping / slam toolbox)  
3. **Autonomous navigation** using Nav2  
4. **Detecting pick & place locations**  
5. **Activating the buzzer as a mission indicator**
6. 
### 🔔 Buzzer Indicator
- When the robot reaches the **pick location (Room 203)** → sounds **once**
- When the robot reaches the **place location (BRAIL Lobby)** → sounds **Twice**

## 🧠 System Architecture
1. **SLAM / Map Generation**
   - Robot explores the area
   - Map is saved to `.pgm` and `.yaml` files

2. **Localization (AMCL)**
   - Determines the robot's position on a static map

3. **Navigation (Nav2)**
   - Runs global planner and local planner
   - Generates a safe path to the target

4. **Pick & Place Logic**
   - Navigates to Room 203 (Pick)
   - Buzzer sounds **1x**
   - Navigates to BRAIL Lobby (Place)
   - Buzzer sounds **2x**
## how to connect from pc to turtle
# via ethernet
ssh ubuntu@192.168.185.3
![gambar0](https://github.com/user-attachments/assets/aa54d734-04a1-440c-b777-af0b2f43804b)

## ▶️ How to Run a Project
1. Preparation Environment
cd ~/kelompok4b_uts
source /opt/ros/humble/setup.bash
2. Build Package ROS 2
# Buat package baru
ros2 pkg create --build-type ament_cmake --node-name nav_kel4b nav_kel4b --dependencies rclcpp nav2_msgs rclcpp_action tf2

# Build package
colcon build

# Source workspace
source install/setup.bash
![gambar1](https://github.com/user-attachments/assets/fa9571a7-0ba0-4006-a2f7-5bc974266387)

3. Launch Visualisasi (RViz)
ros2 launch turtlebot4_viz view_robot.launch.py
![gambar2](https://github.com/user-attachments/assets/24642382-fde8-4168-842c-b6ff7831e6f7)

5. Launch Navigasi dengan Keyboard Control
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -p stamped:=true
7. Launch Sistem Navigasi Nav2
# For localization
ros2 launch nav_kel4b nav_kel4b
![gambarr](https://github.com/user-attachments/assets/3bd5b379-1c8a-4806-99f1-e02a3a955c09)
![gambar4](https://github.com/user-attachments/assets/a9239d74-fa22-450a-940a-fab1a201961a)

6. Run the Pick & Place Mission
ros2 launch nav_kel4b pickplace_launch.py

## Video Demonstrasi
https://youtu.be/vy7ioHENwRQ. 
