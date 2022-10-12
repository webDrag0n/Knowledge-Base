- ## 发行版本
	- [[Windows10]]
	- [[Windows11]]
- ## Windows Subsystem for Linux
	- [[WSL]]
- ## 蓝屏修复
- Win10引导失效报错0x00000e：
  collapsed:: true
	- 使用Win10启动盘启动，选择语言并下一步后，点击修复计算机，然后进入命令行
	- bootrec /rebuildbcd
	- ```cmd
	  bootrec /rebuildbcd
	  exit
	  ```
	- 关机
	- 拔掉启动盘然后重启
- ## 重装系统
- [[Windows系统重装]]
- ## 系统信息
	- ### 硬盘测速
		- ```cmd
		  winsat disk -t > c:\
		  ```
	- 硬盘通电时间检测
		- 使用[CrystalDiskMark](https://crystalmark.info/en/software/crystaldiskmark/)