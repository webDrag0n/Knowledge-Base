- #Linux #so链接库
- 参考：[备忘：gcc在linux下打包so库并调用](https://blog.csdn.net/zuguorui/article/details/96330102)
- 环境：Ubuntu， GCC
- 切换到准备编译的代码文件夹中，输入g++ *.cpp -fPIC -shared -o libname.so，name随便起，这时会生成一个libname.so文件。
- 把so文件复制到准备用的工程中。在该工程位置打开终端，首先在ubuntu环境下要设置库的路径：export LD_LIBRARY_PATH=./，否则在运行时会出现找不到库的错误，别的环境下是否需要暂时不知道。然后连接并编译工程：g++ *.cpp -L. -lname -o main，注意-l后面直接跟的库的名字，没有空格，去掉lib和.so。最后运行：./main。
- ---
- 版权声明：本文为CSDN博主「zuguorui」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
  原文链接：https://blog.csdn.net/zuguorui/article/details/96330102