- 参考腾讯云[Linux云服务器搭建FTP服务-最佳实践](https://cloud.tencent.com/document/product/213/10912)
- # 安装vsftpd
	- ```bash
	  sudo apt update
	  sudo apt install vsftpd
	  ```
- # 建立ftp专用用户和用户组
	- ```bash
	  sudo useradd 
	  ```
- # 配置vsftpd.conf
	- ```bash
	  sudo vim /etc/vsftpd.conf
	  ```
- # 启动vsftpd服务
	- ```bash
	  sudo systemctl service vsftpd enable
	  sudo systemctl service vsftpd restart
	  ```
- ### passive与active模式
- # ftp客户端
	- [Filezilla](https://filezilla-project.org/)（注意安装时不要安装捆绑浏览器！！！）
	- WinSCP（在passive模式下有奇怪的bug会导致无法与目录和文件交互）
-