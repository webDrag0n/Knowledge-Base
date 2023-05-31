- #Git #Github #fake #commit #time
- id:: 63e36e71-8fb1-4987-a839-ad2a815f4a20
  ```bash
  export GIT_AUTHOR_DATE="2022-10-08 20:00:00+08:00"
  export GIT_COMMITTER_DATE="2022-10-08 20:00:00+08:00"
  ```
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
	  会导致Git本地提交记录显示时间已是伪造时间，但是提交至GitHub后发现并未生效，原因在于commit中的`--date`参数只改变了GIT_AUTHOR_DATE，而GitHub依赖GIT_COMMITTER_DATE决定显示时间
- ### 多人同时
	- 如需多人在同一电脑上进行该操作，只需要在每次执行((63e36e71-8fb1-4987-a839-ad2a815f4a20))前执行按该指引操作切换用户即可 [[Git设置用户名和电子邮箱]]