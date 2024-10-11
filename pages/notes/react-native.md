# React-native 学习笔记

## laern mircosoft
>https://learn.microsoft.com/en-us/windows/dev-environment/javascript/react-native-for-windows

## 1. React-native 简介
> https://reactnative.dev/docs/environment-setup
> https://reactnative.dev/docs/set-up-your-environment
> https://reactnative.dev/docs/components-and-apis

## react.org
> https://react.dev/reference/react
> https://zh-hans.react.dev/reference/react

## Android Studio
> https://developer.android.com/studio/run/win-usb


## microsoft 
> https://learn.microsoft.com/en-us/windows/dev-environment/javascript/react-native-for-android

## 打包 [expo](https://expo.dev/)

### 教程 https://docs.expo.dev/tutorial/introduction/
> blog https://www.cnblogs.com/xutongbao/p/18161478
> expo router https://docs.expo.dev/router/introduction/
> expo icon https://icons.expo.fyi/Index

```
eas build --platform android
√ Generated eas.json. Learn more: https://docs.expo.dev/build-reference/eas-json/
EAS project not configured.
√ Would you like to automatically create an EAS project for @zhuxiaoxi1008/my-react-native? ... yes
✔ Created @zhuxiaoxi1008/my-react-native: https://expo.dev/accounts/zhuxiaoxi1008/projects/my-react-native on Expo
✔ Linked local project to EAS project d1116e0e-c2dc-49d8-bb5d-664f8c05d5a1
Loaded "env" configuration for the "production" profile: . Learn more: https://docs.expo.dev/build-reference/variables/

📝  Android application id Learn more: https://expo.fyi/android-package
```

### 打包 apk
打包环境设置
https://docs.expo.dev/build-reference/variables/

```
eas build -p android --profile preview

打包完后 会在这个网站上看到信息
https://expo.dev/accounts/zhuxiaoxi1008/projects/my-react-native/builds/31db688b-c5b2-40a5-a810-a6036810b549
```





React Native 是一个用 JavaScript 编写的框架，使开发者能够为 iOS 和 Android 构建原生应用。React Native 使用 JavaScript 和 React 来构建移动应用，同时使用原生 UI 组件来提供更好的用户体验。

React Native 的主要特点包括：

- 使用 JavaScript 和 React 来构建移动应用
- 使用原生 UI 组件来提供更好的用户体验

## 2. 环境准备

安装 chotolate 

``` powershell 下执行
Set-ExecutionPolicy Bypass -Scope Process -Force

[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

choto -v
```

# 新建项目
npx create-expo-app@latest

## 问题 adb devices not found ？
或者换一个数据线 
https://developer.android.com/studio/run/win-usb 
https://developer.android.com/studio/run/managing-avds?hl=zh-cn

## Here is the list of top free Android emulators for Windows 7, 8.1, 10, 11 PCs and MAC?
Bluestacks
NOX
Andy
droid4x
Windroy
Genymotion
Ko Player
Memu

## react-native npm run start
Welcome!
👋
Step 1: Try it
Edit app/(tabs)/index.tsx to see changes. Press  to open developer tools.
Step 2: Explore
Tap the Explore tab to learn more about what's included in this starter app.
Step 3: Get a fresh start
When you're ready, run npm run reset-project to get a fresh app directory. This will move the current app to app-example.


## react problem
> https://react.dev/warnings/invalid-hook-call-warning

You might be breaking the Rules of Hooks.
你可能违反了“钩子”规则。
You might have mismatching versions of React and React DOM.
你可能安装了不兼容的 React 和 React DOM 版本。
You might have more than one copy of React in the same app.
你可以在同一个应用程序中安装多个 React 版本。

✅ Call them at the top level in the body of a function component.
在函数组件的主体部分，直接调用它们。
✅ Call them at the top level in the body of a custom Hook.
在自定义 Hook 的主体中，直接调用它们。

在其他情况下不支持调用钩子（以 " use " 开头的函数），例如：
🔴 Do not call Hooks inside conditions or loops.
不要在条件或循环中调用 Hooks。
🔴 Do not call Hooks after a conditional return statement.
不要在条件语句 return 之后调用Hooks。
🔴 Do not call Hooks in event handlers.
不要在事件处理程序中调用 Hooks。
🔴 Do not call Hooks in class components.
不要在类组件中调用Hooks。
🔴 Do not call Hooks inside functions passed to useMemo, useReducer, or useEffect.
不要在传递给 ` useMemo `、` useReducer ` 或 ` useEffect ` 的函数内部调用 Hooks。

插件
 "react-native-webview": "^13.8.6"