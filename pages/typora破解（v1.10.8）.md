title:: typora破解（v1.10.8）

- 修改：`/Applications/Typora.app/Contents/Resources/TypeMark/page-dist/static/js/LicenseIndex.180dd4c7.5b0f7af9.chunk.js`
  `hasActivated="true"==e.hasActivated`为`hasActivated="true"=="true"`
- 关闭启动弹窗，修改：`0.99879679.chunk.js`在文件开头添加`setTimeout(**function**() { document.querySelector('.default-btn.secondary-btn').click(); }, 256);`
- 隐藏“未激活”按钮，修改：`/Applications/Typora.app/Contents/Resources/TypeMark/index.html`在开头的<!doctype html><html lang="en"><head>后添加代码`<style>body>div[role="button"]{visibility:hidden;}</style>`