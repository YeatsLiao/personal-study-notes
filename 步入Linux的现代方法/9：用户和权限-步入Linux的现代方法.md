@[TOC](目录)

## 9.1 用户权限的含义和作用

 - 用户与权限
 - 不可能让所有人有所有的权限-不安全
 - 避免被入侵
 - 用户ID UID
 - 系统用户UID<500
 - `cat /etc/passwd`
 - `sudo cat /etc/shadow`

## 9.2 创建、删除、更改用户

 - 创建`sudo useradd user1`
 - 删除`sudo userdel user1`
 - `更改密码sudo passwd user1`
 - `chage` 修改帐号和密码的有效期限

## 9.3 group

 - linux组groups

目的 ：共享资源的权限

 - `tail /etc/group`
 - ubuntu不允许把所有用户纳入一个组，而是每个用户都有一个单独的组
 - `sudo groupadd groupfrank`
 - `sudo groupdel groupfrank`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210509102635653.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210509102643211.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)
## 9.4 文件、文件夹权限

 - `rwx` 文件所有者（Owner）组创始人的权限
 - `r-x` 用户组（Group）组下属成员权限
 - `r-x` 其它用户（Other Users）其它组成员权限

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210509104329602.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021050910435635.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)

> **详见：[Linux chmod命令](https://www.runoob.com/linux/linux-comm-chmod.html)**

## 9.5 作业：自学chmod命令

 - `usermod`命令 用于修改用户的基本信息。
 - `usermod` 命令不允许你改变正在线上的使用者帐号名称。
 - 当 `usermod` 命令用来改变user id，必须确认这名user没在电脑上执行任何程序

## 9.6 章节结束语

 - 边用边学，自学很重要


