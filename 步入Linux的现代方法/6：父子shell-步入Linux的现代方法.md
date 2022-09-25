@[TOC](目录)
## 6.1 父子shell的概念

 - `bash`
 - `ps-f`
 - `ps –forest`

 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508222951588.png)
## 6.2 分号在命令里有什么作用

 - 命令之间带分号 ； 依次执行
 - 创建一个子shell去执行

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508223320975.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508223420916.png)

## 6.3 sleep和jobs

 - `sleep` 将目前动作延迟一段时间 ，后面可接 `s` 为秒，`m` 为 分钟，`h` 为小时，`d` 为日数
 - 挂在后台,如果要干掉，则用`kill`命令
 - `jobs` 显示作业的状态，`-l` 在作业信息中额外的列出PID
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508224836659.png)

## 6.4 后台

 - 后台执行 `tar -zxvf ……；&`

## 6.5 coproc协程

 - Liunx协程处理命令。协程可以同时做两件事。在后台生成一个子shell，并在子shell中执行命令
 - `coproc sleep 10`
 - `coproc frank_av{ sleep 10; sleep 300;}`
 - **一定要分号结尾，大括号内空格**

## 6.6 外部命令和内建命令

 - Shell执行的命令可以分为内建命令（built-in）和外部命令（external） 前者是构建在shell内部
 - 后者是一个独立的文件（可以是二进制文件，也可以是一个脚本） 内建命令由当前shell本身来执行，例如echo, cd等等
 - 外部命令的执行shell进程会fork一个子进程，父进程随后挂起，然后在子进程中exec加载外部文件，子进程返回后，父进程才继续执行

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508224237416.png)

## 6.7 alias别名

 - `alias` 定义或显示别名。
 - `type` 显示指定命令的类型。
 - `alias li=’ls -li’`
 - 但是关闭当前shell就不能用了

## 6.8 章节结束语与经验

 - 掌握与熟用

