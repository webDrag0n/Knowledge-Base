- Anaconda是一个 #Python 包管理器
- #Anaconda升级
- Anaconda 升级时报错 `RemoveError:  'setuptools' is a dependency of conda and cannot be removed from conda's operating environment.`
	- ```bash
	  conda update --force conda
	  
	  conda install -c anaconda setuptools
	  ```
- Anaconda 新建 Jupyter Notebook kernel
	- 以添加`Torch`环境并命名为`Python (torch)`为例
	- ```bash
	  conda activate Torch
	  
	  pip install ipykernel
	  python -m ipykernel install --user --name Torch --display-name "Python (torch)"
	  ```
- Jupyter Notebook kernel 删除
	- 当不需要这个kernel虚拟环境，或者搭建的这个环境不能工作的时候我们需要删除这个虚拟环境。我们需要这样操作：
		- 打开Anaconda Prompt
		- 输入`jupyter kernelspec list`查看安装的kernel和位置
		- 根据显示的路径进入其中把文件夹删除，重启jupyter notebook即可
- Anaconda conda-forge 安装
	- 例：
	  ```bash
	  conda install -c conda-forge pytorch-tabnet
	  ```
- Anaconda创建环境：
	- 下面是创建python=3.6版本的环境，取名叫py36
	- ```bash
	  conda create -n py36 python=3.6
	  ```
-
- 删除环境（不要乱删啊啊啊）
	- ```bash
	  conda remove -n py36 --all
	  ```
-
- 激活环境
	- 下面这个py36是个环境名
	- ```bash
	  conda activate py36      (conda4之前的版本是：source activate py36 )
	  ```
-
- 退出环境
	- ```bash
	  conda deactivate    (conda4之前的版本是：source deactivate )
	  ```
	  ————————————————
	  版权声明：本文为CSDN博主「SleepingBug」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
	  原文链接：https://blog.csdn.net/H_O_W_E/article/details/77370456
- Anaconda 安装于某一环境 myenv 中
	- ```bash
	  conda install -n myenv package_name
	  ```
	-