- #GitLab
- ### 主体备份
	- v12.2 or later:
	  ```bash
	  sudo gitlab-backup create
	  ```
	  v12.1 or earlier:
	  ```bash
	  gitlab-rake gitlab:backup:create
	  ```
	- Docker:
	  ```bash
	  docker exec -t <container name> [Command above]
	  ```
- ### 敏感文件手动备份（必要！）
	-