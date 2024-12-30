# 操作
	- ### 查看运行中的镜像
	  collapsed:: true
		- ```bash
		  docker ps
		  ```
	- ### 传输文件
	  collapsed:: true
		- ```bash
		  docker cp /source container_id:/destination
		  # vice versa
		  ```
	- ### 运行命令
	  collapsed:: true
		- ```bash
		  docker exec -it container_id [command]
		  ```
	- ### 退出Docker不关闭
	  collapsed:: true
		- ```bash
		  ctrl+P+Q
		  ```
	- ### 进入运行中的Container
	  collapsed:: true
		- ```bash
		  docker exec -it container_id /bin/bash
		  ```
	- ### 导入导出当前Docker环境为Image
		- ```bash
		  docker commit container_id name:version
		  ```
		- 导出容器
		  打开 Docker Desktop。
		  选择“Containers / Apps”选项卡。
		  找到要导出的容器，点击右侧的“…”按钮。
		  选择“Export”选项。
		  选择保存位置，导出为 .tar 文件。
		- 导入容器
		  在 Docker Desktop 中，点击“Containers / Apps”选项卡。
		  点击右上角的“Import”按钮。
		  选择之前导出的 .tar 文件，完成导入。
		- 导出镜像
		  点击“Images”选项卡。
		  找到要导出的镜像，点击右侧的“…”按钮。
		  选择“Export”选项。
		  选择保存位置，导出为 .tar 文件。
		- 导入镜像
		  在 Docker Desktop 中，点击“Images”选项卡。
		  点击右上角的“Import”按钮。
		  选择之前导出的 .tar 文件，完成导入。
	- ### `docker save` 命令
	  `docker save`命令用于将一个或多个Docker镜像保存到一个tar归档文件中。这个命令非常适合于镜像的备份或者将镜像从一个Docker环境迁移到另一个Docker环境的场景。
	- ### 命令语法
	  
	  ```
	  docker save **[**OPTIONS**]** IMAGE **[**IMAGE...**]**
	  ```
	- **[OPTIONS]**: 可选参数，例如`-o`，用于指定输出的文件名。
	- **IMAGE [IMAGE...]**: 指定要保存的一个或多个镜像的名称或ID。
	- ### 使用场景
		- 镜像的备份与归档。
		- 将镜像从一个环境迁移到另一个环境，例如从开发环境到测试环境。
	- ### 示例代码
	  将名为`myimage:latest`的Docker镜像保存到名为`myimage_latest.tar`的文件中：
	  ```
	  docker save -o myimage_latest.tar myimage:latest
	  ```
	- ### `docker export` 命令
	  与`docker save`不同，`docker export`命令是用于将一个运行中的容器的文件系统导出为tar归档文件。这个命令适用于需要导出容器内容，而不是镜像的场景。
	- ### 命令语法
	  
	  ```
	  docker export **[**OPTIONS**]** CONTAINER
	  ```
	- **[OPTIONS]**: 可选参数，例如`-o`，用于指定输出的文件名。
	- **CONTAINER**: 指定要导出的容器的ID或名称。
	- ### 使用场景
	  collapsed:: true
		- 容器的文件系统备份。
		- 从运行中的容器创建镜像。
	- ### 示例代码
	  将名为`mycontainer`的容器导出到名为`mycontainer.tar`的文件中：
	  ```
	  docker export -o mycontainer.tar mycontainer
	  ```