- Git是一种 [[版本控制]]工具
- ## 相关错误与修复方法
	- ## Git Filename too long
		- 克隆时遇到过长文件名时在bash中执行下列命令
		- 该命令只对bash中的git生效，对图形界面客户端如github desktop无效
		- ```bash
		  git config --system core.longpaths true
		  ```
	- ## Git Submodule
		- ### 添加子模块
		  
		  添加一个远程仓库项目 `https://github.com/iphysresearch/GWToolkit.git` 子模块到一个已有主仓库项目中。代码形式是 `git submodule add <url> <repo_name>`， 如下面的例子：
		  
		  ```
		  $ git submodule add https://github.com/iphysresearch/GWToolkit.git GWToolkit
		  ```
		  
		  这时，你会看到一个名为 `GWToolkit` 的文件夹在你的主仓库目录中。
		  
		  > 如果你是旧版 Git 的话，你会发现 `./GWToolkit` 目录中是空的，你还需要在执行一步「更新子模块」，才可以把远程仓库项目中的内容下载下来。
		  
		  ```
		  $ git submodule update --init --recursive
		  ```
		  
		  > 如果你不小心把路径写错了，可以用下面的代码来删掉，详细可查阅 `git help submodule`。
		  
		  ```
		  $ git rm --cached GWToolkit
		  ```
		  
		  添加子模块后，若运行 `git status`，可以看到主仓库目录中会增加一个文件 `.gitmodules`，这个文件用来保存子模块的信息。
		  
		  ```
		  $ git status
		  位于分支 main
		  您的分支与上游分支 'origin/main' 一致。
		  
		  要提交的变更：
		  （使用 "git restore --staged <文件>..." 以取消暂存）
		  新文件：   .gitmodules
		  新文件：   GWToolkit
		  ```
		  
		  另外，在 `.git/config` 中会多出一块关于子模块信息的内容：
		  
		  ```
		  **[**submodule "GWToolkit"**]**
		        url **=** https://github.com/iphysresearch/GWToolkit.git
		        active **=** true
		  ```
		  
		  该配置文件保存了项目 URL 与已经拉取的本地目录之间的映射。如果有多个子模块，该文件中就会有多条记录。 要重点注意的是，该文件也像 `.gitignore` 文件一样受到（通过）版本控制。 它会和该项目的其他部分一同被拉取推送。 这就是克隆该项目的人知道去哪获得子模块的原因。