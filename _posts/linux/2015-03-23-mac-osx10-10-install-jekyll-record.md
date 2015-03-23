---
layout: post
title: Mac OSX10.10安装jekyll记录
category: 技术
keywords: jekyll
---
#Mac OSX10.10 安装jekyll记录

###安装方式

Mac OS自带ruby和gem，所以直接在bash中用`gem install jekyll`即可

###遇到问题

1. Errno::ETIMEDOUT:Operation timed out - connect(2) ...(忘记截图见谅)
2. unable to convert "I" from ASCII-8BIT to UTF-8 for lib/yajl/yajl.bundle, skipping

###解决方式

1. 更新gem `sudo gem update --system`
2. 修改~/.bash_profile文件 `export LC_CTYPE="utf-8"`

###问题解决查找资源

* [stackoverflow](www.stackoverflow.com)

