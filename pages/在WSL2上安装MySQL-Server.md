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
  mysql -u root -p
  ```
- 使数据库可被远程访问
	- 1. 开启Windows端口转发和防火墙许可
	- 2. Mysql设置允许远程访问