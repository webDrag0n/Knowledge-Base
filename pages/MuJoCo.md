- MuJoCo
  - Github：[https://github.com/google-deepmind/mujoco](https://github.com/google-deepmind/mujoco)
	- MuJoCo（Multi-Joint dynamics with Contact）是一个为机器人学、生物力学、图形和动画、机器学习等领域的研究和开发设计的通用物理引擎。该引擎最初由Roboti LLC开发，后来被DeepMind收购并免费提供，最终在2022年5月[开源](https://github.com/google-deepmind/mujoco/tree/main)。
- 处理接触力
	- 接触模型：
		- MuJoCo使用soft contact模型，将接触仿真转换为凸优化问题。这种模型考虑了接触面的形变，并通过引入虚拟弹簧和阻尼器来模拟这种形变。
		  接触力通过求解一个基于高斯最小拘束原理的凸优化问题来计算。这确保了接触力的平滑性和连续性，避免了在仿真中可能出现的数值不稳定性。
	- 算法细节：
		- MuJoCo使用一种名为“Complementarity-free”的方法来处理接触问题。这种方法将互补条件松弛化，并引入一个平滑的惩罚项来近似表达接触过程。
		  在接触仿真中，MuJoCo计算惯性矩阵（M）、阻尼矩阵（D）、科氏力（c）、外力（p）以及接触雅可比矩阵（JE）等参数。这些参数共同决定了仿真中物体的动态行为。
		  对于多关节系统，MuJoCo采用了一种递归算法来计算动力学状态。这种算法通过逐步计算每个关节的力和力矩，最终得到整个系统的动力学响应。
	- 实际应用：
		- MuJoCo在机器人学领域的应用非常广泛。由于其高精度和稳定性，它经常被用于控制合成、状态估计、系统识别、机构设计以及通过逆动力学进行数据分析等任务。
		  在机器学习和强化学习领域，MuJoCo也发挥了重要作用。由于其高效的仿真速度和逼真的物理效果，它成为了许多算法验证和评估的首选平台。

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