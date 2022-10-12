- #Windows
- 在[[Windows 11]]家庭版上安装
	- 将以下脚本保存为bat文件并用管理员权限执行
	- ```
	  pushd "%~dp0"
	  
	  dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
	  
	  for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
	  
	  del hyper-v.txt
	  
	  Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL
	  
	  pause
	  ```