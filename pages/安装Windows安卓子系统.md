- 参考： https://zhuanlan.zhihu.com/p/424959704
- ### 一、安装 Windows 虚拟化支持
	- 进入设置 → 应用 → 可选功能 → 更多 Windows 功能，找到并勾选开启**「Hyper-V」**和**「虚拟机平台」**两个选项，安装完成后会提示重启系统。
	- ![](https://pic1.zhimg.com/80/v2-94e54296c8974dd87a5d281d6a258cd0_1440w.jpg)
- ### 二、Win11 正式版安装安卓子系统方法教程 (离线包安装)
	- 如果你使用的是Windows 11正式版，不想换到测试版或者修改系统区域，可以使用“下载WSA离线安装包”的方法安装部署安卓子系统，可以直接绕过地区和测试版限制，在Win11正式版上完成安装。
	- WSA安卓子系统的应用离线安装包是从Windows中的微软应用商店中提取的，可以通过命令行安装。
		- 1.  打开 [https://store.rg-adguard.net](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/%3Fgolink%3DaHR0cHM6Ly9zdG9yZS5yZy1hZGd1YXJkLm5ldC8%3D)
		- 2.  输入 [https://www.microsoft.com/store/productid/9p3395vx91nr](https://link.zhihu.com/?target=https%3A//www.microsoft.com/store/productid/9p3395vx91nr) 选择 Slow，点击对勾
		- 3.  最下方找到文件：MicrosoftCorporationII.WindowsSubsystemForAndroid_1.7.32815.0_neutral___8wekyb3d8bbwe，然后开始下载。(如日后更新，你下载到的文件命名/版本号可能有所不同)
		- 4.  右键点击此文件，在菜单中选择「复制文件地址」
		- 5.  右键点击「Windows 开始菜单图标」，点击「Windows 终端 (管理员)」
		- 6.  在弹出来的 PowerShell 命令行界面中，输入以下命令：
	- ```
	  # 安装命令如下：
	  Add-AppxPackage 鼠标点右键会自动粘贴安装包文件路径
	  # 看起来大概是这样的 (示例，请确保你的路径正确)：
	  Add-AppxPackage "D:\文件所在的路径\wsa.Msixbundle"
	  # 然后回车开始进行安装
	  ```
	- 回车之后就开始安装，等待安装完成就可以了。
	- ![](https://pic4.zhimg.com/80/v2-ad990d305745d2b996bc1d68aa856d73_1440w.jpg)
	- 安装完成后，可以在Windows开始菜单中找到「Windows Subsystem for Android」的应用图标。
	- ![](https://pic2.zhimg.com/80/v2-9f60bf0a3839af630b3b112a85a521a1_1440w.jpg)
- ### 三、在Win11 安卓子系统安装 APK 软件包教程
	- 相比鸡肋的亚马逊应用商店，如果能在Win11上随意安装任何第三方安卓APK安装包，都是这款安卓子系统最正确的使用姿势！其实在ADB命令的帮助下，在Windows 11上安装APK并不难，让我们来看看吧。
	- ### Windows 11 WSA 安装 APK 方法：
		- 1.  打开 WSA 安卓子系统设置页面，打开「**开发人员模式**」 选项
		- ![](https://pic1.zhimg.com/80/v2-f982eeb4fe520c0ca402c95b14f6c3f4_1440w.jpg)
			- 1.  记下上图设置项中显示出来的 WSA 的内部 IP 地址和端口号，如 `127.0.0.1:58526`
			- 2.  [下载安卓 ADB 命令行调试工具](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/1346.html)，并参照文章教程，将 `adb` 命令加入到系统环境变量
			- 3.  打开 Windows 终端 (命令行)，输入以下命令：
		- ```
		  # 第 0 步：确保已正确将 adb 命令加入到系统的环境变量
		  # 执行下面的命令能看到 adb 版本号则表示 ok
		  # 如有错误，请检查环境变量是否配置正确
		  adb version
		  # 第 1 步：连接 WSA
		  adb connect 127.0.0.1:58526
		  # 其中 127.0.0.1:58526 是刚才在 WSA 设置项中看到的 IP
		  # 第 2 步：安装 APK
		  # 连接成功之后，就能用下面命令来安装 APK 了
		  adb install 你的APK文件完整路径
		  # 注意 .apk 的路径最好无中文且无空格，否则需要用英文双引号包裹。
		  # 你可在资源管理器上右键点击 apk 文件选「复制文件地址」获取完整路径
		  #下面是例子：
		  adb install d:\download\apk\weixin.apk
		  adb install "d:\下载\简而易 jianeryi.com\qq.apk"
		  # 最后按下回车即可安装
		  # 安装完成后，在 Windows 开始菜单的“所有应用”里就能找到你安装的 Android 应用
		  ```
		- 这样就能使用 adb 命令安装 apk 文件到 Windows 11 安卓子系统 WSA 了。重点是开启开发者模式，获得正确 IP 地址以及正确安装 adb 命令。
- ### Windows 11上成功运行安卓APP
	- 经过测试，很多常用的安卓应用都能正常运行，流畅度不错，[性能](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/tag/%25E6%2580%25A7%25E8%2583%25BD)令人满意！秒杀很多模拟器！而且安卓程序和Win11联动集成的体验也很好，甚至可以用Win 11的输入法直接在APP中打字，剪贴板也是可以互通的。
	- ![](https://pic1.zhimg.com/80/v2-3db0baf2dd416966b66ee772fa6f640c_1440w.jpg)
- ### 安装国内的 Android 应用商店
	- 每次安装软件的时候使用adb命令比较麻烦。为了更方便地下载常用的安卓应用，我们可以在WSA安装一个国内的应用商店，比如应用宝、酷安应用市场等，然后通过它快速搜索下载各种常用的安卓应用和游戏。
	- 更重要的是，似乎酷安还可以用来管理和卸载已安装的APP程序。除了一些不包含在商店中的应用程序，它们需要通过apk文件安装，其他的基本上不需要使用命令行。
- ### Windows11 – 安卓子系统的特色
	- 支持将安卓 App 固定到开始菜单或任务栏，并通过鼠标、触摸或笔输入与它们交互。
	- 安卓 App 可集成到 Alt + Tab 和任务视图中，并能在 App 之间快速切换。
	- 可在操作中心中查看安卓 App 的推送通知，或在 Windows 应用程序和安卓 App 之间共享剪贴板。
	- 微软还添加了无障碍体验，许多 Windows 辅助功能设置都适用于安卓 App。
- ### 总结
	- 与[虚拟机](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/tag/%25E8%2599%259A%25E6%258B%259F%25E6%259C%25BA)或第三方安卓模拟器相比，微软官方的 Windows 11安卓子系统 在性能和与系统的集成上更为优越！非常实用，可以让安卓生态软件完美扩展到PC。
	- 相信随着Windows 11正式版的发布，以及Android子系统的不断完善和[优化](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/tag/%25E4%25BC%2598%25E5%258C%2596)，将为用户打开一扇通往安卓与Windows紧密合作的新世界的大门。就像[苹果Mac](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/mac)可以安装iOS应用一样，未来在PC上安装安卓移动应用将非常普遍。
- ### 使用虚拟机安装与尝鲜
	- Windows：[VMware Workstation](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/2261.html)（最强虚拟机软件）丨[VMWare Player](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/vmware-workstation-player.html)（免费）
	- MacOS：[Parallels Desktop 虚拟机](https://link.zhihu.com/?target=https%3A//www.jianeryi.com/1828.html)（推荐）