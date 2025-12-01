### 学习随笔

对象
ResizeObserver
```
const observer = new ResizeObserver(entries => {
  // `entries` 是一个 ResizeObserverEntry 对象的数组
  for (let entry of entries) {
    // 监听到的元素
    const targetEl = entry.target;
    
    // 获取新的尺寸信息（例如内容盒的宽度和高度）
    const newWidth = entry.contentRect.width;
    const newHeight = entry.contentRect.height;
    
    console.log(`元素 ${targetEl.id} 的尺寸发生了变化: ${newWidth}x${newHeight}`);
    
    // 可以在这里执行你需要的 DOM 操作或状态更新
  }
});


const myElement = document.getElementById('my-resizable-el');
// 开始监听该元素的尺寸变化
observer.observe(myElement);
// 停止监听
observer.unobserve(myElement);
// 停止所有监听
observer.disconnect();

```
