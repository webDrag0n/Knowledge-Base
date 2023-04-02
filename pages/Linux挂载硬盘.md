- #Linux
- 查看已安装硬盘
- ```bash
  fdisk -l
  
  lsblk -f
  ```
- 以下假设选择`/dev/sdx`硬盘进行挂载
- 磁盘分区
- ```bash
  parted /dev/sdx
  
  
  ```
- 挂载
- ```bash
  mount 
  ```