- #Git
- ### Gitlab服务器搭建
	- 参考：[手把手教你搭建gitlab服务器](https://zhuanlan.zhihu.com/p/62042884)
	- 镜像链接：https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce
	- ubuntu: /ubuntu/pool/focal/main/g/gitlab-ce
		- 下载后在文件路径下执行
		- ```bash
		  sudo dpkg -i gitlab-ce-...x86_64.deb
		  ```
		- 编辑/etc/gitlab/gitlab.rb