---
layout: post
title: SecureCRT乱码问题及解决方案
category: 技术
keywords: Linux SSH SecureCRT
---

# SecureCRT乱码问题

## 解决方案

1. 远程Linux机器，修改环境变量LANG。即在`~/.bash_profile`中添加`export LANG=zh_CN.UTF-8`.
2. 重新连接
3. 修改SecureCRT的设置。即 `Options` --> `Session Options` --> `Appearance` --> `Character encoding`选择`UTF-8`

> 查看[原文](http://blog.csdn.net/malundao/article/details/6584209)


## 未解决问题

1. 公司Linux没有改`~/bash_profile`。`echo $LANG`显示为`zh_CN.GB2312`，但是Mac上的SecureCRT修改encoding后乱码并没有改善。等待后续研究。