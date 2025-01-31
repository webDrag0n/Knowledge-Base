- https://blog.mozui.cn/article/kms
- KMS(Key Management Service)服务是微软提供给企业内部使用的自动激活工具，在单位内部局域网中部署KMS服务后，单位内的所有计算机便可自动激活Windows系统或Office软件。市面上存在非常多的基于KMS的激活软件，这篇文章教你如何自行搭建一个KMS服务器，免去下载激活软件的工作。也提供了一个[公共KMS服务器](https://blog.kuretru.com/kms/)。
- `vlmcsd`是一个用C语言编写的KMS服务器，可以跨平台的运行在各种嵌入式设备上，项目地址：[https://github.com/Wind4/vlmcsd](https://github.com/Wind4/vlmcsd)。在这里我们直接下载编译好的二进制文件，并使用呉真制作的[systemd脚本](https://github.com/kuretru/Scripts-Collection/blob/master/files/vlmcsd/vlmcsd.service)启动vlmcsd，即可提供KMS服务。
- ```bash
  cd /usr/local
  mkdir vlmcsd && cd vlmcsd
  wget <https://github.com/Wind4/vlmcsd/releases/download/svn1113/binaries.tar.gz>
  tar -xzvf binaries.tar.gz
  ln -s binaries/Linux/intel/static/vlmcsd-x64-musl-static vlmcsd
  cd /etc/systemd/system
  wget <https://github.com/kuretru/Scripts-Collection/raw/master/files/vlmcsd/vlmcsd.service> -O vlmcsd.service
  systemctl enable vlmcsd
  systemctl start vlmcsd
  ```
  ```bash
  firewall-cmd --add-port=1688/tcp                   # for firewalld
  iptables -A INPUT -p tcp --dport 1688 -j ACCPET    # for iptables
  ```
- ### 激活Windows
  使用管理员打开cmd或Windows Power Shell，输入以下命令：
  ```bash
  slmgr.vbs -upk                      #移除原有密钥
  slmgr.vbs -ipk {对应操作系统的密钥}    #设置新密钥
  slmgr.vbs -skms kms.kuretru.com     #设置KMS服务器地址
  slmgr.vbs -ato                      #立即尝试激活
  slmgr.vbs -dlv                      #查看激活状态
  ```
- 下表为一些常见的操作系统密钥，若表中没有出现你需要的操作系统，可以在[微软官网](https://docs.microsoft.com/en-us/windows-server/get-started/kmsclientkeys)查询完整的列表。如果你不知道你的操作系统版本，可以使用`wmic os get caption`命令查询。
- |操作系统|密钥|
  |Windows 11/10 Pro|W269N-WFGWX-YVC9B-4J6C9-T83GX|
  |Windows 11/10 Enterprise|NPPR9-FWDCX-D2C8J-H872K-2YT43|
  |Windows 10 Enterprise LTSC 2021|M7XTQ-FN8P6-TTKYV-9D4CC-J462D|
  |Windows 8.1 Pro|GCRJD-8NW9H-F2CDX-CCM8D-9D6T9|
  |Windows 7 Professional|FJ82H-XT6CR-J8D7P-XQJJ2-GPDD4|
  |Windows Server Datacenter|6NMRW-2C8FM-D24W7-TQWMY-CWH2D|
  |Windows Server Standard|N2KJX-J94YW-TQVFB-DG9YT-724CC|
  |Windows Server 2022 Datacenter|WX4NM-KYWYW-QJJR4-XV3QB-6VM33|
  |Windows Server 2022 Standard|VDYBN-27WPP-V4HQT-9VMD4-VMK7H|
-