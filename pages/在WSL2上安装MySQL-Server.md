- #WSL2 #Mysql
- https://zhuanlan.zhihu.com/p/166444726
- ```bash
  sudo apt-get update
  sudo apt-get upgrade
  sudo apt-get install mysql-server
  sudo usermod -d /var/lib/mysql/ mysql
  sudo service mysql start
  # 设置密码
  sudo mysql -u root -p
  ```
- ```bash
  # 之后的登录也使用命令
  sudo mysql -u root -p
  ```
- 使数据库可被远程访问
	- collapsed:: true
	  1. 开启Windows端口转发和防火墙许可
		- #远程访问WSL2服务
		- ```powershell
		  netsh interface portproxy add v4tov4 listenaddress=0.0.0.0 listenport=13306 connectaddress=172.22.62.142 connectport=3306
		  
		  netsh advfirewall firewall add rule name=WSL2 dir=in action=allow protocol=TCP localport=13306
		  ```
	- 2. Mysql设置允许远程访问
		- ```bash
		  sudo vim /etc/mysql/mysql.conf.d/mysql.cnf
		  ```
		- 修改（加#注释）
		  ```bash
		  # bind-address           = 127.0.0.1
		  # mysqlx-bind-address    = 127.0.0.1
		  ```
		  ```bash
		  sudo mysql -u root -p
		  ```
		- ```mysql
		  # mysql 8.0前
		  grant system_user on *.* to 'root';
		  # mysql 8.0后，执行以下命令
		  create user 'root'@'%' identified by '[mysql root password]';
		  grant all on *.* to 'root'@'%';
		  alter user 'root'@'%' identified with mysql_native_password by '[mysql root password]';
		  flush privileges
		  ```
		- service mysql restart
-