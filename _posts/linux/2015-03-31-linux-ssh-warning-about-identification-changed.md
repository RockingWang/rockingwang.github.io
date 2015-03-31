---
layout: post
title: SSH出现冲突警告WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
category: 技术
keywords: Linux SSH
---

## 遇到问题

	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!Someone could be eavesdropping on you right now (man-in-the-middle attack)!It is also possible that the RSA host key has just been changed.The fingerprint for the RSA key sent by the remote host is36:68:a6:e6:43:34:6b:82:d7:f4:df:1f:c2:e7:37:cc.Please contact your system administrator.Add correct host key in /u/xlian008/.ssh/known_hosts to get rid of this message.Offending key in /u/xlian008/.ssh/known_hosts:2RSA host key for 135.1.35.130 has changed and you have requested strict checking.Host key verification failed.
	
## 原因分析

ssh会把你每个你访问过计算机的公钥(public key)都记录在~/.ssh/known_hosts。当下次访问相同计算机时，OpenSSH会核对公钥。如果公钥不同，OpenSSH会发出警告， 避免你受到DNS Hijack之类的攻击。
同一IP的主机上有多个Linux系统，会经常切换，那么这些系统使用同一ip，登录过一次后就会把ssh信息记录在本地的~/.ssh/known_hsots文件中，切换该系统后再用ssh访问这台主机就会出现冲突警告。或者Linux服务器重新安装ssh，也会导致冲突警告。

## 解决方案

1. 手动删除修改known_hsots里面的内容；
2. 修改配置文件“~/.ssh/config”，加上这两行，重启服务器。
   StrictHostKeyChecking no
   UserKnownHostsFile /dev/null

##### 优缺点：
1. 需要每次手动删除文件内容，一些自动化脚本的无法运行（在SSH登陆时失败），但是安全性高；
2. SSH登陆时会忽略known_hsots的访问，但是安全性低；