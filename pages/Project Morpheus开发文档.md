- #[[Project Morpheus]]
- ## 架构
- ![image.png](../assets/image_1729932532531_0.png){:height 306, :width 401}
- ## Roadmap
	- ### 阶段性目标
	- Demo测试任务：实验者戴Hololens2能看到仿真环境中的Unitree H1机器人和箱子，与机器人各抬一边把箱子搬到目标位置。
	-
	- ✅ MuJoCo
		- ✅ Unity端插件部署完成
		- ✅ Unitree MuJoCo部署完成
	- ✅ Unitree h1物理仿真效果测试完成
	- ✅ Unitree sdk2，Unitree sdk2 python
	- ✅ ML-Agent
	- ✅ ROS2 通信
		- ✅ ROS Plugin：Unity-Robotics-Hub
		- ✅ ROS2（foxy，humble）与Unity通信完成测试
		- ✅ ROS2 控制信号控制环境仿真机器人
		- ✅ ROS2 仿真环境机器人状态回传
	- ▶️ ROS2 传感器仿真
		- ⏸️ 相机（自然有，只需要接口）
		- ✅ Lidar传感器
		- ⏸️ IMU（简单，只需要接口）
	- ▶️ Isaac Sim RL Sim2Sim测试
		- ✅ 环境部分部署完成
		- ▶️ 迁移Isaac Gym代码至本平台
	- ▶️ Hololens 2 连接Unity
		- ✅ Microsoft-MRTK3.0 OpenXR技术栈部署完成
		- ✅ Hololens 2连接Unity
		- ⏸️ Hololens 2手部输入反控仿真物体
		- ⏸️ Hololens 2手部动捕信号回传
		- ⏸️ Hololens 2相机信号回传
	- ⏸️ 仿真数据录制模块
		- Unitree H1
		- Unitree Go2
		- 四旋翼无人机
	- ⏸️ Robomaster机器人MuJoCo模型
	- ⏸️ Unity输出语义分割图
		- ⏸️ SAM2？或者直接仿真直出
	- hardware-in-the-loop测试
	- human-in-the-loop测试、数据采集、持续训练
	- simulation-in-the-loop
- ## 部署
	- ### 后端
		- [见Morpheus文档](https://github.com/webDrag0n/Morpheus?tab=readme-ov-file#how-to-build)
		- 核心部件[[Unity-Robotics-Hub]]
		- 运行
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
		- {{embed ((66ef13de-6409-42e9-b603-d1f630dd06be))}}
	- #### 渲染
	- #### Hololens2
		- 手部动捕
	- #### 全身动捕
		-
	-
	-