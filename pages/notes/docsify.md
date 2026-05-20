
<!-- docsify-ignore -->
学习笔记

# docsify
[docsify](https://docsify.js.org/#/zh-cn/quickstart)

# docsify 安装
```
// 安装
npm i docsify-cli -g

// 初始化
docsify init ./docs
```

# docsify 快速开始

```
1. docsify init ./docs

2. docsify serve docs

<!-- {docsify-ignore} -->
<!-- {docsify-ignore-all} -->

```

你可以使用 ` alias ` 来避免不必要的回退。

```
<script>
  window.$docsify = {
    loadSidebar: true,
    alias: {
      '/.*/_sidebar.md': '/_sidebar.md'
    }
  }
</script>
```

> # 侧边栏展开折叠插件

```
<script src="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>
<script>
  window.$docsify = {
    loadSidebar: true, // 加载侧边栏
    subMaxLevel: 2, // 根据标题折叠内容
    sidebarDisplayLevel: 1, // 设置默认折叠的层级 
  };
</script>
```

 



  
  
  



# docsify 插件
[docsify-pagination](https://github.com/elviswolcott/docsify-pagination)  
[docsify-tabs](https://github.com/lyswhut/docsify-tabs)
[docsify-copy-code](https://github.com/jperasmus/docsify-copy-code)
[docsify-zoom](https://github.com/lyswhut/docsify-zoom)
[docsify-katex](https://github.com/Quramy/docsify-katex)
[docsify-tabs](https://github.com/lyswhut/docsify-tabs)
[docsify-pagination](https://github.com/elviswolcott/docsify-pagination)
展开折叠插件
[docsify-expand-all](https://github.com/lyswhut/docsify-expand-all)
docsify-sidebar-collapse
[docsify-sidebar-collapse](https://github.com/lyswhut/docsify-sidebar-collapse)
docsify-pagination
[docsify-pagination](https://github.com/elviswolcott/docsify-pagination)
docsify-tabs
[docsify-tabs](https://github.com/lyswhut/docsify-tabs)


