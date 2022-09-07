- Anaconda是一个 #Python 包管理器
- #Anaconda升级
- Anaconda 升级时报错 `RemoveError:  'setuptools' is a dependency of conda and cannot be removed from conda's operating environment.`
	- ```bash
	  conda update --force conda
	  
	  conda install -c anaconda setuptools
	  ```
- Anaconda 新建 Jupyter Notebook kernel
	- ```bash
	  pip install ipykernel
	  python -m ipykernel install --user --name torch --display-name "Python (torch)"
	  ```
- Anaconda conda-forge 安装
	- 例：
	  ```bash
	  conda install -c conda-forge pytorch-tabnet
	  ```
- Anaconda 安装于某一环境 myenv 中
	- ```bash
	  conda install -
	  ```