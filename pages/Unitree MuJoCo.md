- #MuJoCo #Unitree
- Github: https://github.com/unitreerobotics/unitree_mujoco
- ## 安装
- 安装Unitree MuJoCo之前需要先构建并安装 [[Unitree sdk2]] 和 [[MuJoCo]]，安装步骤详见各自页面
- 安装yaml-cpp用于配置文件读取：
  ```bash
  apt install libyaml-cpp-dev
  ```
- 编译unitree_mujoco:
  ```bash
  cd unitree_mujoco/simulate
  mkdir build && cd build
  cmake ..
  make -j4
  ```
- 注意如果在`make -j4`步骤报错：`cannot find -lddsc&ddscxx`，需要编辑`unitree_mujoco/simulate/CMakeLists.txt`，将：
  ```cmake
  find_package(mujoco REQUIRED)
  include_directories(/usr/local/include/ddscxx /usr/local/include/iceoryx/v2.0.2)
  link_libraries(unitree_sdk2 ddsc ddscxx rt pthread)
  ```
  改为
  ```cmake
  find_package(mujoco REQUIRED)
  find_package(unitree_sdk2 REQUIRED)
  include_directories(/usr/local/include/ddscxx /usr/local/include/iceoryx/v2.0.2)
  link_libraries(unitree_sdk2 ddsc rt pthread)
  ```
  即可正常编译
- 测试：
  ```bash
  ./unitree_mujoco
  ```
- 在新终端中执行：
  ```bash
  ./test
  ```
- 如需使用python3进行控制代码编写，需要安装 [[Unitree sdk2 python]]
  并安装mujoco python和pygame（用于手柄控制）
  ```bash
  pip3 install mujoco
  pip3 install pygame
  ```