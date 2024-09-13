- #ssh
- ```bash
  sudo vim /etc/ssh/sshd_config
  --------------------------------
  RSAAuthentication yes
  PubkeyAuthentication yes
  ```
- ```bash
  vim ~/.ssh/authorized_keys
  ------------------------------
  <粘贴公钥>
  ```