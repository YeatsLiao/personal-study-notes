@[TOC](目录)

# 1. String存在的问题

**认识String**

 - 字符串广泛应用在编程中，在 Java 中字符串属于对象，Java 提供了 `String` 类来创建和操作字符串
 - `String` 创建的字符串存储在公共池中，而 new 创建的字符串对象在堆上
 - `String` 类是不可改变的，所以你一旦创建了 `String` 对象，那它的值就无法改变了


假设有两个`String str1`和`str2`，在创建这两个`String`类的时候计算机会给他们各自一块内存，当执行`str1 = str1 + str2`时，按逻辑是str1的内存内容被修改，内存只占了两块，但实际情况是创建了第三块内存`str1(str1+str2)`
![在这里插入图片描述](https://img-blog.csdnimg.cn/a44b3f759a7b4b64b87aa0691c9c9f91.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_18,color_FFFFFF,t_70,g_se,x_16)


# 2. Stringbuilder以及链式调用的含义
**`StringBuilder`和`StringBuffer`类**

 - 可以解决对字符串进行修改，但`StringBuffer`涉及不是线程安全的，使用情况较少

**和`String`的区别**

 - 创建单个`String`类是创建单个对象，创建多个就是创建多个对象，`StringBuilder`是对对象进行操作，一直操作的都是一个对象


![在这里插入图片描述](https://img-blog.csdnimg.cn/e24b5a87fb7642af9f7bdc280989e98c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_16,color_FFFFFF,t_70,g_se,x_16)


![在这里插入图片描述](https://img-blog.csdnimg.cn/1e46dbf0f21448a98defaec7f7cc418c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



 `trimToSize()`方法用于最小化用于字符的存储，也就是去空
```java
        stringBuilder.trimToSize();
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/318d858a97e04730b9119d015a2ec6a3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


