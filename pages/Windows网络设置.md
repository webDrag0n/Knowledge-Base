- #Windows11
- 重设proxy
  ```bash
  netsh winhttp reset proxy
  ```
- 重设wsl网络（执行以上命令后wsl网络可能出现故障）
  ```bash
  net stop hns
  net start hns
  ```
  ```bash
  netsh winsock reset
  netsh int ip reset
  ```