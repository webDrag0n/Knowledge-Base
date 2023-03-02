- #Jupyter Notebook
  参考：https://www.jianshu.com/p/8fc3cd032d3c
- ### 方法1. ssh远程使用jupyter notebook
	- 1.  在远程服务器上，启动jupyter notebooks服务：
	- ```
	  jupyter notebook --no-browser --port=8889
	  ```
		- 2.  在本地终端中启动SSH：
	- ```
	  ssh -N -f -L localhost:8888:localhost:8889 username@serverIP
	  ```
	- 其中： -N 告诉SSH没有命令要被远程执行； -f 告诉SSH在后台执行； -L 是指定port forwarding的配置，远端端口是8889，本地的端口号的8888。
	- > 注意：username@serverIP替换成服务器的对应账号。
		- 3.  最后打开浏览器，访问：[http://localhost:8888/](http://localhost:8888/)
- ### 方法2. 利用jupyter notebook自带的远程访问功能
	- 官方指南在此：[官方指南](http://jupyter-notebook.readthedocs.io/en/latest/public_server.html#notebook-server-security)
		- 1.  生成默认配置文件
			- `jupyter notebook --generate-config`
		- 2.  生成访问密码(token)
			- 终端输入`ipython`，设置你自己的jupyter访问密码，注意复制输出的`sha1:xxxxxxxx`密码串
	- ```
	  In [1]: from notebook.auth import passwd
	  In [2]: passwd()
	  Enter password:
	  Verify password:
	  Out[2]: 'sha1:xxxxxxxxxxxxxxxxx'
	  ```
		- 3.  修改`./jupyter/jupyter_notebook_config.py`中对应行如下
	- ```
	  c.NotebookApp.ip='*'
	  c.NotebookApp.password = u'sha:ce...刚才复制的那个密文'
	  c.NotebookApp.open_browser = False
	  c.NotebookApp.port =8888 #可自行指定一个端口, 访问时使用该端口
	  ```
		- 4.  在服务器上启动`jupyter notebook`
			- `jupyter notebook`
		- 5.  最后打开浏览器，访问：[http://ip:8888/](http://ip:8888/)
	- 作者：ibunny
	- 链接：https://www.jianshu.com/p/8fc3cd032d3c
	- 来源：简书
	- 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。