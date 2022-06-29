- 参考腾讯云：[Linux云服务器搭建FTP服务-最佳实践](https://cloud.tencent.com/document/product/213/10912)
- ## 安装vsftpd
	- ```bash
	  apt update
	  apt install vsftpd
	  ```
- ## 建立ftp专用用户和用户组
	- 1，创建：
	- -d 指定用户根目录
	- -s 用户登录方式，nologin禁用ssh，使用ftp登录
	- ```bash
	  useradd -d /home/ftpuser -s /sbin/nologin ftpuser
	  ```
	- 扩展，查看存在的用户
	- ```bash
	  cat /etc/passwd
	  ```
	- 扩展，修改
	- ```bash
	  usermod -s /sbin/nologin ftpuser   //限定用户ftpuser不能telnet，只能ftp
	  ```
	- 2，密码 ：
	- ```bash
	  passwd ftpuser
	  ```
	- 按照提示输入对应的密码
	- 3，权限：
	- ```bash
	  chown ftpuser /home/ftpuser/
	  ```
	- 扩展请参考chown 命令，更改文件夹的拥有者，注意和chmod命令的差别
- ## 配置vsftpd.conf
	- 1，ftp的配置文件在为：/etc/vsftpd/vsftpd.conf
	- 2，配置文件
	- anonymous_enable=NO   ；禁止匿名登录
	- chroot_list_enable=YES   ； 使用chroot方式配置权限
	- chroot_list_file=/etc/vsftpd/chroot_list   ； 指定chroot文件的位置
	- vim /etc/vsftpd/chroot_list   ;  打开chroot文件
	- 加入一行，ftpuser
	- 即刚才创建的用户名，在这个文件里面的用户可以登录FTP，并访问其他目录
	- 重启FTP，查看文章第一模块的重启命令
	- 3，配置文件conf中几个常用配置
	- allow_writeable_chroot=YES  ； 添加写权限
	- local_root=/var/ftp  ；  出初始登录目录
	- ```bash
	  ```
- ## 启动vsftpd服务
	- ```bash
	  systemctl service vsftpd enable
	  systemctl service vsftpd restart
	  ```
- ### passive与active模式
- ## ftp客户端
	- [Filezilla](https://filezilla-project.org/)（注意安装时不要安装捆绑浏览器！！！）
	- WinSCP（在passive模式下有奇怪的bug会导致无法与目录和文件交互）
-