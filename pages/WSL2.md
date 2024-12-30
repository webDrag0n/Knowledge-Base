- #WSL
- 启用windows虚拟机功能
  ```bash
  dism.exe /Online /Enable-Feature /FeatureName:VirtualMachinePlatform /All
  ```
- 如何启用wsl2：
	- https://segmentfault.com/a/1190000040143442
	- 想要在Windows 10上启用WLS2，需要满足以下条件：
	  Windows 10 版本 1903 Build 19362，或高于该版本
	  如果是ARM64的系统，则需要版本2004 Build 19041，或高于该版本 　
	  步骤一　- 为WSL启用Windows服务
	  想要在Windows 10上运行WSL，首先需要启用Windows上的一些服务，这些服务默认是关闭的。
	  开始菜单，搜索 PowerShell，右键 PowerShell，选择使用管理员运行。
	  ```bash
	  run-powershell
	  ```
	- 在打开的 PowerShell 终端，执行如下命令：
	  ```bash
	  PS C:\Windows\system32> dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
	  ```
	  [dism.exe]是Windows的部署映像服务和管理工具，上面的命令开启了WSL的功能。
	- 以上命令执行成功之后，继续执行如下命令来开启Hyper-V的功能
	  ```bash
	  PS C:\Windows\system32> dism.exe /online /enable-feature /featurename:VirutalMachinePlatform /all /norestart
	  ```
	  完成以上操作之后，需要重启Windows操作系统，重启之后再次登陆系统。
	  接下来需要从微软下载一个最新的Linux内核升级包并安装，下载安装包 wsl_update_x64.msi，下载完成后直接安装。
	- 完成之后，以管理员身份运行 PowerShell，执行如下命令来设置wsl使用的默认版本
	- ```bash
	  PS C:\Windows\system32> wsl --set-default-version 2
	  ```
	  这里我们将默认设置为 wsl 2 。
	- 上述步骤就完成了WSL2的启用，接下来将使用WSL2安装基于Linux的发行版本（Ubuntu 20.04）。
	  步骤二　- 使用WSL安装Ubuntu 20.04
	  在开启WSL功能之后，安装一个Linux的分发版很简单，只需要打开Windows应用商店（Microsoft Store），这里我们将安装Ubuntu 20.04分发版。
	- microsoft-store
	- 打开应用商店之后，直接在应用商店中搜索 Linux ，将看有很多分发版本的选项，这里选择 Ubuntu 20.04，点击 获取 将应用加入账号，然后在点击 安装 按钮进行安装
	  ```bash
	  install-ubuntu
	  ```
	- 安装完成之后，就可以点击 启动 运行Ubuntu子系统，第一次运行需要一些时间来进行初始化配置，然后会提示输入Linux系统的用户名和密码。
	  这里的用户名和秘密不需要与Windows系统的用户名和密码一致，但可以通过sudo来获取管理权限。
	  ```bash
	  ubuntu-init
	  ```
	- 当完成初始化之后，就可以使用该Linux子系统了，当然是以终端的方式。
	  步骤三 - 安装Wdindows终端应用（Windows Terminal）
	  安装的Ubuntu子系统提供了一个默认的终端，不过微软开源了一个Windows上的终端工具 - Windows Terminal，该工具支持很多自定义配置，同时支持Windows的Powershell，也支持Linux子系统，因此可以安装使用。
	- 直接在应用商店搜索 Terminal ，选择 Windows Terminal 进行安装，安装完成之后可通过开始菜单启动
	- windows-termial
	- Windows Terminal默认是打开Powershell的，不过其支持多标签，点击标题栏上 + 服务旁边的下拉按钮，选择Ubuntu-20.04，新标签就会打开Ubuntu的这个子系统终端
	- termianl-ubuntu
	- Windows Termial支持很多自定义配置，具体请参考其文档。