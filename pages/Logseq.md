- ### Github开发页面
	- https://github.com/logseq/logseq
	-
- ### Markdown 文档
  id:: 6249ba5b-b3e7-4878-8cb1-7d7dc1209932
	- ==https://www.markdownguide.org/tools/logseq/==
- ### 制作Notion风格的链接卡片
	- <div contenteditable="false" data-content-editable-void="true"><div style="display: flex; color: rgb(255, 255, 255)"><a rel="noopener noreferrer" style="display: block; color: inherit; text-decoration: none; flex-grow: 1; min-width: 0px;" href="https://stackoverflow.com/questions/22575662/filename-too-long-in-git-for-windows"><div class="notion-focusable" role="button" tabindex="0" style="user-select: none; transition: background 20ms ease-in 0s; cursor: pointer; width: 100%; display: flex; flex-wrap: wrap-reverse; align-items: stretch; text-align: left; overflow: hidden; border: 1px solid rgba(255, 255, 255, 0.16); border-radius: 3px; position: relative; color: inherit; fill: inherit;"><div style="flex: 4 1 180px; padding: 12px 14px 14px; overflow: hidden; text-align: left;"><div style="font-size: 14px; line-height: 20px; color: rgb(255, 255, 255); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; min-height: 24px; margin-bottom: 2px;">Filename too long in Git for Windows</div><div style="font-size: 12px; line-height: 16px; color: rgba(255, 255, 255, 0.65); height: 32px; overflow: hidden;">
	  
	  Asked I'm using Git-1.9.0-preview20140217 for Windows. As I know, this release should fix the issue with too long filenames. But not for me. Surely I'm doing something wrong: I did git config core.longpaths true and git add . and then git commit. Everything went well.
	  
	  </div><div style="display: flex; margin-top: 6px;"><img src="https://cdn.sstatic.net/Sites/stackoverflow/Img/apple-touch-icon@2.png?v=73d79a89bded" style="width: 16px; height: 16px; min-width: 16px; margin-right: 6px;"><div style="font-size: 12px; line-height: 16px; color: rgb(255, 255, 255); white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">https://stackoverflow.com/questions/22575662/filename-too-long-in-git-for-windows</div></div></div><div style="flex: 1 1 180px; display: block; position: relative;"><div style="position: absolute; inset: 0px;"><div style="width: 100%; height: 100%;"><img src="https://cdn.sstatic.net/Sites/stackoverflow/Img/apple-touch-icon@2.png?v=73d79a89bded" style="display: block; object-fit: cover; border-radius: 1px; width: 100%; height: 100%;"></div></div></div></div></a></div></div>
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
  ~~`shift + enter`，直接enter会添加新的块（block）~~(默认)
  该设置现在通过编辑config.edn，在`:shortcut`处改为
  ```lua
  :shortcuts
  {
  	:editor/new-block "shift+enter"
  	:editor/new-line "enter"
  }
  ```
  实现了对调
- ### 导出Github Pages后的网页链接
  直接写``[webdrag0n.github.io](webdrag0n.github.io)``会创建一个以该网址为名的页面，应该直接粘贴带https://协议标识的网页链接，如 https://webdrag0n.github.io/
-
- ### 编辑器样式
	- 编辑器内皮肤可通过更改`C:\Users\webDrag0n\Documents\WORKSPACE_LOGSEQ\logseq\custom.css`来更改
	- 或在插件市场安装插件【推荐】
-
- ### 导出样式
	- 导出样式为`C:\Users\webDrag0n\Documents\WORKSPACE_LOGSEQ\logseq\export.css`，复制custom.css内容至export.css可统一编辑器与导出样式