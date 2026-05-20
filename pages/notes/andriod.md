## UI uni-app 开发

## 原生 kolit + Jetpack Compose
https://kotlinlang.org/docs/basic-syntax.html#program-entry-point
https://developer.android.com/compose


## 🚀 Kotlin + Jetpack Compose 详细学习计划

您选择 **Kotlin + Jetpack Compose** 作为学习方向非常明智，这是 Google 官方推荐的 Android 现代开发技术栈。这份计划为期 **8 周**，假设您每周投入约 **10-15 小时**进行学习和实践。

---

### 第一阶段：Kotlin 语言基础 (Week 1 - 2)

这是构建 Compose 大厦的基石。您必须先掌握 Kotlin 语言特性。

| 周次 | 知识点 | 重点概念 (必掌握) | 推荐官方资料 (中文) | 预计用时 |
| :--- | :--- | :--- | :--- | :--- |
| **Week 1** | **Kotlin 基础语法** | 变量 (val/var), 数据类型, **Null Safety (空安全)**, 控制流 (When, If), 函数定义。 | [**Kotlin 官方文档**](https://kotlinlang.cn/) - **"基础"** 和 **"类和对象"** 部分。 | 10-12 小时 |
| **Week 2** | **面向对象与高级特性** | **类 (Classes), 继承, 接口, 数据类 (Data Class)**, 扩展函数 (Extension Functions), 集合操作 (List/Map/Filter/Map)。 | [**Kotlin 官方文档**](https://kotlinlang.cn/) - **"函数和泛型"** 和 **"协程指南"** (只需了解概念)。 | 10-12 小时 |

> **学习目标：** 能够熟练使用 Kotlin 编写简单的函数和类，并能理解 Kotlin 的空安全机制。

---

### 第二阶段：Compose 基础与状态管理 (Week 3 - 4)

从传统 XML 切换到声明式 UI (Compose)，理解其核心思想。

| 周次 | 知识点 | 重点概念 (必掌握) | 推荐官方资料 (中文) | 预计用时 |
| :--- | :--- | :--- | :--- | :--- |
| **Week 3** | **Compose 入门与原理** | **Composable 函数 (可组合函数)**, Modifiers (修饰符), Previews (预览), **Recomposition (重组) 原理**。 | [**Android 开发者 - Compose 基础**](https://developer.android.google.cn/jetpack/compose/documentation?hl=zh-cn) | 10-15 小时 |
| **Week 4** | **状态管理与列表** | **State (状态)**, `remember` & `mutableStateOf`, **State Hoisting (状态提升)**, **列表 (`LazyColumn`/`LazyRow`)**。 | [**官方 Codelab: Jetpack Compose 状态**](https://developer.android.google.cn/codelabs/jetpack-compose-state?hl=zh-cn) | 10-15 小时 |

> **学习目标：** 能够使用 Composable 构建简单界面，理解状态是驱动 UI 变化的唯一方式，并能创建可滚动列表。

---

### 第三阶段：架构、数据与并发 (Week 5 - 6)

将 UI 与数据分离，引入 MVVM 架构和异步操作。

| 周次 | 知识点 | 重点概念 (必掌握) | 推荐官方资料 (中文) | 预计用时 |
| :--- | :--- | :--- | :--- | :--- |
| **Week 5** | **Jetpack 架构组件** | **ViewModel** (`ViewModel` 和 `ViewModelProvider`), **Lifecycle** (生命周期), DataStore (数据存储基础)。 | [**Android 开发者 - 架构指南**](https://developer.android.google.cn/topic/libraries/architecture?hl=zh-cn) | 10-15 小时 |
| **Week 6** | **数据流与并发** | **Kotlin Coroutines (协程)** 基础, **Side Effects (副作用)** (`LaunchedEffect`, `rememberCoroutineScope`), 接入 **Retrofit** 进行网络请求。 | [**官方 Codelab: Kotlin Coroutines**](https://developer.android.google.cn/codelabs/kotlin-coroutines?hl=zh-cn) | 12-15 小时 |

> **学习目标：** 能够使用 ViewModel 存储和管理 UI 数据，理解协程在 Android 异步操作中的重要性，并完成一次实际的网络请求。

---

### 第四阶段：进阶与实战 (Week 7 - 8)

| 周次 | 知识点 | 重点概念 (必掌握) | 推荐官方资料 (中文) | 预计用时 |
| :--- | :--- | :--- | :--- | :--- |
| **Week 7** | **导航与动画** | **Compose Navigation (NavController)**, 嵌套导航图, **基本动画** (`AnimatedVisibility`, `animate*AsState`), 主题化 (`MaterialTheme`)。 | [**Compose Navigation 文档**](https://developer.android.google.cn/jetpack/compose/navigation?hl=zh-cn) | 15-20 小时 |
| **Week 8** | **实战项目与测试** | **动手完成一个完整的小项目** (如待办事项App, 天气App), 单元测试 (Unit Test) 基础, **Hilt/Koin** 依赖注入基础。 | 实践为主，结合 **Google Developers YouTube 频道 (有中文字幕)** 和官方示例代码。 | 15-20 小时 |

---

## 进阶方向 (完成基础学习后)

完成以上基础计划后，您可以根据兴趣和职业发展，选择以下方向深入学习：

### 1. 架构深度与优化

| 方向 | 知识点 | 目标 |
| :--- | :--- | :--- |
| **Clean 架构** | MVVM-C (Coordinator), MVI (Model-View-Intent) 模式，多模块化 (Multi-Module) 项目结构。 | 适用于大型、复杂的企业级应用开发。 |
| **性能优化** | **Baseline Profiles** (基线配置文件) 优化启动速度，Profiling (性能分析) 工具的使用。 | 确保应用在低端设备上也能流畅运行。 |
| **依赖注入** | 深入学习 **Hilt** 或 **Koin**，掌握依赖注入在测试和架构中的重要性。 | 提高代码的解耦性和可测试性。 |

### 2. Compose 高级特性

| 方向 | 知识点 | 目标 |
| :--- | :--- | :--- |
| **高级动画** | Custom Layout (自定义布局), `Layout` Composable, MotionLayout 在 Compose 中的应用，手势处理。 | 实现复杂的、非标准的原生级交互和动画效果。 |
| **互操作性** | 在 Compose 中使用 View (如 WebView), 在 View 中使用 Compose (`ComposeView`)。 | 将 Compose 逐步引入到现有的 XML 项目中。 |

### 3. 跨平台探索

| 方向 | 知识点 | 目标 |
| :--- | :--- | :--- |
| **Kotlin Multiplatform (KMP)** | 学习 KMP 的架构，实现逻辑层 (Data, ViewModel) 的跨平台共享。 | 将核心业务逻辑同时部署到 iOS、Web 和桌面端。 |

---

## 学习资料与资源推荐 (以中文为主)

1.  **💻 Android 开发者官网 (中文版):**
    * 这是您的**主要学习阵地**。所有最新的 API、指南和最佳实践都在这里。
    * **链接：** `developer.android.google.cn/` (请确保使用 `.cn` 域名访问中文资源)。
    * **重点关注：** **“Jetpack Compose”** 和 **“Android 基础知识”** 两个板块。

2.  **🧪 Google Codelabs (中文版):**
    * Codelabs 是带有详细步骤的实践练习，非常适合上手。
    * **搜索关键词：** “Jetpack Compose Codelabs”。

3.  **📺 Google Developers YouTube 频道:**
    * 提供了大量的 **Compose 视频教程**和技术会议录像，很多都配有高质量的**中文字幕**。

4.  **📚 Kotlin 官方文档 (中文版):**
    * 学习 Kotlin 语言最权威的资源。
    * **链接：** `kotlinlang.cn/`