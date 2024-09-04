
<!-- docsify-ignore -->
学习笔记

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