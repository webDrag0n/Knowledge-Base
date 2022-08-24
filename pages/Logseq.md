- ### Github开发页面
	- https://github.com/logseq/logseq
	-
- ### Markdown 文档
  id:: 6249ba5b-b3e7-4878-8cb1-7d7dc1209932
	- ==https://www.markdownguide.org/tools/logseq/==
	-
- ### 中文社区
	- ==https://cn.logseq.com/==
	-
- ### 入门
  id:: 6249ba8f-d84b-4164-8a3d-9949f2fb3758
	- [Official Tutorial](https://docs.logseq.com/#/page/tutorial)
	- [markdown-cheat-sheet](markdown-cheat-sheet)
	- https://zhuanlan.zhihu.com/p/441457813
	- https://pwa.sspai.com/post/69503
	- [markdown-cheat-sheet](https://cn.logseq.com/t/topic/91)
	-
	- https://zhuanlan.zhihu.com/p/450086994
	- https://pengx17.github.io/knowledge-garden/
	-
- ### 块内换行
  `shift + enter`，直接enter会添加新的块（block）(默认)
  该设置现在通过编辑config.edn，在`:shortcut`处加入
  ```lua
  :shortcuts
  {
  :editor/new-block "shift+enter"
  :editor/new-line "enter"
  }
  ```
- ### 导出Github Pages后的网页链接
  直接写``[webdrag0n.github.io](webdrag0n.github.io)``会创建一个以该网址为名的页面，应该直接粘贴带https://协议标识的网页链接，如 https://webdrag0n.github.io/
-
- ### 编辑器样式
	- 编辑器内皮肤可通过更改`C:\Users\webDrag0n\Documents\WORKSPACE_LOGSEQ\logseq\custom.css`来更改
	- 或在插件市场安装插件【推荐】
-
- ### 导出样式
	- 导出样式为`C:\Users\webDrag0n\Documents\WORKSPACE_LOGSEQ\logseq\export.css`，复制custom.css内容至export.css可统一编辑器与导出样式