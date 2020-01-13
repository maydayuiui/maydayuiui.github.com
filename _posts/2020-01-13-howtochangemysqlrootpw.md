---
layout: post
title: How to change mysql root password if you forget it
---

Sometimes you forget the mysql root password, or you just do a DB restore from backup file and you don't know the root password. Then, you can follow below instructions to reset your mysql root password.

```
// Stop mysqld if it's running by systemctl or just kill it.
// Use mysql account
$ cat /home/me/mysql-init
ALTER USER 'root'@'localhost' IDENTIFIED BY 'abcd1234';
$ mysqld --init-file=/home/mysql/mysql-init &
// now your root password is abcd1234, test it. and restart mysqld.
$ mysql -uroot -p
mysql> shutdown
```
