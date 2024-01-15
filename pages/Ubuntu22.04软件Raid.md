title:: Ubuntu22.04软件Raid

- #Raid #Ubuntu
- 参考：https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-22-04#creating-a-complex-raid-10-array
- use mdadm in ubuntu
	- check for the drives whether there is already any raid existed before creating a new one.
	- [[Linux硬盘分区]] 不要格式化
	- mdadm检查分区
		- ```bash
		  $> sudo mdadm -E /dev/sd[b-e]
		  $> sudo mdadm --examine /dev/sdb /dev/sdc /dev/sdd /dev/sde
		  
		  # 输出
		  /dev/sdc:
		     MBR Magic : aa55
		  Partition[0] :   4294967295 sectors at            1 (type ee)
		  /dev/sde:
		     MBR Magic : aa55
		  Partition[0] :   4294967295 sectors at            1 (type ee)
		  /dev/sdd:
		     MBR Magic : aa55
		  Partition[0] :   4294967295 sectors at            1 (type ee)
		  /dev/sdg:
		     MBR Magic : aa55
		  Partition[0] :   4294967295 sectors at            1 (type ee)
		  ```
	- 建立raid10
		- ```bash
		  $> sudo mdadm --create --verbose /dev/md0 --level=10 --layout=o3 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc /dev/sdd
		  
		  #输出
		  mdadm: Defaulting to version 1.2 metadata
		  mdadm: array /dev/md0 started.
		  ```
	- 检查新建raid是否建立成功
		- ```bash
		  $> cat /proc/mdstat
		  
		  #输出
		  Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
		  md0 : active raid10 sdg1[3] sdd1[2] sde1[1] sdc1[0]
		        15627786240 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
		        [>....................]  resync =  0.2% (43876352/15627786240) finish=1262.2min speed=205766K/sec
		        bitmap: 117/117 pages [468KB], 65536KB chunk
		  
		  unused devices: <none>
		  ```
		- collapsed:: true
		  ```bash
		  $> sudo mdadm --examine /dev/sdb /dev/sdc /dev/sdd /dev/sde
		  ```
			- 输出
			- ```bash
			  /dev/sdc:
			     MBR Magic : aa55
			  Partition[0] :   4294967295 sectors at            1 (type ee)
			  /dev/sde:
			     MBR Magic : aa55
			  Partition[0] :   4294967295 sectors at            1 (type ee)
			  /dev/sdd:
			     MBR Magic : aa55
			  Partition[0] :   4294967295 sectors at            1 (type ee)
			  /dev/sdg:
			     MBR Magic : aa55
			  Partition[0] :   4294967295 sectors at            1 (type ee)
			  
			  ```
		- collapsed:: true
		  ```bash
		  $> sudo mdadm --examine /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
		  ```
			- 输出
			- ```bash
			  /dev/sdc1:
			            Magic : a92b4efc
			          Version : 1.2
			      Feature Map : 0x1
			       Array UUID : ee966ee8:11df167b:58bb9346:ca7cac03
			             Name : swat:0  (local to host swat)
			    Creation Time : Sat Oct 21 09:04:47 2023
			       Raid Level : raid10
			     Raid Devices : 4
			  
			   Avail Dev Size : 15627786240 sectors (7.28 TiB 8.00 TB)
			       Array Size : 15627786240 KiB (14.55 TiB 16.00 TB)
			      Data Offset : 264192 sectors
			     Super Offset : 8 sectors
			     Unused Space : before=264104 sectors, after=0 sectors
			            State : active
			      Device UUID : e3b76d08:ab3b046b:9f875778:92fbc471
			  
			  Internal Bitmap : 8 sectors from superblock
			      Update Time : Sat Oct 21 09:11:20 2023
			    Bad Block Log : 512 entries available at offset 72 sectors
			         Checksum : 417c3b33 - correct
			           Events : 75
			  
			           Layout : near=2
			       Chunk Size : 512K
			  
			     Device Role : Active device 0
			     Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
			  /dev/sde1:
			            Magic : a92b4efc
			          Version : 1.2
			      Feature Map : 0x1
			       Array UUID : ee966ee8:11df167b:58bb9346:ca7cac03
			             Name : swat:0  (local to host swat)
			    Creation Time : Sat Oct 21 09:04:47 2023
			       Raid Level : raid10
			     Raid Devices : 4
			  
			   Avail Dev Size : 15627786240 sectors (7.28 TiB 8.00 TB)
			       Array Size : 15627786240 KiB (14.55 TiB 16.00 TB)
			      Data Offset : 264192 sectors
			     Super Offset : 8 sectors
			     Unused Space : before=264104 sectors, after=0 sectors
			            State : active
			      Device UUID : 600225b1:477fd333:9a528db4:7f758868
			  
			  Internal Bitmap : 8 sectors from superblock
			      Update Time : Sat Oct 21 09:11:20 2023
			    Bad Block Log : 512 entries available at offset 72 sectors
			         Checksum : e5fc0e35 - correct
			           Events : 75
			  
			           Layout : near=2
			       Chunk Size : 512K
			  
			     Device Role : Active device 1
			     Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
			  /dev/sdd1:
			            Magic : a92b4efc
			          Version : 1.2
			      Feature Map : 0x1
			       Array UUID : ee966ee8:11df167b:58bb9346:ca7cac03
			             Name : swat:0  (local to host swat)
			    Creation Time : Sat Oct 21 09:04:47 2023
			       Raid Level : raid10
			     Raid Devices : 4
			  
			   Avail Dev Size : 15627786240 sectors (7.28 TiB 8.00 TB)
			       Array Size : 15627786240 KiB (14.55 TiB 16.00 TB)
			      Data Offset : 264192 sectors
			     Super Offset : 8 sectors
			     Unused Space : before=264104 sectors, after=0 sectors
			            State : active
			      Device UUID : 8c11a33f:dabef8ec:dc09932e:753c9cd8
			  
			  Internal Bitmap : 8 sectors from superblock
			      Update Time : Sat Oct 21 09:11:20 2023
			    Bad Block Log : 512 entries available at offset 72 sectors
			         Checksum : 17b8db2e - correct
			           Events : 75
			  
			           Layout : near=2
			       Chunk Size : 512K
			  
			     Device Role : Active device 2
			     Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
			  /dev/sdg1:
			            Magic : a92b4efc
			          Version : 1.2
			      Feature Map : 0x1
			       Array UUID : ee966ee8:11df167b:58bb9346:ca7cac03
			             Name : swat:0  (local to host swat)
			    Creation Time : Sat Oct 21 09:04:47 2023
			       Raid Level : raid10
			     Raid Devices : 4
			  
			   Avail Dev Size : 15627786240 sectors (7.28 TiB 8.00 TB)
			       Array Size : 15627786240 KiB (14.55 TiB 16.00 TB)
			      Data Offset : 264192 sectors
			     Super Offset : 8 sectors
			     Unused Space : before=264104 sectors, after=0 sectors
			            State : active
			      Device UUID : d751a4d0:ebd5489a:389878a3:1325ba25
			  
			  Internal Bitmap : 8 sectors from superblock
			      Update Time : Sat Oct 21 09:11:20 2023
			    Bad Block Log : 512 entries available at offset 72 sectors
			         Checksum : 180da985 - correct
			           Events : 75
			  
			           Layout : near=2
			       Chunk Size : 512K
			  
			     Device Role : Active device 3
			     Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
			  ```
		- collapsed:: true
		  ```bash
		  $> sudo mdadm --detail /dev/md0
		  ```
			- ```bash
			  /dev/md0:
			             Version : 1.2
			       Creation Time : Sat Oct 21 09:04:47 2023
			          Raid Level : raid10
			          Array Size : 15627786240 (14.55 TiB 16.00 TB)
			       Used Dev Size : 7813893120 (7.28 TiB 8.00 TB)
			        Raid Devices : 4
			       Total Devices : 4
			         Persistence : Superblock is persistent
			  
			       Intent Bitmap : Internal
			  
			         Update Time : Sat Oct 21 09:14:48 2023
			               State : clean, resyncing 
			      Active Devices : 4
			     Working Devices : 4
			      Failed Devices : 0
			       Spare Devices : 0
			  
			              Layout : near=2
			          Chunk Size : 512K
			  
			  Consistency Policy : bitmap
			  
			       Resync Status : 0% complete
			  
			                Name : swat:0  (local to host swat)
			                UUID : ee966ee8:11df167b:58bb9346:ca7cac03
			              Events : 114
			  
			      Number   Major   Minor   RaidDevice State
			         0       8       33        0      active sync set-A   /dev/sdc1
			         1       8       65        1      active sync set-B   /dev/sde1
			         2       8       49        2      active sync set-A   /dev/sdd1
			         3       8       97        3      active sync set-B   /dev/sdg1
			  ```
	- 格式化文件系统
		- collapsed:: true
		  ```bash
		  $> sudo mkfs.ext4 /dev/md0
		  ```
			- ```bash
			  mke2fs 1.46.5 (30-Dec-2021)
			  Creating filesystem with 3906946560 4k blocks and 488370176 inodes
			  Filesystem UUID: 6fb3df9f-e7fe-4745-969b-51625c4bf243
			  Superblock backups stored on blocks: 
			          32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
			          4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
			          102400000, 214990848, 512000000, 550731776, 644972544, 1934917632, 
			          2560000000, 3855122432
			  
			  Allocating group tables: done                            
			  Writing inode tables: done                            
			  Creating journal (262144 blocks): done
			  Writing superblocks and filesystem accounting information:              
			  done
			  ```
	- 挂载文件夹[[Linux挂载硬盘]]
		- ```bash
		  $> sudo mount /dev/md0 /Storage
		  ```
	- 修改/etc/fstab开机自动挂载
		- ```bash
		  $> echo '/dev/md0 /mnt/md0 ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab
		  
		  #自动重载
		  $> sudo mount -av
		  ```
	- 保存RAID设置
		- ```bash
		  sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
		  ```
		- ```bash
		  root> cat /etc/mdadm.conf 
		  
		  ARRAY /dev/md0 level=raid10 num-devices=4 metadata=1.2 name=swat:0 UUID=ee966ee8:11df167b:58bb9346:ca7cac03
		     devices=/dev/sdc1,/dev/sdd1,/dev/sde1,/dev/sdg1
		  ```
	- 更新启动引导
		- ```bash
		  $> sudo update-initramfs -u
		  ```
	-