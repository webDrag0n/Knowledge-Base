- Git是一种
- ## 相关错误与修复方法
	- ### Git Filename too long
		- 克隆时遇到过长文件名时在bash中执行下列命令
		- 该命令只对bash中的git生效，对图形界面客户端如github desktop无效
		- ```bash
		  git config --system core.longpaths true
		  ```