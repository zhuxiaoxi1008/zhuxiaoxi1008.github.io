# React-native 学习笔记

## 1. React-native 简介

> https://reactnative.dev/docs/environment-setup

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
Andy
droid4x
Windroy
Genymotion
Ko Player
Memu
NOX

