@[TOC](目录)
#	1. 软件架构
**B/S 架构软件 —— 我们所有的东西都希望通过网站的形式使用，而不依赖于任何其他第三方环境，且依赖于浏览器的应用**

##	B/S 
通俗来说就是开发网站
 -	Web程序 office网页端
##	C/S  
桌面应用—— 基于C/C++的QT开发（岗位少）
 -	WPS office
#	2. 开发B/S架构软件需要哪些人才？
 -	前端
 -	后端
 -	测试
 -	运维 —— 管服务器、管部署
 -	产品经理（PM）
 -	首席技术官CTO【技术岗最高职位】（可能没有）
 -	架构师【技术岗次高职位】
#	3. 前端准备
 -	Vs Code
 -	Google Chrome 
 -	Nodejs
 -	设置淘宝镜像命令

```python
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

 -	Yarn（可选）如果你要安装它，前提是必须安装Nodejs
 -	查看当前镜像源

```python
config get registry
```

 -	修改淘宝镜像

```python
yarn config set registry https://registry.npm.taobao.org/

```
-	切换自带镜像源

```python
yarn config set registry https://registry.yarnpkg.com
```

#	4. 前端
##	HTML
（超文本标记语言——HyperText Markup Language）是构成 Web 世界的一砖一瓦。它定义了网页内容的含义和结构。
##	CSS
网页的表现与展示效果
##	JavaScript
 (JS)功能与行为
##	JS 框架
Jquery Vue React
##	css 框架
bootstrap   ELEUI 
##	Web开发
MDNWeb
#	5. 后端
##	VMware 虚拟机
##	Linux基础
 -	vim  shell 
 -	Linux RedHat    Kali  
 -	Ubuntu  16.04 18.04
 -	Centos 
 -	开源与闭源 
特殊的几个人能看见（开发组）
 -	阿里镜像源

```python
https://mirrors.aliyun.com/ubuntu/
```

 -	设置root密码

```python
sudo passwd root
```

 -	安装必要软件

```python
sudo apt-get install openssh-server
```

 -	ssh连接

```python
ssh liyoh@xxx.xxx.xxx
```

##	后端语言：Java/Go/Nodejs/C#(.NET)/Python/PHP 
 -	JSP -> html 里面扩展java代码 eg: <%for...%>
 -	前后端分离
 -	pm2
##	HTTP服务器搭建软件：Tomcat/Nginx/Apache 
 -	Express  
 -	公网IP  网站所有人都能打开 
 -	DNS服务器解析 备案  买域名

##	数据库：MySql/Oracle/SQLServer/SQLite/MongoDB/Redis
 -	动态页面 ：和用户之间具有数据交互
 -	CRUD：对数据的 增删改查
 -	Mysql5.7
[https://dev.mysql.com/downloads/mysql/5.7.html](https://dev.mysql.com/downloads/mysql/5.7.html)
 -	Ubuntu18.04 
[https://blog.csdn.net/weixx3/article/details/80782479](https://blog.csdn.net/weixx3/article/details/80782479)
 -	连接Mysql
NVIcat
TypeORM
##	计算机网络
(↓以下仅供了解)
##	MVC模式
 -	model 模型
 -	service 层
 -	controller 控制器
##	HTTP API
 -	TCP 传输控制协议	UDP用户数据包协议
#	6. Git（前端后端）
 -	版本控制  
保留了一切的历史 可以让代码迅速恢复到你想指定的commit位置
 -	协作开发 —— 需要网络
在自己的电脑上使用git，那确实是有版本控制功能，没有协作开发功能
大家把每次写的东西放到哪？基于git的一个平台--GitHub，GitLab
如何放在Linux上部署运行？网站是怎么运行的？
#	7. 全栈（非常难）
前端（node.js）跨入后端
#	8. Devops（开发+运维）
开发+质量检测+技术运营
#	9. Github（好地方）
# 结束语
 注意休息， 尽可能不要透支身体
![在这里插入图片描述](https://img-blog.csdnimg.cn/8c5d16a703804566ad732c97846660df.png)
**以上所有内容来自课程个人笔记：[走向实战，学完C之后学什么？前端后端？Java？Python?网站开发？B/S开发预备课-Frank](https://www.bilibili.com/video/BV1d7411p7RF)**


