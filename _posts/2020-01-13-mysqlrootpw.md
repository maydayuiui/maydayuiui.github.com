---
layout: post
title: How to change mysql root password
---

If you forget mysql root password or just restore DB from a dump file. You may need to change root password.

```
// Stop mysqld if it's running by systemctl or just kill it.
// mysql account
$ cat /home/me/mysql-init
ALTER USER 'root'@'localhost' IDENTIFIED BY 'abcd1234';
$ mysqld --init-file=/home/me/mysql-init &
$ mysql -uroot -p
mysql> shutdown
```

This method works for version 5.7 and 8.0. 
