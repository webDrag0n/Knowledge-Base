- #Python #JupyterHub
- ⚠如无必要请不要使用该JupyterHub，此项目旨为提供一个JupyterHub的最小安装，生产环境请参考 ((63e1f57a-98bf-418d-bd6f-011b9c45744d))
- # 安装
	- ```bash
	  sudo apt install python3 python3-dev git curl
	  curl -L https://tljh.jupyter.org/bootstrap.py | sudo -E python3 - --admin <admin-name>
	  ```
	- 注：当网络不佳导致curl下载卡顿时可以尝试在网页端打开并复制粘贴文本至同名文件，使用`sudo -E python3 bootstrap.py --admin <admin-name>`进行第二阶段
- # 停止与重启
	- ## 停止
	- ```bash
	  systemctl stop jupyterhub.service
	  ```
	- ## 重启
	- ```bash 
	  # 重启Traefik服务
	  sudo tljh-config reload proxy
	  # 重启jupyter hub
	  sudo tljh-config reload hub
	  ```
- # 移除
- 参考：[What does the installer do?](https://tljh.jupyter.org/en/latest/topic/installer-actions.html)
- ```bash
  sudo rm -rf /opt/tljh/hub
  ```
- ```bash
  sudo rm -rf /opt/tljh/user
  ```
- ```bash
  sudo unlink /usr/bin/tljh-config
  ```
- ```bash
  sudo rm -rf /opt/tljh/config
  ```
- ```bash
  # stop the services
  systemctl stop jupyterhub.service
  systemctl stop traefik.service
  systemctl stop jupyter-<username>
  
  # disable the services
  systemctl disable jupyterhub.service
  systemctl disable traefik.service
  # run this command for all the Jupyter users
  systemctl disable jupyter-<username>
  
  # remove the systemd unit
  rm /etc/systemd/system/jupyterhub.service
  rm /etc/systemd/system/traefik.service
  
  # reset the state of all units
  systemctl daemon-reload
  systemctl reset-failed
  ```