- #Linux
- 参考[Ubuntu根目录满了怎么扩容](https://juejin.cn/s/Ubuntu%E6%A0%B9%E7%9B%AE%E5%BD%95%E6%BB%A1%E4%BA%86%E6%80%8E%E4%B9%88%E6%89%A9%E5%AE%B9)
- 当硬盘信息如下所示，在sda3下的`ubuntu--vg-ubuntu--lv`仅占据了100G/462.7G
- ```bash
  $ lsblk
  NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
  sda                         8:0    0 465.8G  0 disk
  ├─sda1                      8:1    0     1G  0 part /boot/efi
  ├─sda2                      8:2    0     2G  0 part /boot
  └─sda3                      8:3    0 462.7G  0 part
    └─ubuntu--vg-ubuntu--lv 253:0    0   100G  0 lvm 
  ```
- 查看是否为lvm分区
- ```bash
  $ sudo lvscan
   ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [<462.71 GiB] inherit
  ```
- 使用以下命令扩展Ubuntu根分区（此处为扩展至最大）：
- ```bash
  sudo lvextend -r -l +100%FREE /dev/ubuntu-vg/root
  ```