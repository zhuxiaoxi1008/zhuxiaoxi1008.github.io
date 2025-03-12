前言

### 主题
Monokai Pro
同时提供 配色主题和文件主题,看起来比较舒服.
配色方案有多种,用ctrl+k+t快速选择主题

### 基础插件
HTML CSS Support
提供html和css的代码高亮和提示,必备插件
JavaScript (ES6) code snippets
vscode本身有内置js的代码提示,装一个JavaScript (ES6) code snippets用来提示代码片段就够了.

### Vue插件推荐
Vue - Official
Vue Peek
Vue VSCode Snippets
### React
Simple React Snippets
Typescript React code snippets
ES7+ React/Redux/React-Native snippets
### 小程序
uni-helper
### 代码格式化
Prettier - Code formatter
在 settings.json中也需要配置一下
```
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript|react]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript|react]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[vue]": {
    "editor.defaultFormatter": "Vue.volar"
  },
  "prettier.configPath": ".prettierrc.js",

```
Eslint
### 数据库
SQL Tools
MongoDB for VS Code
Redis
### 其他插件
Better Comments
以不同的颜色高亮注释,如果需要自定义可以在 settings.json中写入配置来进行自定义
```
"better-comments.tags": [
  {
    "tag": "!",
    "color": "#FF2D00",
    "strikethrough": false,
    "underline": false,
    "backgroundColor": "transparent",
    "bold": false,
    "italic": false
  },
  {
    "tag": "?",
    "color": "#3498DB",
    "strikethrough": false,
    "underline": false,
    "backgroundColor": "transparent",
    "bold": false,
    "italic": false
  },
  {
    "tag": "//",
    "color": "#474747",
    "strikethrough": true,
    "underline": false,
    "backgroundColor": "transparent",
    "bold": false,
    "italic": false
  },
  {
    "tag": "todo",
    "color": "#FF8C00",
    "strikethrough": false,
    "underline": false,
    "backgroundColor": "transparent",
    "bold": false,
    "italic": false
  },
  {
    "tag": "*",
    "color": "#98C379",
    "strikethrough": false,
    "underline": false,
    "backgroundColor": "transparent",
    "bold": false,
    "italic": false
  }
]

```
Turbo Console Log

按下快捷键就可以快速的打印出上面的这种 console.log
Console Ninja
Path Intellisense
自动补全路径的插件,在项目结构比较深的时候这个工具就很好用了
git相关
Git Graph:
GitLens — Git supercharged
Project Manager
vite
替代了Live Server在我插件列表中的位置
vscode-mindmap
VSCode Animations
Bookmarks
配置文件
```
{
  "workbench.layoutControl.enabled": false,
  "window.commandCenter": false,
  "window.menuBarVisibility": "compact",
  "security.workspace.trust.untrustedFiles": "open",
  "editor.scrollbar.scrollByPage": true,
  "editor.smoothScrolling": true,
  "explorer.confirmDelete": false,
  "explorer.confirmDragAndDrop": true,
  "git.confirmSync": false,
  "editor.fontVariations": false,
  "workbench.startupEditor": "none",
  "editor.acceptSuggestionOnCommitCharacter": false,
  "editor.fontSize": 16,
  "search.followSymlinks": false,
  "search.useIgnoreFiles": false,
  "typescript.tsserver.maxTsServerMemory": 12288,
  "git.autorefresh": false,
  "editor.fontWeight": "bold",
  "editor.codeLensFontFamily": "'Monaspace Radon'",
  "editor.fontFamily": "'Monaspace Radon'",
  "debug.console.fontFamily": "FiraCode Nerd Font",
  "editor.fontLigatures": true,
  "explorer.compactFolders": false,
  "typescript.format.enable": false,
  "editor.formatOnSave": true,
  "extensions.ignoreRecommendations": true,
  "files.autoSave": "afterDelay",
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  },
  "emmet.triggerExpansionOnTab": true,
  "editor.cursorBlinking": "smooth",
  "editor.cursorStyle": "block",
  "editor.cursorSmoothCaretAnimation": "on",
  "workbench.list.smoothScrolling": true,
  "diffEditor.ignoreTrimWhitespace": false,
  // 保存后自动修复格式
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  // 添加vue支持
  "eslint.validate": ["javascript", "javascriptreact", "vue"],
  "files.eol": "\n",
  "eslint.format.enable": true,
  "editor.linkedEditing": true,
  "typescript.disableAutomaticTypeAcquisition": true,
  "files.associations": {
    "*.json": "jsonc"
  },
  "window.zoomLevel": -1,
  "px-to-rpx.autoRemovePrefixZero": true,
  "px-to-rpx.baseWidth": 375,
  "px-to-rpx.fixedDigits": 2,
  "javascript.updateImportsOnFileMove.enabled": "never",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript|react]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript|react]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[vue]": {
    "editor.defaultFormatter": "Vue.volar"
  },
  "prettier.configPath": ".prettierrc.js",
  "update.mode": "default",
  "workbench.tree.enableStickyScroll": true,
  "turboConsoleLog.logMessagePrefix": "👉",
  "terminal.integrated.smoothScrolling": true,
  "[javascriptreact]": {
    "editor.defaultFormatter": "vscode.typescript-language-features"
  },
  "editor.inlayHints.fontFamily": "'Monaspace Radon'",
  "animations.Install-Method": "Apc Customize UI++",
  "vite.autoStart": false,
  "apc.imports": [
    "file:///c:/Users/cathe/.vscode/extensions/brandonkirbyson.vscode-animations-2.0.1/dist/updateHandler.js"
  ],
  "animations.Enabled": true,
  "workbench.iconTheme": "Monokai Pro (Filter Machine) Icons",
  "workbench.colorTheme": "Monokai Pro (Filter Machine)",
  "terminal.integrated.env.windows": {},
  "console-ninja.featureSet": "Community"
}
```