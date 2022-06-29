- 参考腾讯云：[Linux云服务器搭建FTP服务-最佳实践](https://cloud.tencent.com/document/product/213/10912)
- ## 安装vsftpd
	- ```bash
	  sudo apt update
	  sudo apt install vsftpd
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
	  
	  usermod -d /home/ftpuser2   ftpuser    //更改用户ftpuser的主目录为/home/ftpuser2
	  ```
	- 2，密码 ：passwd  ftpuser
	- 按照提示输入对应的密码
	- 3，权限：chown ftpuser /home/ftpuser/
	- 扩展请参考chown 命令，更改文件夹的拥有者，注意和chmod命令的差别
- ## 配置vsftpd.conf
	- ```bash
	  sudo vim /etc/vsftpd.conf
	  ```
- ## 启动vsftpd服务
	- ```bash
	  sudo systemctl service vsftpd enable
	  sudo systemctl service vsftpd restart
	  ```
- ### passive与active模式
- ## ftp客户端
	- [Filezilla](https://filezilla-project.org/)（注意安装时不要安装捆绑浏览器！！！）
	- WinSCP（在passive模式下有奇怪的bug会导致无法与目录和文件交互）
-