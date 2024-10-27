- #Docker
- ## 镜像选择
	- 建议使用
	  nvcr.io/nvidia/nvhpc:24.9-devel-cuda_multi-ubuntu22.04
	  nvcr.io/nvidia/nvhpc:21.7-devel-cuda11.4-centos7
	  ```bash
	  docker pull <image_name>:<tag>
	  ```
- ## 镜像部署
	- 端口：22和业务接口
	- 目录挂载
		- 建议将外置目录挂载为Docker环境的根目录
- ## SSH密钥配置
	- ```bash
	  ssh-keygen -t ed25519
	  ~/.ssh/authorized_keys
	  ```
- ## 启动项配置
	- ~/.bashrc
-