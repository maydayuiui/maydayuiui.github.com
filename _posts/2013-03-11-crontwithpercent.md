---
layout: post
title: 在cron中使用date +%Y
---

#在cron中使用date +%Y
之前在crontab中加入了一些entry，今早查看发现没有正常运行。查看cron log：

    ...rsync.log.`date +)

命令最后在\`date +就结束了。没有运行**%Y**等。于是bing之。发现**%**在cron中是特殊字符，必须使用\转义之。

最后在[wiki][1]中找到了完整的解释：

> Percent-signs (%) in the command, unless escaped with backslash (\\), will be changed into newline characters, and all data after the first % will be sent to the command as standard input.

[1]: http://en.wikipedia.org/wiki/Cron
