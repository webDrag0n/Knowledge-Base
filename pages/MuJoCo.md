- Github：[https://github.com/google-deepmind/mujoco](https://github.com/google-deepmind/mujoco)
- ## 安装
- ```bash
  apt install libglfw3-dev libxinerama-dev libxcursor-dev libxi-dev
  # 配置文件读取使用yaml-cpp
  apt install libyaml-cpp-dev
  git clone https://github.com/google-deepmind/mujoco.git
  mkdir build && cd build
  cmake ..
  make -j4
  sudo make install
  ```
- 测试：
- ```bash
  simulate
  ```
-