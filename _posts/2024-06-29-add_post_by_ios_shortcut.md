---
title:      "优雅的新增一篇博客"
date:       2024-06-29 09:00:00 +0800
tags: [博客,技术]
---

# 基于jekyll的博客搭建

这个教程有很多了，可以自行搜索
[基于jekyll的博客搭建](https://www.bing.com/search?q=%E5%9F%BA%E4%BA%8Ejekyll%E7%9A%84%E5%8D%9A%E5%AE%A2%E6%90%AD%E5%BB%BAs)

# 教程正文

## 思路

> 在搭建好我们的这样一个博客网站之后，新增一篇博客也就是要提交一次commit，然后push到github上，然而github提供了[这样的API](https://docs.github.com/en/rest/repos/contents?apiVersion=2022-11-28)，所以问题就变得简单了。

## PostMan调试

先搞到一个access_token，这个token是用来访问github的api的，在github的个人设置里面可以找到。

![](https://cdn.jsdelivr.net/gh/MasterKeee/picture/20240629225205.png)

![](https://cdn.jsdelivr.net/gh/MasterKeee/picture/20240629230558.png)

## 快捷指令实现

调通了api之后，就可以写一个简单的脚本，用来新增一篇博客。这边我可以分享一下我写的脚本，可以参考一下。记得打开快捷指令填写一些必要的信息。

[推送博客文章模板](https://www.icloud.com/shortcuts/1fe3e531bd7c4d5ab145810580cae6bb)

## 效果图
![](https://cdn.jsdelivr.net/gh/MasterKeee/picture/dfbf1159f9c015c5c6cac0349404060.png)

![](https://cdn.jsdelivr.net/gh/MasterKeee/picture/afb7f1b7ddce0db86db4b278d2800b5.png)

## 使用方法

下载一个markdown编辑器[MWeb](https://apps.apple.com/cn/app/mweb-markdown-%E5%86%99%E4%BD%9C-%E7%AC%94%E8%AE%B0%E5%92%8C%E5%8F%91%E5%B8%83/id1183407767)，然后编辑好了markdown之后，点击上面的分享，选择快捷指令就可以推送了。

![](https://cdn.jsdelivr.net/gh/MasterKeee/picture/ca8d525416a26667000d44de2a86e7b.jpg)

最后，这篇推文就是使用这个方法推送上去的。