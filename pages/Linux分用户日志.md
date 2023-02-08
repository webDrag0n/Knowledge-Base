- 参考 [Linux下记录所有用户的登录和操作日志](https://blog.51cto.com/xuaijun/2821502)
- 在 [/etc/bash/bashrc](((62eb946d-a94f-4486-880a-06594b75aec2))) 中加入
- ```bash
  history
  USER=`whoami`
  USER_IP=`who -u am i 2>/dev/null| awk '{print $NF}'|sed -e 's/[()]//g'`
  if [ "$USER_IP" = "" ]; then
  USER_IP=`hostname`
  fi
  if [ ! -d /var/log/history ]; then
  mkdir /var/log/history
  chmod 777 /var/log/history
  fi
  if [ ! -d /var/log/history/${LOGNAME} ]; then
  mkdir /var/log/history/${LOGNAME}
  chmod 300 /var/log/history/${LOGNAME}
  fi
  export HISTSIZE=4096
  DT=`date +"%Y%m%d_%H:%M:%S"`
  export HISTFILE="/var/log/history/${LOGNAME}/${USER}@${USER_IP}_$DT"
  chmod 600 /var/log/history/${LOGNAME}/*history* 2>/dev/null
  ```
- 保存的文件名格式为：`${USER}@${USER_IP}_$DateTime`
-
- 为每个用户建立``/var/log/history/{Username}``目录，并按需设置每个文件夹的访问权限，建议设置如下：
- ```bash
  /var/log/history            root     root   drwxrwxrwx
  /var/log/history/{Username} Username nosudo d-wx------
  ```
- 注意此处的nosudo为用户所在组，此处取nosudo是将该组下用户全部移除了sudo权限