- #Unitree sdk2 #Python
- GitHub：[https://github.com/unitreerobotics/unitree_sdk2_python](https://github.com/unitreerobotics/unitree_sdk2_python)
- ## 安装
- ```bash
  git clone https://github.com/unitreerobotics/unitree_sdk2_python.git
  cd unitree_sdk2_python
  pip3 install -e .
  ```
- 如果安装中出现错误：
  `Could not locate cyclonedds. Try to set CYCLONEDDS_HOME or CMAKE_PREFIX_PATH`
  需要编译安装cyclonedds：
  ```bash
  git clone https://github.com/eclipse-cyclonedds/cyclonedds -b releases/版本号如0.10.x 
  cd cyclonedds && mkdir build install && cd build
  cmake .. -DCMAKE_INSTALL_PREFIX=../install
  cmake --build . --target install
  ```
  回到unitree_sdk2_python目录：
  ```bash
  cd ~/unitree_sdk2_python
  export CYCLONEDDS_HOME="~/cyclonedds/install" # 替换为你的cyclonedds安装目录
  pip3 install -e .
  ```
-