- #Linux
- Screen is a background task host
- 后台启动一个新的screen进程（静默启动）
	- ```bash
	  screen -dmS <session-id> <command>
	  ```
- 恢复中断的screen进程（仍处于attach状态）
	- ```bash
	  screen -D -r ＜session-id>
	  ```
- 强制停止