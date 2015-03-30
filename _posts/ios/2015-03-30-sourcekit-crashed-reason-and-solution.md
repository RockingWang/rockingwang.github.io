---
layout: post
title: Sourcekit Crashed 原因分析及解决方案
category: 技术
keywords: sourcekit crashed
---
# SourceKitService Crashed

## 原因分析

[[原文](http://www.th7.cn/Program/IOS/201411/314500.shtml)]
swift编译和使用过程中，xcode有时候会报SourceKitService Crashed、SourceKitService Terminated异常（Editor functionality temporarily limited），导致编译没有问题，但是xcode不会高亮显示代码，也不能提示代码。异常如下代码：

		SourceKitService Crashed
		Crashlog generated in ~/Library/Logs/DiagnosticReports
		Editor functionality temporarily limited.

该问题是Kit报出的，一般是由于项目名称中包含‘swift’这个词或者注释包含中文所导致.

## 解决方法：

1. [[原文](http://www.th7.cn/Program/IOS/201411/314500.shtml)]简单解决就是修改项目名称，将所有中文注释换为英文（包括头注释中的版权信息中的 2014年，这个年字也会影响），若仍不起作用需要新建项目，然后进行迁移。
2. [[原文](http://stackoverflow.com/questions/26295799/sourcekitservice-crashed)]Have this problem with Xcode 6.1 (release, not GM).<br/>There a few “magic” solutions that works temporarily, but require a restart. <br/>There is quick fix that seems to hold (and does not require a complete restart).<br/>Delete the content of: DerivedData/ModuleCache<br/>(Full path: ~/Library/Developer/Xcode/DerivedData/ModuleCache)



