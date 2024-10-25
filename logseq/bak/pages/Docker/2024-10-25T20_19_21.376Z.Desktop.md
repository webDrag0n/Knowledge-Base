- # 操作
	- ### 查看运行中的镜像
		- ```bash
		  docker ps
		  ```
	- ### 传输文件
		- ```bash
		  docker cp /source container_id:/destination
		  # vice versa
		  ```
	- ### 运行命令
		- ```bash
		  docker exec -it container_id [command]
		  ```