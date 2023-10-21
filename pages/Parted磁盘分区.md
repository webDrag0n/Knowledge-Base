- #Parted #磁盘 #分区
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
  
  #格式化 sdxn中的n为sdx磁盘的n号分区
  mkfs.ext4 /dev/sdxn
  ```