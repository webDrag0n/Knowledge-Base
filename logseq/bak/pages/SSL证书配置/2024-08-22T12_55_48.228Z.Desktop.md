- [[SSL证书]]
- 从域名证书签发商处下载ssl证书，然后根据对应网页服务器的流程配置
- # Apache2 SSL证书配置
  id:: 6429768d-04b9-4b12-be66-b3c275cf37e0
	- 证书格式：Nginx证书
	- 打开`/etc/apache2/sites-available`，找到你需要用到该证书的服务对应的配置文件，如`nextcloud.conf`
	- ```conf
	  Alias /nextcloud "/var/www/nextcloud"
	  DocumentRoot "/var/www/nextcloud"
	  #填写证书名称
	  ServerName www.xxx.com
	  ServerAlias 111.111.111.111 xxx.com *.xxx.com
	  
	  #启用 SSL 功能
	  SSLEngine on
	  #证书文件的路径
	  SSLCertificateFile /etc/httpd/ssl/www-xxx-com.crt
	  #私钥文件的路径
	  SSLCertificateKeyFile /etc/httpd/ssl/www-xxx-com.key
	  #证书链文件的路径
	  SSLCertificateChainFile /etc/httpd/ssl/www-xxx-com.crt
	  ```
	- 将证书放置于对应路径下
	- 重启apache2
	- ```bash
	  apachectl -k restart
	  ```