- Anaconda是一个 #Python 包管理器
- #Anaconda升级
- Anaconda 升级时报错 `RemoveError:  'setuptools' is a dependency of conda and cannot be removed from conda's operating environment.`
	- ```bash
	  conda update --force conda
	  
	  conda install -c anaconda setuptools
	  ```
- Anaconda 新建 ip