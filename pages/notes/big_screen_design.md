# 🖥️ Vue 3 大屏等比例缩放适配笔记
vue3-big-screen
github: [https://github.com/dddggg123/vue3-big-screen?tab=readme-ov-file](https://github.com/dddggg123/vue3-big-screen?tab=readme-ov-file)

其他demo 
[big-data-view](https://gitee.com/iGaoWei/big-data-view)

## VUE2 集成
[DataV](http://datav.jiaminghi.com/guide/#%E5%AE%89%E8%A3%85)
[vue-chartjs](https://vue-chartjs.org/guide/)
[vue-echarts option-> code 生成器](https://vue-echarts.dev/)
vue2 文档[vue-echarts](https://vue-echarts.github.io/)

---

## VUE3集成
[vue-echarts](https://github.com/ecomfe/vue-echarts/blob/main/README.zh-Hans.md)
```
npm install echarts vue-echarts

<VChart class="chart" :option="option" />
```

[DATAV vue3](@kjgl77/datav-vue3)
[DATAV VUE3 demo](https://datav-vue3.netlify.app/)
```
npm install @kjgl77/datav-vue3

import DataVVue3 from '@kjgl77/datav-vue3'
app.use(DataVVue3)
```

[tailwindcss 4](https://tailwindcss.com/docs/installation)
```
npm install tailwindcss @tailwindcss/vite


import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'
export default defineConfig({
  plugins: [
    tailwindcss(),
  ],
})

@import "tailwindcss";
```

[sass](https://sass-lang.com/guide/#variables)
```
npm install sass -D


css: {
    preprocessorOptions: {
      scss: {
		// 全局导入
        additionalData: `@import "@/styles/variables.scss";`,
        silenceDeprecations: ['import']
      }
    },
  },
```

### 迁徙图
[迁徙图](https://www.makeapie.cn/echarts_content/xYS-YtzOaf.html)




## 🚀 核心思路

这段代码采用 **`transform: scale()`** 对大屏容器进行整体缩放，以实现**等比例（等比缩放，保持内容不被拉伸）适配不同尺寸的浏览器窗口。目标是确保大屏内容始终在视口中完整显示**，同时通过在宽边留出黑边来保持设计比例。

## ⚙️ 关键变量与设计尺寸

| 变量/常量 | 作用描述 | 默认值 |
| :--- | :--- | :--- |
| `baseWidth` | 设计稿宽度 | `1920` |
| `baseHeight` | 设计稿高度 | `1080` |
| `baseProportion` | 设计稿宽高比 $(\frac{1920}{1080})$ | $\approx 1.77778$ |
| `screenRef` | 绑定大屏根元素的引用 | - |
| `scale` | 存储计算出的 X, Y 轴缩放值 | `{ width: "1", height: "1" }` |

## 🧠 `calcRate` 函数适配逻辑

该函数的核心在于比较**当前窗口的宽高比** (`currentRate`) 与**设计稿的宽高比** (`baseProportion`)，并根据比较结果来确定缩放的基准。

$$
\text{currentRate} = \frac{\text{window.innerWidth}}{\text{window.innerHeight}}
$$

### 1\. 场景一：窗口更宽/更扁 (`currentRate > baseProportion`)

**判定:** 窗口的宽度裕度大于高度裕度，**高度**成为视口的瓶颈。

| 目标 | 内容必须铺满**高度** |
| :--- | :--- |
| **基准** | 以**高度**为基准进行缩放。 |
| **逻辑** | 确保 Y 轴缩放比等于 X 轴缩放比 $(S_y = S_x)$，且 $S_y$ 必须等于 $\frac{\text{window.innerHeight}}{\text{baseHeight}}$。 |
| **计算** | $S_y = S_x = \frac{\text{window.innerHeight}}{\text{baseHeight}}$ |
| **效果** | 内容铺满高度，两侧留黑边。 |

### 2\. 场景二：窗口更高/更窄 (`currentRate <= baseProportion`)

**判定:** 窗口的高度裕度大于宽度裕度，**宽度**成为视口的瓶颈。

| 目标 | 内容必须铺满**宽度** |
| :--- | :--- |
| **基准** | 以**宽度**为基准进行缩放。 |
| **逻辑** | 确保 X 轴缩放比等于 Y 轴缩放比 $(S_x = S_y)$，且 $S_x$ 必须等于 $\frac{\text{window.innerWidth}}{\text{baseWidth}}$。 |
| **计算** | $S_x = S_y = \frac{\text{window.innerWidth}}{\text{baseWidth}}$ |
| **效果** | 内容铺满宽度，上下留黑边。 |

## ✨ 缩放应用

最终计算出的缩放值 $S_x$ 和 $S_y$ 会被应用到大屏容器的 `transform` 样式上：

```javascript
screenRef.value.style.transform = `scale(${scale.width}, ${scale.height})`;
```

**⚠️ 提示：** 为了实现完美的居中效果，大屏容器 (`screenRef.value`) 的 CSS 样式通常还需要配合以下属性：

```css
{
    position: absolute;
    left: 50%;
    top: 50%;
    /* 配合 transform: scale() 实现居中 */
    transform-origin: 0 0; 
    /* 缩放后通过 translate 将元素中心移到视口中心 */
    transform: translate(-50%, -50%) scale(Sx, Sy); 
}
```


完整的代码如下：
```javascript
import { ref } from "vue";

export default function windowResize() {
	// * 指向最外层容器
	const screenRef = ref();
	// * 定时函数
	const timer = ref(0);
	// * 默认缩放值
	const scale = {
		width: "1",
		height: "1",
	};
	// * 设计稿尺寸（px）
	const baseWidth = 1920;
	const baseHeight = 1080;

	// * 需保持的比例（默认1.77778）
	const baseProportion = parseFloat((baseWidth / baseHeight).toFixed(5));
	const calcRate = () => {
		// 当前宽高比
		const currentRate = parseFloat(
			(window.innerWidth / window.innerHeight).toFixed(5)
		);
		if (screenRef.value) {
			if (currentRate > baseProportion) {
				// 表示更宽
				scale.width = ( (window.innerHeight * baseProportion) / baseWidth ).toFixed(5);
				scale.height = (window.innerHeight / baseHeight).toFixed(5);
				screenRef.value.style.transform = `scale(${scale.width}, ${scale.height})`;
			} else {
				// 表示更高
				scale.height = ( window.innerWidth / baseProportion / baseHeight ).toFixed(5);
				scale.width = (window.innerWidth / baseWidth).toFixed(5);
				screenRef.value.style.transform = `scale(${scale.width}, ${scale.height})`;
			}
		}
	};

	const resize = () => {
		clearTimeout(timer.value);
		timer.value = window.setTimeout(() => {
			calcRate();
		}, 200);
	};

	// 改变窗口大小重新绘制
	const windowDraw = () => {
		window.addEventListener("resize", resize);
	};

	// 改变窗口大小重新绘制
	const unWindowDraw = () => {
		window.removeEventListener("resize", resize);
	};

	return {
		screenRef,
		calcRate,
		windowDraw,
		unWindowDraw,
	};
}