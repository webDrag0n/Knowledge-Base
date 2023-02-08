- # JupyterHub安装
  id:: 63e1f57a-98bf-418d-bd6f-011b9c45744d
	- ## 直接安装
		- [Quickstart](https://jupyterhub.readthedocs.io/en/stable/quickstart.html)
		- 使用 `pip`
		  ```bash
		  sudo apt-get install nodejs npm
		  python3 -m pip install jupyterhub
		  npm install -g configurable-http-proxy
		  python3 -m pip install jupyterlab notebook  # needed if running the notebook servers in the same environment
		  ```
		- 使用 `conda` （conda自带nodejs）
		- ```bash
		  conda install -c conda-forge jupyterhub  # installs jupyterhub and proxy
		  conda install jupyterlab notebook  # needed if running the notebook servers in the same environment
		  ```
		- 测试
		  ```bash
		  conda install -c conda-forge jupyterhub  # installs jupyterhub and proxy
		  conda install jupyterlab notebook  # needed if running the notebook servers in the same environment
		  ```
	- ## Docker镜像
-