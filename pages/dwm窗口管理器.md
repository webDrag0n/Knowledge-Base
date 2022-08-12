- ### 安装
	- https://hackeradam.com/post/install-dwm-ubuntu-20.10/
	- ```bash
	  sudo apt-get install build-essential libx11-dev libxinerama-dev sharutils suckless-tools libxft-dev stterm
	  
	  cd /usr/local/src
	  sudo wget http://dl.suckless.org/dwm/dwm-6.2.tar.gz
	  sudo tar xvzf dwm-6.2.tar.gz
	  chown -R `id -u`:`id -g` dwm-6.2
	  
	  cd dwm-6.2/
	  sudo make clean install
	  
	  
	  ```