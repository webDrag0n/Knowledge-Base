- ## 发行版本
	- [[Windows10]]
	- [[Windows11]]
- ## Windows Subsystem for Linux
	- [[WSL]]
- ## 蓝屏修复
- Win10引导失效报错0x00000e：
	- 使用Win10启动盘启动，选择语言并下一步后，点击修复计算机，然后进入命令行
	- bootrec /rebuildbcd
	- ```cmd
	  bootrec /rebuildbcd
	  exit
	  ```
	- 关机
	- 拔掉启动盘然后重启
-