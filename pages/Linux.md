- ## 一些重要文件的名字，位置与功能
	- etc
		- bash.bashrc
		  id:: 62eb946d-a94f-4486-880a-06594b75aec2
			- 当交互式终端打开时被执行，默认会引用并执行 ((62eb948c-87d4-4004-8131-6dcd549c8e0a))
		- profile
		  id:: 62eb948c-87d4-4004-8131-6dcd549c8e0a
			- 当ssh登录发生时被执行
- ## 安全
	- [[Linux分用户日志]]
	- [[Linux权限管理]]
- ## 服务搭建
	- [[FTP服务器搭建]]
- ## Linux安装Windows应用
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