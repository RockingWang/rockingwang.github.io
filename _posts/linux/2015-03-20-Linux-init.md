---
layout: post
title: Linux的启动说明
category: Linux
keywords: linux init
---

#Linux的启动相关

>遇到情况说明：同事添加Weblogic开机自启动，导致服务器开机后黑屏，只有weblogic可以访问，其他包括Oracle数据库和SSH均无法使用。

###解决方案

远程访问weblogic的web管理器进行关闭服务，关闭后其他服务顺序自启动。

###原因

在`/etc/rc.d/rc5.d`文件夹中得`S20weblogic`的启动顺序为20，先于X、Oracle、SSH等服务启动，故没有图形界面，无法访问数据库和SSH。

###扩展

####Linux开机自启服务

Linux启动时，会运行`init`程序，由它启动后面的任务，包括多用户环境、网络等。

	修改文件：/etc/inittab 中 id:3:initdefault的数字

Linux操作系统有六种不同的运行级（run level），在不同的运行级下，系统有着不同的状态，分别为：

* 0：停机：千万不要把initdefault设置为0，会导致Linux无法启动
* 1：单用户模式：类似win9x的安全模式
* 2：多用户：但是没有NFS
* 3：完全多用户模式：标准运行级，常见的字符终端界面
* 4：一般不用，在一些特殊情况下使用
* 5：X11，即进到X-Window系统
* 6：重新启动：会导致Linux不断地重新启动