- #WSL2
- ```powershell
  # 端口转发
  netsh interface portproxy add v4tov4 listenaddress=0.0.0.0 listenport=[exposed windows port] connectaddress=[wsl ip] connectport=[wsl port]
  
  # 防火墙规则
  netsh advfirewall firewall add rule name=WSL2 dir=in action=allow protocol=TCP localport=[exposed windows port]
  ```