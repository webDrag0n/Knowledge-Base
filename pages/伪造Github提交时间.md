- #Git #Github #fake #commit #time
- 设置环境变量（Linux环境下测试，Windows环境尚未确定成功）
  ```bash
  export GIT_AUTHOR_DATE="2022-10-08 20:00:00+08:00"
  export GIT_COMMITTER_DATE="2022-10-08 20:00:00+08:00"
  ```
  两个时间保持一样
- 正常执行
  ```bash
  git init
  git commit -m "message"
  git 
  ```