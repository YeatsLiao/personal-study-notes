@[TOC](目录)

 - 视频讲解很详细，主要是安装和配置操作，所以未记录太详细。
# 1.1 windows两种安装方式，入门选手推荐第二种(win10演示)
 - **Mysql官网下载地址：[https://dev.mysql.com/downloads/mysql/](https://dev.mysql.com/downloads/mysql/)**

>  **详见：[「MySQL」从零到删库精品课程P3](https://www.bilibili.com/video/BV18i4y187i3?p=3)**

# 1.2 更改终端，放弃cmd作为主要终端，使用一流终端
 - **Hyper官网：[https://hyper.is/](https://hyper.is/)（网络原因可能进不去，可以网上搜一下）**

>  **详见：[「MySQL」从零到删库精品课程P4](https://www.bilibili.com/video/BV18i4y187i3?p=4)**

# 1.3 MYSQL服务的启动与停止

 - 任务管理器中服务可以启动与停止Mysql Server。
 - Mysql是C/S架构软件。
 - 启动命令`mysql -u root -p`
 - 停止命令`net stop Mysql57`

>  **详见：[「MySQL」从零到删库精品课程P5](https://www.bilibili.com/video/BV18i4y187i3?p=5)**

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/8edc83aaf1e14c9caa4ae2ce4e93ec54.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 1.4 连接mysql
 - 连接Mysql`mysql -u root -p`
 - `-u` 指user用户，后接用户名，root表示用户管理员权限
 - `-p` 指passwd密码，表示接下来要输入的密码是隐藏的，也可以用`mysql -u root -p123456`直接输入密码
 - 关闭连接`\q` 或 `quit` 或`exit`
 - **详见：**[「MySQL」从零到删库精品课程P6](https://www.bilibili.com/video/BV18i4y187i3?p=6)

# 1.5 初始化data数据文件夹
Mysql目录：`C:\Program Files\MySQL\MySQL Server 5.7`
 - `bin`文件用来放命令
 - `include`包含头文件
 - `lib`引用库
 - `share`字符集编码

这里少了一个`data`数据文件夹，默认不创建，已管理员身份打开cmd，输入以下指令即可创建：

 - `cd C:\'Program Files'\MySQL\'MySQL Server 5.7'`
 - `mysqld --initialize-insecure --user=root`
 
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/cf63f4442ad04a2bb3691830ec43386c.png)
 
若出现`Set-Location : 找不到接受实际参数错误`，是因为路径包含空格识别不了，需要在有空格的目录加上引号
![在这里插入图片描述](https://img-blog.csdnimg.cn/970d190decf64bc793f410686273cdbf.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/bafbea9082dc433ea82c1005b0a08d51.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

