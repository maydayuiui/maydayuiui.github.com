---
layout: post
title: VPS简单加固
---

1. 建立普通用户，禁止root登陆。
> 遇到`su: Authentication failure`。运行：`chmod u+s /bin/su`解决。
2. 安装[denyhosts][1]。自动把N次连接失败的IP加入/etc/hosts.deny。

[1]: http://www.cyberciti.biz/faq/block-ssh-attacks-with-denyhosts/
