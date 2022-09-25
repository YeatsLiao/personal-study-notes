@[TOC](目录)

# 1. 相对论和IO流之说
 **Input/Output Stream**
 

 - 词典中`Stream`的意思是有方向性的流动的液体/电流，强调过程
 - 理解`I/O Stream`可以看作是输入/输出方向的流体

![在这里插入图片描述](https://img-blog.csdnimg.cn/1e5662a519734a0584ad7cd5a1f34904.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



**从相对论的角度看待 I/O流**

 - 冬天旱季的时候，支流把水输出到长江中，长江输入这些水
 - 夏季雨季的时候，支流转换角色输入这些水，而长江输出这些水
 - 流必须要有管道，流动一定会有输出口和输入口，而谁输出、谁输入要看你选定的参照系

![在这里插入图片描述](https://img-blog.csdnimg.cn/24df3861e2584c37af6909795295f424.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)





# 2. 汉语文学理解IO流

 - 解释流这个词，像水流的东西输入/输出
 - 有一个物体会流动，像水一样，有输入和输出两种方式或者两种方向

![在这里插入图片描述](https://img-blog.csdnimg.cn/be2c77c569dc4c8eb7ff213bbc37d452.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 3. 图解IO流
**I/O Stream 文档中的两幅图**

>  **详见：[I/O Streams (The Java™ Tutorials > Essential Java Classes ...](https://docs.oracle.com/javase/tutorial/essential/io/streams.html)**

![在这里插入图片描述](https://img-blog.csdnimg.cn/035f3a89bae44290986cdca2693bd0ac.png)
**Reading information into a program** 读数据，数据源数据流到了程序中，对于程序是`input`，对于数据源是`output`，是程序在读取数据源中的数据

![在这里插入图片描述](https://img-blog.csdnimg.cn/19bc50f63a694fc29cdb8c292339cdfa.png)
**Writing information from a program** 写数据，程序数据流到了数据源中，对于程序是`output`，对于数据源是`input`，是程序在往数据源中写数据

上面两种方式都是站在程序的角度上对数据源的操作，参照物是程序，因为我们操纵的就是程序



# 4. 俩亲爹：InputStream和OutPutStream
**终极静态父类**

 - I/O流就是用来管理各种数据的输入和输出，在这个包中有两个终极静态父类，`InputStream`和`OutputStream`
 - 这两个类提供和数据操作相关的方法，后有其他不同类型的数据控制子类来继承这两个类

`InputStream`专门管理数据的读相关操作
![在这里插入图片描述](https://img-blog.csdnimg.cn/b1a500a9d1f44d45b982a02a4279c148.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


`OutputStream`专门管理数据的写相关操作
![在这里插入图片描述](https://img-blog.csdnimg.cn/a76b8aebdf3245cc9c70763ec53e3fe6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 5. FileInputStream字节流读取文件

> **参考：[java基础知识之FileInputStream流](https://blog.csdn.net/ai_bao_zi/article/details/81097898)**

文件读取流，创建一个`file`文件夹，将其作为`Resources Root`目录
![在这里插入图片描述](https://img-blog.csdnimg.cn/db77ab9657c84e84aa1a14403ae106c3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_18,color_FFFFFF,t_70,g_se,x_16)
在`file`文件夹下创建`1.txt`文件，随便写入一点东西，`.read()`方法是按照字节的二进制形式一个一个读取的，如果不想看到ASCII码，就需要将它转换成`(char)`类型，在代码的末尾要加上`.close()` 关闭程序

![在这里插入图片描述](https://img-blog.csdnimg.cn/4aea2e9769e04495b32118e1fd3f5f33.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 6. FileOutPutStream字节流写入文件
文件输出流，创建`2.txt`空文件，`.write()`方法读取整个字节数组，不需要使用for循环也能全部写入文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/ee8d715866ca466f8f15f72034e40df6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2746eeac83a04ed78f2fa5eb39423f2e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 7. buff缓冲复制文件

**引出缓冲概念**

 - 文件流的读取是一个一个字节读的，写也是一个一个字节写，是否可以将读文件的字节传输到写文件的字节流里面，相当于完成文件的复制呢？
 - `buff`就相当于缓冲，搬箱输入与输出，复制文件就不需要一个字节一个字节传了


![在这里插入图片描述](https://img-blog.csdnimg.cn/c059da49f43f47ec8b1f7a7b0817e89c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 8. buffered字节缓冲流、装饰设计模式
**引出缓冲区**

 - 在原来的读写文件中按单个字节的方式速度很慢，加了缓冲区以后，一次性读1024个字节，这样就会更快
 -  `Buffer` 类是 `java.nio` 的构造基础，一个 `Buffer` 对象是固定数量的数据的容器，其作用是一个存储器或者分段运输区，数据可被存储并在之后用于检索

`BufferInputStream`源码中这是缓冲输入流一次性读取8192个字节流

![在这里插入图片描述](https://img-blog.csdnimg.cn/3a01a5231abf4543b905dd451b32d259.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



**装饰模式**

 - 又名包装(Wrapper)模式。装饰者模式以对客户端透明的方式扩展对象的功能，是继承关系的一个替代方案

以复制文件函数为例，在这里不能直接将`path`路径传入到`BufferedInputStream`，而是使用了文件输入输出流创建的对象。`BufferedInputStream`中接收的是**对象**而不是字符串，这就叫装饰设计模式
![在这里插入图片描述](https://img-blog.csdnimg.cn/47e272ac43c048628c6e450029e05e8a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 9. FileReader和FileWriter，俩专门来搞定txt文件



 - `FileReader`类从`InputStreamReader`类继承而来。该类按字符读取流中数据
 - `FileWriter` 类从`OutputStreamWriter` 类继承而来。该类按字符向流中写入数据

这两种流非常适合用来读取文本文件一类的文件，不需要再设置字节数组来进行读取，在写文件的时候也不需要获取字符串的字节流
![在这里插入图片描述](https://img-blog.csdnimg.cn/17c3fa0a74bd413d8c9ea337791909f8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 10. BufferedReader、BufferedWriter

`BufferedReader`可以直接读取一行的信息

![在这里插入图片描述](https://img-blog.csdnimg.cn/9565c103a9d441d1b8e82e78331a9cf5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`BufferedWriter`也非常简单，但要注意**把流关闭**，特别是写文件的时候，如果没关，写出来的文件中不会有内容显示
![在这里插入图片描述](https://img-blog.csdnimg.cn/033e8ac796fa4f68b4aea29344a8eaf1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)




# 11. 一次性讲解剩余的N个流(扩展课)Java里那些极其骚的IO流
各种流的体验
# 12. Apache Common IO
Apache Commons IO是对java.io的扩展，其对IO封装了一些好用的工具类，只需要少量的代码就能完成大量的IO操作
> **Apache Common IO下载详见：[Apache Commons IO](https://mvnrepository.com/artifact/commons-io/commons-io)**

![在这里插入图片描述](https://img-blog.csdnimg.cn/d3cf9aa2053e4a29826f7c1d2a3a17a9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
例如要写入数据，只需一行代码就能搞定了，其它相关方法可以自行学习
![在这里插入图片描述](https://img-blog.csdnimg.cn/877f36bfc52d4ae695c61bdf91d1c8ca.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 13. IO流结束语

