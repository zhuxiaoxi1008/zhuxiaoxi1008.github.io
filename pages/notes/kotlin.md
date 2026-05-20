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
    基本结构：Lambda 表达式必须通过 {} 来包裹
    完整语法：{ 参数1: 类型, 参数2: 类型 -> 函数体 }
    示例：val sum = { a: Int, b: Int -> a + b }
    如果Lambda声明了参数部分的类型，且返回值类型⽀持类型推导，那么Lambda变量就可以省
略函数类型声明

步骤,写法,简化点,推荐场景
    1,{ it: Int -> println(it) },最完整，显式一切,教学、新手理解、复杂 lambda
    2,{ it -> println(it) },省略参数类型,中间过渡
    3,{ println(it) },使用默认 it,日常最常用
    4,val p = { println(it) },省略函数类型声明,类型推断足够清晰时
    5,val p = ::println,方法引用，极简,完全匹配已有函数时首选


1.单个参数的隐式名称  的使用条件：
   - it 只能在有明确上下文的情况下使用
   - 必须能够从上下文中推断出参数类型
    
