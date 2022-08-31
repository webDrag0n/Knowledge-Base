- #Git
- ### Gitlab服务器搭建
	- 社区版（CE）
	- 参考：[手把手教你搭建gitlab服务器](https://zhuanlan.zhihu.com/p/62042884)
	- 镜像链接：https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce
	- ubuntu: /ubuntu/pool/focal/main/g/gitlab-ce
		- 下载后在文件路径下执行
		- ```bash
		  sudo dpkg -i gitlab-ce-...x86_64.deb
		  ```
		- 编辑/etc/gitlab/gitlab.rb，更改GitLab URL下的external_url属性为服务器ip或域名，并设置端口，例：
		  `10.60.2.114:8081`
		- ```bash
		  gitlab-ctl reconfigure
		  gitlab-ctl restart
		  ```
		- 安装完成后会提示初始密码文件路径，复制密码并在刚刚配置的域名/ip访问gitlab，默认用户为root