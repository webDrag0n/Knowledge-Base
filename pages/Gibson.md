- #具身智能 #仿真 #平台
- [Gibson](http://gibsonenv.stanford.edu/) 是由斯坦福大学开发的一个高保真 3D 模拟平台，专注于具身智能（Embodied AI）的研究。以下是一些关键特点和组件：
- ### 关键特点
  1. **真实世界感知**：Gibson 环境基于真实世界的 3D 扫描数据，提供高度逼真的视觉和物理模拟。这使得智能体能够在接近现实的环境中进行训练¹。
  2. **多模态传感器数据**：Gibson 提供多种传感器数据，包括 RGB、深度、表面法线和语义标签，帮助智能体更好地理解和感知环境²。
  3. **物理引擎集成**：Gibson 集成了 Bullet 物理引擎，支持刚体和软体的物理模拟，能够模拟碰撞、重力、摩擦等物理现象²。
- ### 主要组件
  1. **Gibson 平台**：一个高效的 3D 模拟器，支持多种智能体和传感器配置。它优先考虑模拟速度，适用于大规模实验¹。
  2. **Gibson 数据库**：包含超过 1400 个楼层空间和 572 个完整建筑的 3D 扫描数据，提供丰富的训练环境¹。
  3. **Goggle 合成机制**：用于缩小虚拟环境与现实世界之间的感知差距，帮助智能体更好地适应现实环境¹。
- ### 应用场景
  Gibson 主要用于以下研究任务：
- **视觉导航**：训练智能体在复杂环境中导航。
- **物体操作**：训练智能体与环境中的物体进行交互和操作。
- **问答系统**：结合自然语言处理和视觉感知，智能体根据观察和交互回答问题。
  
  Gibson 的设计理念是通过在高效模拟环境中训练智能体，然后将学到的技能转移到现实世界中，从而加速具身 AI 的研究进程¹²。
  
  Source: Conversation with Copilot, 9/19/2024
  (1) Gibson Environment | Stanford. http://gibsonenv.stanford.edu/.
  (2) Gibson Environment - Stanford University. http://gibsonenv.stanford.edu/platform/.
  (3) OmniGibson - Stanford University. https://behavior.stanford.edu/omnigibson/.
  (4) AI Habitat. https://aihabitat.org/.