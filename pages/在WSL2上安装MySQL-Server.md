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
	- 1. 开启Windows端口转发和防火墙许可
	-
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
		  sudo mysql -u root
		  ```
		- ```MySql
		  grant system_user on *.* to 'root';
		  # mysql 8.0后
		  create user 'root'@'%' identified by '[mysql root password]';
		  grant all on *.* to 'root'@'%';
		  alter user 'root'@'%' identified with mysql_native_password by '[mysql root password]';
		  flush privileges
		  ```
		- ```bash
		  service mysql restart
		  ```