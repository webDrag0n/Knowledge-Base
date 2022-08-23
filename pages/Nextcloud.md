- ### 安装与配置
	- #### 安装
		- [Use Apache2 Server](https://docs.nextcloud.com/server/stable/admin_manual/installation/source_installation.html#apache-web-server-configuration)
		-
	- 配置文件
		- `/var/www/html/nextcloud/config/config.php`
	- Configuration Parameters
		- Documentation link: https://docs.nextcloud.com/server/19/admin_manual/configuration_server/config_sample_php_parameters.html?highlight=overwrite%20cli%20url
	- 配置Redis加速
		- 参考
			- https://www.jianshu.com/p/b9daf981ebba
			- [Nextcloud私有云盘配置和优化技巧](https://zhuanlan.zhihu.com/p/50322342)
			- [NextCloud的调优及安全配置](https://www.fencatn.com/197/)
		- #### 安装Redis
		- ```bash
		  sudo apt install redis redis-servere
		  ```
		- #### 设置Redis密码【必须】
		- ```bash
		  redis-cli
		  
		  127.0.0.1:6379> CONFIG set requirepass xxx
		  ```
		- 更改配置文件
		- ```bash
		  sudo vim /var/www/html/nextcloud/config/config.php
		  
		  +
		  #'memcache.distributed' => '\\OC\\Memcache\\Redis',
		  'memcache.locking' => '\\OC\\Memcache\\Redis',
		  'filelocking.enabled' => 'true',
		  #'redis' => array(
		  #  'host' => 'localhost',
		  #  'port' => 6379,
		  #  'password' => 'Lzx3778.redis',
		  #),
		  'redis' => array(
		    'host' => '/var/run/redis/redis.sock',
		    'port' => 0,
		    'dbindex' => 0,
		    'password' => 'Lzx3778.redis',
		    'timeout' => 1.5,
		  ),
		  ```
- ### 增加信任域名
	- https://help.nextcloud.com/t/howto-add-a-new-trusted-domain/26
	- #### 在 [[apache2]] 中几个重要的配置文件位置
		- nextcloud自身配置文件
			- `/etc/apache2/sites-available/nextcloud.conf`
			- `/etc/apache2/sites-enabled/nextcloud.conf`
			- 以上两个文件内容相同，ssl证书位置和允许通过什么域名访问的设置都在里面，在available文件夹中为可选未启动，~~放入enabled文件夹中以后并执行~~
			- 请勿直接修改`sites-enable/nextcloud.conf`，使用以下命令：
			  background-color:: #793e3e
			- ```bash
			  a2ensite nextcloud.conf
			  sudo service apache2 restart
			  ```
			- 完成配置
- ### 数据目录权限
  collapsed:: true
	- {{embed ((62fc9ef9-95bb-4877-ae90-50aaf730c887))}}
- ### Nextcloud + Raidrive DAV客户端
  collapsed:: true
	- ![image.png](../assets/image_1653845444421_0.png)
- ### 数据硬盘迁移
  collapsed:: true
	- 挂载新硬盘
	- 设置启动时自动挂载
		- ```bash
		  vim /etc/fstab
		  
		  + /dev/sdb1 /new ext4 defaults 0 0
		  ```
	- 重启
	- 复制文件
		- ```bash
		  cp -r /original/* /new
		  
		  # 确认复制隐藏文件
		  cp /original/.htaccess /original/.ocdata /CloudStorage/
		  ```
	- 更改文件夹与子文件夹所有权
		- ```bash
		  chown -hR www-data:www-data /new
		  ```
	- 修改 nextcloud 配置文件中的数据存储目录位置，配置文件路径为 */data/wwwroot/nextcloud/config* （部分旧版镜像的配置文件路径为：*/data/wwwroot/default/nextcloud/config*）
		- `'datadirectory' => '/CloudStorage'`
- ### 挂载外部硬盘
  collapsed:: true
	- https://www.zywvvd.com/notes/environment/nas/nextcloud/nextcloud-add-disk/
- Memcache \OC\Memcache\APCu not available for local cache
- ### 进入维护模式
	- ```bash
	  sudo -u www-data php occ maintenance:mode --on
	  ```
	- 如报错`Could not open input file: occ`，请确认是否nextcloud目录与子目录，子文件皆可被www-data用户读写
	-
-