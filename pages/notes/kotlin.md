## Demo
Now in Android (Google 官方最佳参考)
https://github.com/android/nowinandroid
Compose Samples (Google 官方多个小 Demo 集合)
https://github.com/android/compose-samples
Awesome Jetpack Compose Android Apps (精选高质量 Compose App 合集)
https://github.com/androiddevnotes/awesome-jetpack-compose-android-apps
NotyKT (笔记类完整 App)
https://github.com/PatilShreyas/NotyKT
Ivy Wallet (记账类、多模块、Clean Arch)
https://github.com/Ivy-Apps/ivy-wallet
BaseApp Jetpack Compose (Clean Architecture 模板)
https://github.com/merttoptas/BaseApp-Jetpack-Compose-Android-Kotlin
Eyepetizer (开眼视频高仿、UI 精致)
https://github.com/VIPyinzhiwei/Eyepetizer

## 笔记
1.变量声明，不需要指定类型或放在声明变量后 var 和 val
2.静态类型语言可以进行类型推导
3.函数声明 fun 必须指定返回值类型，不指定返回值类型默认返回 Unit

什么时候写函数类型总结：
如果它是⼀个函数的参数？必须使⽤。
·如果它是⼀个⾮表达式定义的函数？除了返回Unit，其他情况必须使⽤。
·如果它是⼀个递归的函数？必须使⽤。
·如果它是⼀个公有⽅法的返回值？
为了更好的代码可读性及输出类型的可控性，建议使⽤。
除上述情况之外，你可以尽量尝试不显式声明类型，直到你遇到下⼀个特殊情况。

通过两个冒号来实现对于某个类的⽅法进⾏引⽤

4.lambda 表达式
    lambda 表达式是函数类型的一种特殊形式，它允许我们定义函数作为参数或返回值。
    Lambda 表达式必须通过{}来包裹
    基本结构：Lambda 表达式必须通过 {} 来包裹
    完整语法：{ 参数1: 类型, 参数2: 类型 -> 函数体 }
    示例：val sum = { a: Int, b: Int -> a + b }
关键特性
    隐式参数 it：

    当 Lambda 只有一个参数时，可以省略参数声明
    使用 it 代替显式参数名
    例如：list.filter { it > 0 } 代替 list.filter { value -> value > 0 }
    单表达式简写：

    当 Lambda 只包含一个表达式时，可以省略 -> 和 {}（仅适用于函数最后一个参数是 Lambda 的情况）
    例如：list.forEach { println(it) }
    尾随 Lambda 语法：

    如果函数的最后一个参数是 Lambda，可以将 Lambda 放在括号外
    例如：request { /* 网络请求配置 */ } 代替 request({ /* 网络请求配置 */ })
