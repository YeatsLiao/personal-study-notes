@[TOC](目录)

## 7.1 什么是环境变量？到底高清楚，彻底高清楚什么究竟是环境变量！！！！！

 - 环境变量（environment variables）一般是指在操作系统中用来指定操作系统运行环境的一些参数，如：临时文件夹位置和系统文件夹位置等
 - 文件夹写入的环境变量，意味则可以在任何位置访问该文件夹，相当于告诉系统这个目录在哪里

## 7.2 全局环境变量和局部环境变量

 - windows:系统变量与用户变量
 - linux: 全局环境变量和局部环境变量
 - 全局环境变量`printenv`
 - `printenv USER`
 - `echo $USER`
 - `cd $HOME`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508225612655.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508225701727.png)
## 7.3 用户和局部变量的定义

 - 局部变量只能在当前shell执行，子shell或者退出后就不能用了
 - 注意 定义局部变量不要大写
 - 全局变量用大写，下划线命名法
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508230607923.png)

## 7.4 定义全局变量

 - `export` 为shell变量或函数设置导出属性。
 - 可以子shell里执行，但关闭后仍失效
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508230858419.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021050823090874.png)
## 7.5 默认的环境变量
 - `set`
 
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508232418314.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)


## 7.6 为啥要用环境变量

 - 配置开发环境需要使用
 - 临时环境变量
 - `PATH=$PATH:/home/yeats/Templates/`
 
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210508231327312.png)

## 7.7 永久配置环境变量？

 - 启动文件：开机的时候默认执行的环境变量
 - `bash shell`
 - 1登录shell
 - 2非登录就打开shell
 - 3运行脚本非交互shell
 - `cat /etc/profile`
 - `~/.bashrc`
 - `~/.bash_profile`
 - `~/.profile`
 - `~/.bash_login`
 - `cat bashrc`


 - 加入全局环境变量(需学习vim)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021050823144961.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ2MjA3MDI0,size_16,color_FFFFFF,t_70)

