- #具身智能 #仿真 #平台
- [AI2-THOR](https://ai2thor.allenai.org/) 是由 Allen Institute for AI 开发的一个开源平台，专门用于视觉 AI 和具身智能（Embodied AI）的研究。以下是一些关键特点和组件：
- ### 关键特点
  1. **多样化的环境**：AI2-THOR 提供了 200 多个高质量的 3D 场景，包括厨房、卧室、浴室和客厅等¹。这些场景中包含超过 2000 个独特的物体，支持物理模拟和交互。
  2. **多智能体支持**：平台支持多种智能体类型，如人形机器人、无人机等，能够在单个场景中进行多智能体协作²。
  3. **丰富的交互**：AI2-THOR 提供了 200 多种动作，支持广泛的交互和导航任务²。这些动作包括物体操作、导航、状态变化（如开/关、热/冷）等。
- ### 主要组件
  1. **iTHOR**：一个高层交互框架，适用于具身常识推理研究。它包含 120 个房间和 2000 多个独特物体，支持物理交互和状态变化¹。
  2. **RoboTHOR**：一个中层交互框架，专注于物体操作任务。它使用 LoCoBot 机器人和 Kinect 相机，提供 89 个公寓和 600 多个物体的物理和模拟对照环境¹。
  3. **ManipulaTHOR**：一个专门用于视觉物体操作的环境，使用机械臂进行物体操作任务²。
- ### 应用场景
  AI2-THOR 主要用于以下研究任务：
- **视觉导航**：训练智能体在复杂环境中导航。
- **物体操作**：训练智能体与环境中的物体进行交互和操作。
- **问答系统**：结合自然语言处理和视觉感知，智能体根据观察和交互回答问题。
  
  AI2-THOR 的设计理念是通过在高效模拟环境中训练智能体，然后将学到的技能转移到现实世界中，从而加速具身 AI 的研究进程³⁴。
  
  Source: Conversation with Copilot, 9/19/2024
  (1) AI2-THOR. https://ai2thor.allenai.org/.
  (2) allenai/ai2thor: An open-source platform for Visual AI. - GitHub. https://github.com/allenai/ai2thor.
  (3) AI2-THOR: A virtual environment for training home assistant robots. https://unity.com/resources/ai2-thor-session.
  (4) Allen Institute Launches Updated Embodied AI Challenge. https://www.infoq.com/news/2022/03/ai2-thor-challenge/.
  (5) AI2-THOR: An Interactive 3D Environment for Visual AI - ar5iv. https://ar5iv.labs.arxiv.org/html/1712.05474.
  (6) undefined. http://ai2thor.allenai.org.