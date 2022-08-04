- ## 一些重要文件的名字，位置与功能
	- etc
		- bash.bashrc
		  id:: 62eb946d-a94f-4486-880a-06594b75aec2
			- 当交互式终端打开时被执行，默认会引用并执行 ((62eb948c-87d4-4004-8131-6dcd549c8e0a))
		- profile
		  id:: 62eb948c-87d4-4004-8131-6dcd549c8e0a
			- 当ssh登录发生时被执行
- ## 安全
	- ### 分用户日志
		- 参考 [Linux下记录所有用户的登录和操作日志](https://blog.51cto.com/xuaijun/2821502)
		- 在 ((62eb946d-a94f-4486-880a-06594b75aec2)) 中加入
		- ```bash
		  history
		  USER=`whoami`
		  USER_IP=`who -u am i 2>/dev/null| awk '{print $NF}'|sed -e 's/[()]//g'`
		  if [ "$USER_IP" = "" ]; then
		  USER_IP=`hostname`
		  fi
		  if [ ! -d /var/log/history ]; then
		  mkdir /var/log/history
		  chmod 777 /var/log/history
		  fi
		  if [ ! -d /var/log/history/${LOGNAME} ]; then
		  mkdir /var/log/history/${LOGNAME}
		  chmod 300 /var/log/history/${LOGNAME}
		  fi
		  export HISTSIZE=4096
		  DT=`date +"%Y%m%d_%H:%M:%S"`
		  export HISTFILE="/var/log/history/${LOGNAME}/${USER}@${USER_IP}_$DT"
		  chmod 600 /var/log/history/${LOGNAME}/*history* 2>/dev/null
		  ```
		- 为每个用户建立``/var/log/history/{Username}``目录，并按需设置每个文件夹的访问权限，建议设置如下：
		- ```bash
		  /var/log/history            root     root   drwxrwxrwx
		  /var/log/history/{Username} Username nosudo d-wx------
		  ```
		- 注意此处的nosudo为用户所在组，此处取nosudo是将该组下用户全部移除了sudo权限
	- ### 权限管理
		- 移除sudo权限：
			-
		- drwxr-xr-x权限：
		  id:: c0a1706b-a747-4d5b-9d9e-c2fbf387665a
			- 目录所有者可读写执行，其他用户只能读写不能执行
			- sudo chmod -755 directory
- ## 服务搭建
  collapsed:: true
	- [[FTP服务器搭建]]
- ## Linux安装Windows应用
  collapsed:: true
	- ### 微信
		- ```bash
		  # "install wine"
		  sudo apt install wine
		  # "install winetricks"
		  sudo apt install winetricks
		  winetricks riched20
		  winetricks fakechinese
		  # "change to win10"
		  winecfg
		  ```
		- 下载微信Windows安装包并在下载目录打开终端
		- ```bash
		  # "install weichart"
		  env LANG="zh_CN.UTF-8" wine WeChatSetup.exe
		  # "install front"
		  echo "LANG=zh_CN.UTF-8" >> ~/.local/share/applications/wine/Programs/微信/微信.desktop
		  ```
		- 完成后重启系统