@[TOC](目录)

## 4.1 CLI准备
CLI相关设置，选择`Preferences`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210505233347601.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)

 - `Theme Variant` 主题变换
 - `Open new terminals in` 打开一个新终端的方式，Tab代表在同一窗口下创建新终端，Window代表开一个新窗口打开新终端
 - `New tab position` 新终端位置，默认为上一次位置

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210505233353858.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)
快捷方式设置，`Ctrl+Alt+T` 打开新终端
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210505233401391.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)




## 4.2 CLI Terminal

```java
yeats@yeats-virtual-machine:~$
```

 - 用户名@机器名：当前所在目录   `$`表示等待用户输入
 - `~`表示用户`home`目录
 - `/home`是存放所有用户文件的根目录

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210505233412275.png)
`Settings`中`About`可以查看机器名与相关信息
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210505233755311.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)

## 4.3 搞定Linux命令参数，得心应手使用各类命令——授之于渔  先拿ls开张

 - `ls`命令 用来显示目标列表，在Linux中是使用率较高的命令
 - `ll#` 列出当前目录可见文件详细信息
 - `man`命令是`Linux`下的帮助指令，通过`man`指令可以查看Linux中的指令帮助、配置文件帮助和编程帮助等信息

> **推荐：[Linux命令搜索](https://wangchujiang.com/linux-command/)**

## 4.4 Linux根目录，它们和Windows有什么区别

 - Windows 盘符，文件目录 `\`反斜线
 - Linux一切皆文件，文件目录 `/` 斜线

## 4.5 Linux根目录解析，fhs权威论文，搞定所有的发行版本文件夹分布

 - `/` linux根目录
 - `/bin` 二进制目录 GUN工具 命令
 - `/cdrom` 光盘
 - `/etc` 系统配置文件
 - `/home` 用户主目录
 - `/lib` 库目录 存放库文件
 - `/lost+found` 当系统发生错误时，将一些遗失的片段放置在这个目录下
 - `/mnt` 挂载（外在的设备和电脑进行连接）目录
 - `/proc` 伪文件系统
 - `/run` 运行目录
 - `/snap` 包管理，软件包安装管理方式
 - `/tmp` 临时目录
 - `/var` 可变目录
 - `/boot`  启动目录
 - `/dev` 设备目录
 - `/media` 媒体目录
 - `/opt` 可选目录
 - `/root` root用户的主目录 管理员
 - `/sbin` 系统二进制目录，GNU高级管理员使用的命令或工具
 - `/srv` 服务目录
 - `/usr` 用户二进制目录，GNU工具

> **详见：[FHS文件系统层级标准](https://www.pathname.com/fhs/)**

## 4.6 cd命令

 - `cd` 进入用户主目录
 - `cd..` 切换到上一层
 - `cd –` 返回到上一次的工作目录。

## 4.7 Ctrl + C？ 拉到吧，在Linux上可不是复制

 - `Ctrl+c`( kill foreground process ) 发送SIGINT信号给前台进程组中的所有进程，强制终止程序的执行
 - `Ctrl+l`  清屏

## 4.8 绝对路径

 - 全路径 D:\Study\Frank_FuckPPT\Linux

## 4.9 相对路径

 - 不全路径 \Frank_FuckPPT\Linux

## 4.10 Linux上的路径与Windows上的路径

 - `gedit /Doucument/doc/1.txt` 操作根目录 绝对路径
 - `gedit ~/Document/doc/1.txt` 当前目录 相对路径
 - `gedit ./Document/doc/1.txt` 当前目录 相对路径
 - `gedit Document/doc/1.txt` 当前目录 相对路径

## 4.11 如何练习？经验课

 - 单点符号`.`当前文件
 - 双点符号`..`当前目录的父目录


## 4.12 ls进阶用法：文件夹下各种匹配过滤符号

 - `*`号替代多个符号

 - `？`号替代一个符号

 - `-a`,，`--all` 列出目录中所有文件，包括以“`.`”开头的文件

 - `-l`， `--format=long`，`--format=verbose`除每个文件名外，增加显示文件类型、权限、硬链接数等信息

 - `-F`，`--classify`， `--file-type`在每个文件名后附上一个字符以说明该文件的类型

## 4.13 touch命令
`touch`命令 两个功能

 - 一是用于把已存在文件的时间标签更新为系统当前的时间（默认方式）
 - 二是用来创建新的空文件

## 4.14 cp命令

 - `cp`命令 将源文件或目录复制到目标文件或目录中
 - 源文件：制定源文件列表。默认情况下，`cp`命令不能复制目录，如果要复制目录，则必须使用`-R`选项
 - 目标文件：指定目标文件。当“源文件”为多个文件时，要求“目标文件”为指定的目录
 - `cp` 你想复制的文件？ 你想复制到哪？
 - `-i`覆盖既有文件之前先询问用户
 - `-R/r`递归处理，将指定目录下的所有文件与子目录一并处理

## 4.15 cp递归练习技巧

 - `pwd` 显示当前工作目录

```java
 - cp -R ./*java ~/Documents/temp/
```

## 4.16 Linux终端光标移动技巧

 - `Tab`自动补全
 - `Ctrl + E` 跳到行尾
 - `Ctrl + B` 光标向左移动
 - `Ctrl + H` 删除光标前一个字符 相当于退格
 - `Ctrl + T` 把光标前一个字符往后移动
 - `Ctrl + R` 搜索之前用过的命令
 - `Ctrl + W` 删除光标前一个单词
 - `Ctrl + U` 删掉光标前面的内容
 - `Ctrl + K` 删掉光标后面的内容

## 4.17 lnk链接文件的介绍

 - `.lnk`快捷方式
 - Linux链接文件
 - 1.符号链接(软链接)
 指快捷方式	原来的文件/文件夹必须存在
 - 2.硬链接 
指副本	原来的文件/文件夹必须存在

## 4.18 符号链接和硬链接

 - `ln`命令 用来为文件创建链接，链接类型分为硬链接和符号链接两种，默认的链接类型是硬链接。如果要创建符号链接必须使用"-s"选项
 - `ln` 原文件名 链接的文件名
 - `ls -l` 查看
 - 软链接：有指向，是一个单独的文件，不同介质
 - 硬链接：无指向，同一介质
 - 软链接复制的是链接文件

## 4.19 注意事项

 - 符号链接Symbolic links
 - 软链接 Soft links

## 4.20 mv命令

 - `mv`命令 用来对文件或目录重新命名，或者将文件从一个目录移到另一个目录中
 - 做重命名，`mv 重命名谁 命名成什么`

## 4.20 移动和骚操作

 - 做移动，`mv 移动的文件 移动到的目录`
 - 输入完之后，`cd !$`
 - `!$`是列出并执行你的命令历史里面最近的一条记录

## 4.21 rm——最佳年度删库跑路

 - `sudo rm -rf /*`   该命令极度危险
 - `rm` 命令可以删除一个目录中的一个或多个文件或目录，也可以将某个目录及其下属的所有文件及其子目录均删除掉。对于链接文件，只是删除整个链接文件，而原有文件保持不变
 - `rm -i` 有提示
 - `rm -i -rf` 无提示

>  **注意： linux没有回收站**

## 4.22 创建文件夹以及删除文件夹

 - `mkdir` 用来创建目录
 - `rmdir` 用来删除空目录

## 4.23 文件类型

 - `file`用来探测给定文件的类型
 - Windows 文本是txt
 - linux 文本是text

## 4.24 cat ，more ，less

 - `cat` 连接多个文件并打印到标准输出，适用于短文本
 - `-n`, `--number` 对所有行编号，从1开始编号
 - `more` 显示文件内容，每次显示一，以全屏方式显示
 - `b`上一页 `space` 下一页 `q`退出
 - `less`分屏上下翻页浏览文件内容
 - `less`命令允许用户向前或向后浏览文件，而`more`命令只能向前浏览。
 - 用`less`命令显示文件时，用PageUp键向上翻页，用PageDown键向下翻页。要退出less程序，应按Q键
 - 浏览文件中输入 `/` 用于搜索

## 4.25 tail 和 head命令

 - `tail` 在屏幕上显示指定文件的末尾若干行

```javascript
tail -n 2 demo.c
```

 - `head`显示文件的开头部分

```javascript
head -n 2 demo.c
```

## 4.26 章节结束语和经验
