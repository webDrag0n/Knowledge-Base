- #[[Project Morpheus]]
- ## 架构
- ![image.png](../assets/image_1729932532531_0.png){:height 306, :width 401}
- ## Roadmap
	- ✅ MuJoCo
		- Unity端插件部署完成
	- ✅ [[Unitree MuJoCo]]
		- 部署完成
	- ✅ [[Unitree sdk2]] [[Unitree sdk2 python]]
	- ✅ ML-Agent
	- ✅ ROS Plugin：Unity-Robotics-Hub
		- ROS2（foxy）与Unity通信完成测试，相关过程记录在 [[Unity-Robotics-Hub]]
	- ▶️ Isaac Sim RL Sim2Sim测试
		- ✅ 环境部分部署完成
		- 缺失依赖待解决
	- ▶️ Hololens 2 连接Unity
		- ✅ Microsoft-MRTK3.0 OpenXR技术栈部署完成
		- ▶️ Hololens 2连接Unity（相机输出）
		- ⏸️ Hololens 2手部输入反控仿真物体
	- ⏸️ 动捕数据录制模块
	- ⏸️ Unitree H1仿真数据录制模块
- ## 部署
	- #### 后端
		- Docker
			- 下载`morpheus_backend.tar`
			- TODO 补充docker链接
			- TODO 需要将docker镜像名与文件名统一
			- ```bash
			  docker load -i morpheus_backend.tar
			  docker run --name morpheus --gpus all -it --shm-size=16g --rm -v /mnt/j/DockerDirs/morpheus/:/root -p 10000:10000 morpheus:v0.1
			  [press ctrl-p-q to detach from container]
			  docker ps -a # get docker container id
			  docker exec -it [container_id] /bin/bash
			  
			  # activate humble environment
			  # IMPORTANT: CHECK IF ~/.bashrc ALREADY INCLUDES THE FOLLOWING COMMAND!
			  source /opt/ros/humble/setup.bash
			  echo " source /opt/ros/humble/setup.bash" >> ~/.bashrc
			  
			  # Get Morpheus backend repo
			  cd ~
			  git clone https://github.com/webDrag0n/MorpheusROS2EndPoint.git
			  cd MorpheusROS2EndPoint
			  rm -r build # clean legacy builds
			  
			  # Build
			  colcon build
			  source install/setup.sh
			  ```
		- Manual Install
			- [[Unity-Robotics-Hub]]
	- #### 渲染
	- #### Hololens2
	- #### 动作捕捉
	-
	-