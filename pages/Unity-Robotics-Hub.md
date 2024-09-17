- #Unity #机器人仿真
- ## 安装
	- Git：[官方Git页面](https://github.com/Unity-Technologies/Unity-Robotics-Hub)
	- 首先使用鱼香ROS教程安装ROS2环境
	- [安装ros_unity_integration与demo](https://github.com/Unity-Technologies/Unity-Robotics-Hub/blob/main/tutorials/ros_unity_integration/setup.md)
		- ```bash
		  git clone https://github.com/Unity-Technologies/Unity-Robotics-Hub.git
		  # 注意最后的branch指定参数
		  git clone https://github.com/Unity-Technologies/ROS-TCP-Endpoint.git -b main-ros2
		  mkdir workspace_colcon
		  cd workspace_colcon
		  mkdir src
		  cp -r ../ROS-TCP-Endpoint ../Unity-Robotics-Hub ./src
		  
		  ```
		- ros_tcp_endpoint目录下：
		  ```bash
		  # conda 环境会扰乱ros2引用
		  conda deactivate
		  
		  # 一定要执行两次
		  # --symlink-install 更快迭代
		  colcon build --symlink-install
		  source install/setup.bash
		  colcon build --symlink-install
		  source install/setup.bash
		  ```
		- 如安装过程中报`No module named 'em'`错误，请通过`pip3 install empy==3.3.2`安装`em`模块，⚠️注意版本号不对也有可能报错，其他缺少模块报错只需缺什么装什么即可。
		- 测试
		  ```bash
		  # conda 环境会扰乱ros2引用
		  conda deactivate
		  
		  ros2 run ros_tcp_endpoint default_server_endpoint --ros-args -p ROS_IP:=0.0.0.0
		  ```
		- 注意如果报错某package not found或import error，很有可能是没有一开始就关闭conda环境，可以尝试删除除src以外所有生成文件重新构建。
	- 安装URDF-Importer
		- 官方教程：[Importing a Niryo One Robot using URDF Importer](https://github.com/Unity-Technologies/Unity-Robotics-Hub/blob/main/tutorials/urdf_importer/urdf_tutorial.md)
		- 在unity package manager中选择`install from git`并填入链接`https://github.com/Unity-Technologies/URDF-Importer.git?path=/com.unity.robotics.urdf-importer#v0.5.2`，v0.5.2为版本号，请注意选择。
		-
		-