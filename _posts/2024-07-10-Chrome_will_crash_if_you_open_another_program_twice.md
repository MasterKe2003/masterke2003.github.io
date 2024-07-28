---
title: "Chrome浏览器内打开其他软件两次必定崩溃"
date: 2024-07-10 18:18:00 +0800
tags: [chrome,bug,吐槽]
---

> bug描述

最近发现了一个bug，Chrome浏览器经常在打开下载文件夹或通过URL调起软件时崩溃，而且很容易复现。但我的另一台电脑没有这个问题，两台电脑都是win11系统，Chrome版本都是最新的，后来也装了测试版，也有这个问题。
> bug原因

Directory Opus + win11 + 搜狗输入法或微信输入法

> 问题解决

该问题已经在DOpus最新测试版（13.6.3.0）中修复，参考官方论坛BUG反馈帖子：[Chrome Crashes with DOpus and Chinese Input Methods on Windows 11 – Help & Support – Directory Opus Resource Centre](https://resource.dopus.com/t/chrome-crashes-with-dopus-and-chinese-input-methods-on-windows-11/50811)

下面是这个帖子的大概内容：

## 背景
自从Windows 11发布以来，使用Directory Opus（DOpus）的中国用户遇到了一个问题：将DOpus与搜狗/微信输入法结合使用会导致Chrome崩溃。以下是一些来自中国互联网的帖子，记录了这个问题：
  * [Chrome最近是否经常崩溃？ - V2EX](www.v2ex.com)
  * [Windows 11下Chrome崩溃案例分析 – HafuHafu](hafuhafu.com)
  * [Windows 11下Chrome频繁崩溃，你也这样吗？ - V2EX](machbbs.com)
经过调查，问题似乎源于DOpus注册的ShellExecuteHooks。删除这个注册表键可以防止Chrome崩溃。除此之外，还有几种方法可以防止Chrome崩溃：
  1. 删除DOpus中的ShellExecuteHooks键
  2. 卸载微信输入法或搜狗输入法
  3. 恢复到Windows 10

需要注意的是，这些Chrome崩溃发生在以下特定情况下：
1. 在下载页面点击“在文件夹中打开”
2. 任何启动外部应用程序的场景（例如，在Telegram中点击“在Telegram中查看”）
总结来说，崩溃发生在Chrome需要调用shell32.dll时。

## 附加信息

我还尝试使用x64dbg附加到chrome.exe，并发现了可能的问题原因：`shell32.dll`访问了一个空指针指向的内存。这个问题是因为`dopuslib.dll`中的一个函数调用了`TlsSetValue`，导致shell32.dll读取的TLS值不正确。然而，切换回内置的Windows输入法会在`dopuslib.dll`中增加一个`TlsFree`步骤，使其正常工作。

## 复现步骤
  1. 安装Windows 11
  2. 安装Chrome的官方版本
  3. 安装DOpus
  4. 安装搜狗输入法并切换到它
  5. 在Chrome中打开[https://t.me/IbDirectoryOpusGroup](https://t.me/IbDirectoryOpusGroup)并重复点击页面上的“在Telegram中查看”按钮

## 总结
因此，我想知道DOpus是否可以尝试解决这个问题，或者至少提供关于DOpus注册的ShellExecuteHooks的作用信息。如果它的作用不是至关重要，我建议中国用户自己删除这个注册表键。
[接下来的对话涉及技术细节，主要是关于如何解决这个问题的讨论。]
最后，版本13.6.3（Beta）似乎已经修复了这个问题。版本13.6.x Beta的特性将被合并到版本13.7中。