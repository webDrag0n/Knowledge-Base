- #Java
- ## java jps命令使用解析
- https://blog.csdn.net/wo541075754/article/details/55095443
- 在linux环境下显示一个进程的信息大家可能一直都在使用ps命令，比如用以下命令来显示当前系统执行的java进程：
- ```bash
  ps -ef | grep java
  ```
- 针对java的进程，jdk1.5以后提供了一个查看当前所有java进程pid的小工具。
- ### 位置
	- `JAVA_HOME/bin/`目录下面
- ### 功能
	- jps(Java Virtual Machine Process Status Tool)是JDK 1.5提供的一个显示当前所有java进程pid的命令，简单实用，非常适合在linux/unix平台上简单察看当前java进程的一些简单情况。
- ### 使用
	- 先执行`jps –help`查看一下此命令的使用方法
- 先执行jps –help 查看一下此命令的使用方法
- ```bash
  # jps -help
  usage: jps [-help]
       jps [-q] [-mlvV] [<hostid>]
  
  Definitions:
    <hostid>:      <hostname>[:<port>]
  ```
- 具体 [options]选项解析：
  -q：仅输出VM标识符，不包括classname,jar name,arguments in main method；
  -m：输出main method的参数；
  -l：输出完全的包名，应用主类名，jar的完全路径名；
  -v：输出jvm参数 ；
  -V：输出通过flag文件传递到JVM中的参数(.hotspotrc文件或-XX:Flags=所指定的文件 ；
  
  实例
  jps命令：
  ```bash
  [root@119 app]# jps
  16464 jar
  2300 jar
  ```
- jps -q：
  ```bash
  [root@119 app]# jps -q
  16464
  2300
  ```
  
  jps -m
  
  ```bash
  [root@119 app]# jps -m
  16464 jar
  2300 jar
  ```
  
  jps -l
  
  [root@119 app]# jps -l
  16464 test-1.0.0-SNAPSHOT.jar
  9671 sun.tools.jps.Jps
  1
  2
  3
  当然，也可以组合使用参数，比如
  
  jps -ml
  1
  特殊说明
  jps仅查找当前用户的Java进程，而不是当前系统中的所有进程。