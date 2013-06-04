---
layout: post
title: Branded Zones
---
# Branded Zones
每年都会给包含zone的Solaris打patch，一直都是直接在global zone里打patch，sub-zone中的patch也会一并打上。直到去年，有些zone需要进入到sub-zone中去打patch。除此之外，还有一个区别，当使用`uname -a`查看版本时，版本显示为`Generic_Virtual`。没有直接显示出版本号，需要使用`showrev -v`的方式来查看。

今天才醒悟过来，需要直接到subzone中打patch的都是Solaris 9或8。而我们的global zone都是Solaris 10。它们并不是直接继承的global zone。而是需要某种转换。

在[wiki][1]里有更加详细的叙述，这种叫做Branded Zone。

[1]: http://en.wikipedia.org/wiki/Solaris_Containers#Branded_zones

> 'solaris9' provides a Solaris 9 environment on a Solaris 10 system, including translation from Solaris 9 system calls to Solaris 10 system calls (available only on SPARC systems)

在每个sub-zone中有一个参数`brand`。如果`brand=solaris9`，则sub-zone为solaris 9的系统。这个参数只能在创建zone时设置。可以使用`flasharchive`来创建solaris 9的安装文件，进而install进zone中。

