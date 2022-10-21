- #Chrome
- [Official Website](https://sites.google.com/chromium.org/driver/getting-started)
- ## 下载
- [chromedriver下载与安装方法，亲测可用](https://blog.csdn.net/zhoukeguai/article/details/113247342)
- chromedriver下载地址：
- [http://chromedriver.storage.googleapis.com/index.html](http://chromedriver.storage.googleapis.com/index.html)
- [http://npm.taobao.org/mirrors/chromedriver/](http://npm.taobao.org/mirrors/chromedriver/)
- 把exe文件复制到浏览器的安装目录下：C:\Program Files (x86)\Google\Chrome\Application
  （要根据自己实际安装目录）
- 把exe文件复制到python的安装目录下
- 配置环境变量:此电脑→右击属性→高级系统设置→环境变量→**用户变量**→Path→编辑→新建，将以下路径复制,然后不要忘记后续全部点击确定
- 打开pycharm,输入以下代码，测试一下是否驱动成功
- from selenium import webdriver
- driver = webdriver.Chrome()
  url = 'https://www.csdn.net/'
  driver.get(url)
  driver.maximize_window()
- 成功!!