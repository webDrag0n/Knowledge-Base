- #Unity #机器人仿真
- ## 安装
  collapsed:: true
	- Git：[官方Git页面](https://github.com/Unity-Technologies/Unity-Robotics-Hub)
	- 首先使用[鱼香ROS](https://fishros.org.cn/forum/)教程安装ROS2-foxy桌面版环境，如遇到问题也可改为安装基础版，但是桌面版有更全面的功能，对于其他ROS2开发可能有用。
		- [一键安装教程](https://fishros.org.cn/forum/topic/20/%E5%B0%8F%E9%B1%BC%E7%9A%84%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85%E7%B3%BB%E5%88%97)
		  ```bash
		  wget http://fishros.com/install -O fishros && . fishros
		  ```
	- 下载本仓库
		- ```bash
		  git clone https://github.com/webDrag0n/Morpheus.git
		  ```
	- 删除build目录（如有）并执行：
		- ```bash
		  bash start_compile.sh
		  ```
	- [安装ros_unity_integration与demo](https://github.com/Unity-Technologies/Unity-Robotics-Hub/blob/main/tutorials/ros_unity_integration/setup.md)
	  id:: 66e563ac-54e4-4847-a4ed-8ff236dfaa9f
		- 将项目目录下的MuJoCo.zip复制至用户目录（Windows：C:/Users/<UserName>）并解压，文件夹命名为`MuJoCo`
		- ```bash
		  git clone https://github.com/Unity-Technologies/Unity-Robotics-Hub.git
		  # 注意最后的branch指定参数
		  git clone https://github.com/Unity-Technologies/ROS-TCP-Endpoint.git -b main-ros2
		  mkdir workspace_colcon
		  cd workspace_colcon
		  mkdir src
		  cp -r ../ROS-TCP-Endpoint ../Unity-Robotics-Hub ./src
		  ```
		- workspace_colcon目录下：
		  id:: 66e5649f-d7b9-41e0-9960-4d4ba47b3d90
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
	- Unity端插件安装
	  id:: 66f11252-eeb3-43d1-8b00-d9f84883f836
		- 安装ROS-TCP-Connector（Unity端插件）
			- 在unity package manager中选择`install from git`并填入链接`https://github.com/Unity-Technologies/ROS-TCP-Connector.git?path=/com.unity.robotics.ros-tcp-connector`
		- 安装URDF-Importer
			- 官方教程：[Importing a Niryo One Robot using URDF Importer](https://github.com/Unity-Technologies/Unity-Robotics-Hub/blob/main/tutorials/urdf_importer/urdf_tutorial.md)
			- 在unity package manager中选择`install from git`并填入链接`https://github.com/Unity-Technologies/URDF-Importer.git?path=/com.unity.robotics.urdf-importer#v0.5.2`，v0.5.2为版本号，请注意选择。
		- 将该仓库中tutorials/ros_unity_integration/ros2_packages下的包复制至workspace_colcon/src并重新执行编译步骤 ((66e5649f-d7b9-41e0-9960-4d4ba47b3d90))
		- 在 Unity 菜单栏中，转到 Robotics -> Generate ROS Messages.... 在 Message Browser 窗口中，单击右上角的 Browse 按钮​​，将 ROS 消息路径设置为此 repo 中的 tutorials/ros_unity_integration/ros_packages/unity_robotics_demo_msgs。
			- ros2_packages 文件夹中的版本是等效的；ROS2 用户可以随意使用或不使用。
		- 在消息浏览器中，展开 unity_robotics_demo_msgs 子文件夹，然后单击“Build 2 msgs”和“Build 2 srvs”，从 ROS .msg 和 .srv 文件生成 C# 脚本。
- ## 增加模块
	- 在`<workspace>/src/unity_robotics_demo/unity_robotics_demo/`目录下添加新publisher，如`h1_control_publisher.py`
	- 更改`<workspace>/src/unity_robotics_demo/setup.py`，在`entry_points`字段下以
	  ```python
	  entry_points={'console_scripts': ['h1_control_publisher = unity_robotics_demo.h1_control_publisher:main'], ...}
	  ```
	  的格式注册新模块
	- 在`<workspace>/src/unity_robotics_demo/unity_robotics_demo_msgs/msg/`目录下添加新消息，如`H1ControlCommand.msg`
	- 更改`<workspace>/src/unity_robotics_demo/unity_robotics_demo_msgs/CMakeLists.txt`，在`rosidl_generate_interfaces`字段下以
	  ```cmake
	  rosidl_generate_interfaces(${PROJECT_NAME}
	  	"msg/H1ControlCommand.msg"
	      ...
	      "srv/xxx.srv"
	      DEPENDENCIES builtin_interfaces geometry_msgs std_msgs
	  )
	  ```
	  格式注册新消息
	- 最后执行`<workspace>/start_compile.sh`或
	  ```bash
	  cd <workspace>
	  source install/setup.bash
	  colcon build
	  source install/setup.bash
	  ```
	  完成编译
- ## 运行
	- 运行前需要重新编译工作区，以防有更改在增加模块阶段忘记编译
	  ```bash
	  cd <workspace>
	  ./start_compile.sh
	  ./start_h1_publisher.sh
	  ```
	- 开启三个终端，分别依次执行：
	  ```bash
	  # Terminal 1
	  source install/setup.sh
	  ./start_ros_tcp_endpoint.sh 
	  ```
	  启动并运行Unity项目
	  开启第二个终端
	  ```bash
	  # Terminal 2
	  source install/setup.sh
	  ./start_h1_publisher.sh
	  ```
	  开启第三个终端
	  ```bash
	  # Terminal 3
	  source install/setup.sh
	  cd src/unity_robotics_demo/unity_robotics_demo
	  python3 h1_controller.py
	  ```
	- 回到Unity窗口即可看的结果