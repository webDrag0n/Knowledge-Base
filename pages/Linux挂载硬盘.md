- #Linux
- 查看已安装硬盘
- ```bash
  fdisk -l
  
  lsblk -f
  ```
- 以下假设选择`/dev/sdx`硬盘进行挂载
- 磁盘分区，参考[linux新增大于2T硬盘，分区并挂载](https://blog.csdn.net/u012150360/article/details/81333051)
- ```bash
  parted /dev/sdx
  
  
  ```
- 挂载
- ```bash
  mount 
  ```