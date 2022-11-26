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
  git add "blah"
  git commit -m "message"
  ```
- ### 踩坑
	- 直接使用
	  ```bash
	  git commit --amend --no-edit --date="Thu Nov 10 01:28:33 2022 +0800"
	  ```
	  会导致Git本地提交记录显示时间已是伪造时间，但是提交至GitHub后发现并未生效，原因在于commit中的`--date`参数只改变了GIT_AUTHOR_DATE，而GitHub依赖GIT_COMMITTER_DATE