- ### 架构设计
- ### 游戏机制
	- 终端机黑入：
		- 终端机黑入是游戏中最核心的玩法机制，通过黑入终端机，玩家可以获得新的权限点数，在终端机附近会划出警戒区，玩家在警戒区内进入摄像头或公司士兵视野时，警惕值会上涨，警惕值满直接游戏失败读档，士兵与摄像头都有巡逻规律供玩家钻空子。终端机初始对玩家隐藏位置，通过士兵巡逻的密度，周围环境线索等信息启发玩家找到终端机，在找到终端机并靠近开始终端机黑入以后启动黑入小游戏，在黑入
- ### 剧情大纲
	-
- ### 跨场景传递变量
  id:: 6249b6e8-7d0e-4d71-98fe-2ec62347b8f5
  heading:: true
	- [What is the proper way to handle data between scenes?](https://gamedev.stackexchange.com/questions/110958/what-is-the-proper-way-to-handle-data-between-scenes)
- Scriptable Object
	- [https://www.youtube.com/watch?v=WLDgtRNK2VE](https://youtu.be/WLDgtRNK2VE) demo
	- https://youtu.be/7jxS8HIny3Q detailed explained
- ### 多线程
- Unity中可以编写c#脚本实现多线程，但是Unity本身的组件不支持线程安全，需要自行编写
	- https://docs.unity3d.com/Manual/JobSystemMultithreading.html
-
- Unity相关项目
	- [[FUNCTION开发日志]]