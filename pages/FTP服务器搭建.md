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
- 执行以下命令，打开 vsftpd.conf 文件。
  ```vim /etc/vsftpd/vsftpd.conf```
  按 i 切换至编辑模式，根据实际需求选择 FTP 模式，修改配置文件 vsftpd.conf：
	- 注意:
	  background-color:: #978626
	  FTP 可通过主动模式和被动模式与客户端机器进行连接并传输数据。由于大多数客户端机器的防火墙设置及无法获取真实 IP 等原因，建议您选择被动模式搭建 FTP 服务。如下修改以设置被动模式为例，您如需选择主动模式，请前往 设置 FTP 主动模式。
- i. 修改以下配置参数，设置匿名用户和本地用户的登录权限，设置指定例外用户列表文件的路径，并开启监听 IPv4 sockets。
  ```bash
  anonymous_enable=NO
  local_enable=YES
  write_enable=YES
  chroot_local_user=YES
  chroot_list_enable=YES
  chroot_list_file=/etc/vsftpd/chroot_list
  listen=YES
  ```
- ii. 在行首添加 #，注释 listen_ipv6=YES 配置参数，关闭监听 IPv6 sockets。
  #listen_ipv6=YES
- iii. 添加以下配置参数，开启被动模式，设置本地用户登录后所在目录，以及云服务器建立数据传输可使用的端口范围值。
  local_root=/var/ftp/test
  allow_writeable_chroot=YES
  pasv_enable=YES
  pasv_address=xxx.xx.xxx.xx #请修改为您的 Linux 云服务器公网 IP
  pasv_min_port=40000
  pasv_max_port=45000
  按 Esc 后输入 :wq 保存后退出。
  执行以下命令，创建并编辑 chroot_list 文件。
  vim /etc/vsftpd/chroot_list
  按 i 进入编辑模式，输入用户名，一个用户名占据一行，设置完成后按 Esc 并输入 :wq 保存后退出。
  设置的用户将不会被锁定在主目录，您若没有设置例外用户的需求，可跳过此步骤，输入 :wq 退出文件。
-
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