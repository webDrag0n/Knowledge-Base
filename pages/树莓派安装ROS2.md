- #树莓派 #树莓派4B #ROS2
- ROS2官方声称的可以直接按照Ubuntu安装方法来安装是不行的
- ROS2 Docker还没有试过，可能可以
- 参考：https://forums.raspberrypi.com/viewtopic.php?t=361746
- ```bash
  sudo apt install -y git colcon python3-rosdep2 vcstool wget python3-flake8-docstrings python3-pip python3-pytest-cov python3-flake8-blind-except python3-flake8-builtins python3-flake8-class-newline python3-flake8-comprehensions python3-flake8-deprecated python3-flake8-import-order python3-flake8-quotes python3-pytest-repeat python3-pytest-rerunfailures python3-vcstools libx11-dev libxrandr-dev libasio-dev libtinyxml2-dev
  
  mkdir -p ~/ros2_iron/src
  
  cd ~/ros2_iron
  
  vcs import --input https://raw.githubusercontent.com/ros2/ros2/iron/ros2.repos src
  
  sudo rm /etc/ros/rosdep/sources.list.d/20-default.list
  
  sudo apt upgrade
  
  sudo rosdep init
  
  rosdep update
  
  rosdep install --from-paths src --ignore-src --rosdistro iron -y --skip-keys "fastcdr rti-connext-dds-6.0.1 urdfdom_headers python3-vcstool"
  
  colcon build --symlink-install
  ```