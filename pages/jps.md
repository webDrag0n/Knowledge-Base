- #Java
- ## # java jps命令使用解析
- 在linux环境下显示一个进程的信息大家可能一直都在使用ps命令，比如用以下命令来显示当前系统执行的java进程：
- ```bash
  ps -ef | grep java
  ```
- 针对java的进程，jdk1.5以后提供了一个查看当前所有java进程pid的小工具。
- ### 位置
  `JAVA_HOME/bin/`目录下面
- ### 功能
  jps(Java Virtual Machine Process Status Tool)是JDK 1.5提供的一个显示当前所有java进程pid的命令，简单实用，非常适合在linux/unix平台上简单察看当前java进程的一些简单情况。
- ### 使用
  先执行jps –help 查看一下此命令的使用方法