- #Linux
- # 简介
- useradd是一个linux命令，但是它提供了很多参数在用户使用的时候根据自己的需要进行设置；而adduser是一个perl 脚本，在使用的时候会出现类似人机交互的界面，提供选项让用户填写和选择，这个命令比起useradd来说比较简单，也比较傻瓜。
- ## adduser
	- ```bash
	  adduser
	  ```
	- 在使用adduser命令的时候，系统会添加这个用户名，并且还会自动地创建与这个用户名名字一样的用户组作为这个用户的初始用户组。此外，还会自动地在/home目录下面创建一个与用户同名的目录，接着执行"cp /etc/skel  /home/用户名"的操作，实现新增用户的主目录的初始化。
	  用adduser这个命令创建的账号是系统账号，可以用来登录到我们的ubuntu系统。
- ## useradd
	- ```bash
	  useradd
	  ```
	- useradd有大量的参数供我们进行个性化设置，但是，也有比较多的默认设置是我们不知道的，所以，在进行这个参数选择的时候还是需要谨慎和细心，不然的话可能会得到跟我们预想中不一样的结果。useradd的参数如下：
	          -c 备注 加上备注。并会将此备注文字加在/etc/passwd中的第5项字段中
	          -d 用户主文件夹。指定用户登录所进入的目录，并赋予用户对该目录的的完全控制权
	          -e 有效期限。指定帐号的有效期限。格式为YYYY-MM-DD，将存储在/etc/shadow
	          -f 缓冲天数。限定密码过期后多少天，将该用户帐号停用
	          -g 主要组。设置用户所属的主要组
	          -G 次要组。设置用户所属的次要组，可设置多组
	          -M 强制不创建用户主文件夹
	         -m 强制建立用户主文件夹，并将/etc/skel/当中的文件复制到用户的根目录下
	          -p 密码。输入该帐号的密码
	          -s shell。用户登录所使用的shell
	          -u uid。指定帐号的标志符user id，简称uid
	  useradd这个命令创建的是普通账号，并不能用来登录系统。
	  于是我得出了一个结论：当使用参数"-m"的时候，系统会自动地在/home目录下建立一个与新建用户同名的用户主文件夹；如果不使用"-m"的话，那么就默认是使用“-M”参数，不创建主文件夹，即使你使用了"-d"这个参数。所以，"-d"这个参数是跟"-m"一起使用的，让用户自己选择主文件夹的路径。
-
- deluser
- usermod -aG
- ————————————————
  版权声明：本文参考CSDN博主「li_101357」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
  原文链接：https://blog.csdn.net/li_101357/article/details/46778827