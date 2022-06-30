- ### 权限
	- drwxr-xr-x权限：
	  id:: c0a1706b-a747-4d5b-9d9e-c2fbf387665a
		- 目录所有者可读写执行，其他用户只能读写不能执行
		- sudo chmod -755 directory
-
- ## Linux安装Windows应用
	- ### 微信
		- echo "install wine"
		  sudo apt install wine
		- echo "install winetricks"
		  sudo apt install winetricks
		  winetricks riched20
		  winetricks fakechinese
		- echo "change to win10"
		  winecfg
		- 此处下载微信Windows安装包并
		- echo "install weichart"
		  env LANG="zh_CN.UTF-8" wine WeChatSetup.exe
		- echo "install front"
		  echo "LANG=zh_CN.UTF-8" >> ~/.local/share/applications/wine/Programs/微信/微信.desktop
		- echo "restart system"