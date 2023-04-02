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
  
  #对磁盘信息进行查看
  (parted) print
  
  (parted) mklabel gpt
  
  #(parted) mkpart primary 下限% 上限%
  (parted) mkpart primary 0% 24%
  (parted) mkpart primary 25% 100%
  
  #再次确认
  (parted) print
  
  #退出parted
  (parted) q
  
  #格式化
  mkfs.ext4 /dev/sdbx
  ```
- 挂载
- ```bash
  mount 
  ```