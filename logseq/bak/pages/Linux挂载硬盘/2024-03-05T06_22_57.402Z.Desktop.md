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
  
  #格式化 sdxn中的n为sdx磁盘的n号分区
  mkfs.ext4 /dev/sdxn
  ```
- 挂载
- ```bash
  mount /dev/sdbx target_dir
  ```
- 自动挂载
	- 修改fstab文件，linux启动时，会从/etc/fstab自动扫描挂载。
	- `sudo vim /etc/fstab`
	- fstab中，每条配置信息都分为固定的6个部分
	  [2]:fs_file - 该字段描述希望的文件系统加载的目录点，对于swap设备，该字段为none；对于加载目录名包含空格的情况，用40来表示空格。
	  [3]:fs_type - 定义了该设备上的文件系统，一般常见的文件类型为ext4 (Linux设备的常用文件类型)、vfat(Windows系统的fat32格式)、NTFS、isoArray600等。在不确定的情况下可以使用auto。
	  [4]:fs_options - 指定加载该设备的文件系统是需要使用的特定参数选项，多个参数是由逗号分隔开来。
	  对于大多数系统使用”defaults”就可以满足需要。不多说。
	  [5]:fs_dump - 该选项被”dump”命令使用来检查一个文件系统应该以多快频率进行转储，若不需要转储就设
	  置该字段为0
	  [6]:fs_pass - 该字段被fsck命令用来决定在启动时需要被扫描的文件系统的顺序，根文件系统”/”对应该字
	  段的值应该为1，其他文件系统应该为2。若该文件系统无需在启动时扫描则设置该字段为0
	- 本例，在fstab文件中添加sdb1分区自动挂载的配置如下：
	  `/dev/sdx1 /target_dir ext4 defaults 0 0`