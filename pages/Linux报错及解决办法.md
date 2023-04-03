- #Linux #报错
- [W: Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast](https://serverfault.com/questions/755194/ubuntu-15-10-server-w-possible-missing-firmware-lib-firmware-ast-dp501-fw-bin)
	- It is a harmless bug for now
	- ```bash
	  sudo touch /lib/firmware/ast_dp501_fw.bin
	  ```
- [This account is currently not available](https://www.cnblogs.com/Autism-jay/p/9228875.html)
  id:: 63e36e6f-814d-4487-9756-875fa1269401
	- 解决办法：
	- 比如我是 su kafka的时候出现的问题
	- 用vi看看 kafka的帐号信息
	- ```bash
	  cat /etc/passwd | grep kafka
	  ```
	- 发现它的shell是“/sbin /nologin”，需要将起改成“/bin/bash”