- 在windows中安装CUDA环境，参考 [[NVIDIA]] 官方教程：[CUDA on WSL User Guide](https://docs.nvidia.com/cuda/wsl-user-guide/index.html#getting-started-with-cuda-on-wsl)
- ```bash
  wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
  sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
  wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda-repo-wsl-ubuntu-11-8-local_11.8.0-1_amd64.deb
  sudo dpkg -i cuda-repo-wsl-ubuntu-11-8-local_11.8.0-1_amd64.deb
  sudo cp /var/cuda-repo-wsl-ubuntu-11-8-local/cuda-*-keyring.gpg /usr/share/keyrings/
  sudo apt-get update
  sudo apt-get -y install cuda
  ```
- 如果遇到报错：`nvcc --version command says nvcc is not installed`
	- nano /home/$USER/.bashrc
	  Inside there add the following: (replace cuda-8.0 with your version)
	  
	  `export PATH="/usr/local/cuda-8.0/bin:$PATH"`
	  `export LD_LIBRARY_PATH="/usr/local/cuda-8.0/lib64:$LD_LIBRARY_PATH"`
	- Then do the following to save and close the editor:
	  
	   On you keyboard press the following: 
	  
	   ctrl + o             --> save 
	   enter or return key  --> accept changes
	   ctrl + x             --> close editor
	  Now either do source .bashrc or close and open another terminal
	  
	  Now run `nvcc --version`
	  
	  Information:
	  
	  .bashrc: is the file read by the terminal before opening and its found in the /home/$USER diretory of the user in question.
	  the . before the file means its hidden from view unless you instruct you file manager to show hidden files
	-