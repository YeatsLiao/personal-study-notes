@[TOC](目录)
# 1. 阶段

**Java NIO - File**

 - `Java NIO`中的`Files`类（`java.nio.file.Files`）提供了多种操作文件系统中文件的方法。
 - `Java Files`类是Java 1.7中引入的，是`java.nio.file`包的一部分

# 2. 字符集编码吹X


> **推荐学习视频：[【编码】中文编码介绍](https://www.bilibili.com/video/BV1ur4y1A7eq)**

 - 字符是许多字符的集合
 - 字符编码字面意思就是对字符进行编码，将某个字符映射成其他形式的数据以便在计算机中存储和传输
 - 如果每种语言都要出一种字符集来存储的话，那就无法统一标准了，会造成多冗余的工作
 - Unicode是为了解决传统的字符编码方案的局限而产生的，它为每种语言中的每个字符设定了统一并且唯一的二进制编码，以满足跨语言、跨平台进行文本转换、处理的要求

IDEA里面需要设置`Encoding`为中文编码`UTF-8`，企业里需要统一编码
![在这里插入图片描述](https://img-blog.csdnimg.cn/f47933ab2fdb4590862dcd9f21d6eb3c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 3. 转换字符编码


**任何数据都存在两种状态**

 - Encode编码
 - Decode解码

想要读取数据的模式，需要进行解码，即二进制通过解码变成明文

使用`getBytes`方法可以获得字符串编码，使用`Charset`类能够创建编码器和解码器
![在这里插入图片描述](https://img-blog.csdnimg.cn/6a778ab378ed4f0b9857d877a5667e54.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/7ffb2eed04b646389ffadc97b111068a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_18,color_FFFFFF,t_70,g_se,x_16)

> **参考：[Java批量转换文件夹中文件的编码（从gbk到utf8）](https://blog.csdn.net/qq1032355091/article/details/51803496)**

