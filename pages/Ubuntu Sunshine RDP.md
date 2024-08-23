## Sunshine远程桌面
- 可用于Ubuntu22.04 / 24.04
- Github：https://github.com/LizardByte/Sunshine
- ## 安装步骤
- ```bash
  cd ~
  # 下载合适版本
  wget https://github.com/LizardByte/Sunshine/releases/download/v0.23.1/sunshine-ubuntu-22.04-amd64.deb
  dpkg
  
  # 安装
  dpkg -i sunshine-ubuntu-22.04-amd64.deb
  
  # 修复依赖
  sudo apt install -f
  
  # 运行
  sunshine
  ```