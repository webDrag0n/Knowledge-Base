- ### 安装
	- https://hackeradam.com/post/install-dwm-ubuntu-20.10/
	- ```bash
	  sudo apt-get install build-essential libx11-dev libxinerama-dev sharutils suckless-tools libxft-dev stterm
	  
	  cd /usr/local/src
	  sudo wget http://dl.suckless.org/dwm/dwm-6.3.tar.gz
	  sudo tar xvzf dwm-6.3.tar.gz
	  chown -R `id -u`:`id -g` dwm-6.3
	  
	  cd dwm-6.3/
	  sudo make clean install
	  
	  sudo apt install dwm
	  sudo cp /usr/share/xsessions/dwm.desktop{,.bak}
	  sudo apt purge dwm
	  sudo mv /usr/share/xsessions/dwm.desktop{.bak,}
	  ```
	- 安装完成后登出当前窗口管理器或重启，在登录界面选择dwm登入即可
- ### 基本用法
	- Alt + Shift + Enter: Launch Terminal
	  Alt + Shift + C: Kill current Client
	  Alt + t: Switch to a Tile Layout
	  Alt + m: Switch to a Monocle Layout
	  Alt + f: Switch to a Floating Layout
	  Alt + p: Launch the demnu
	  Alt + [0-9]: Switch to tag [0-9]
	  Alt + Shift + Q: Quit DWM
- [Change the Suckless DWM Wallpaper with Feh](https://www.yanboyang.com/dwmwallpaper/)