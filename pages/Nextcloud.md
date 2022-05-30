- Configuration Parameters
	- Documentation link: https://docs.nextcloud.com/server/19/admin_manual/configuration_server/config_sample_php_parameters.html?highlight=overwrite%20cli%20url
- 如何增加信任域名
	- https://help.nextcloud.com/t/howto-add-a-new-trusted-domain/26
- 在apache2版本中几个重要的配置文件位置
	- nextcloud自身配置文件
	- apache2配置文件
		- /etc/apache2/sites-available/nextcloud.conf
		- /etc/apache2/sites-enabled/nextcloud.conf
		- 以上两个文件内容相同，ssl证书位置和允许通过什么域名访问的设置都在里面，在available文件夹中为可选未启动，放入enabled文件夹中以后并执行
			- ```bash
			  sudo service apache2 restart
			  ```
			- 完成配置
- ### 数据目录权限
- {{embed ((c0a1706b-a747-4d5b-9d9e-c2fbf387665a))}}
- ### Nextcloud + Raidrive DAV客户端
	- ![image.png](../assets/image_1653845444421_0.png)