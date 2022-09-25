@[TOC](目录)

# 0.1 引言
前接Java与生活，该课属于Java进阶阶段

> **详见：[Java与生活](https://blog.csdn.net/qq_46207024/article/details/120645238?spm=1001.2014.3001.5502)**

# 0.2 API的定义和用处
**API 的定义和作用**

 - API是应用程序接口，是为了方便客户和开发人员使用，以实现某种功能
 - Java API就是提供给JAVA工程师的一种方法库，API文档中拥有Java 的大部分知识
 - 这些API就是一些JDK里面给我们的类，这些类已经封装完成，在使用过程中只需要了解它的功能
 - 同时我们书写API也是将API写好，最后由别的工程师去利用


# 0.3 Scanner（普通类）
`Scanner`里面提供了许多与扫描相关的方法，通过这些方法我们大概可以猜测，API里的方法要如何命名，对于不用数据类型的返回值方法要如何写，对于变量不同的方法，我们又要如何写

命名的名字要和方法的操作有相关性，名字上要体现是什么返回类型的，并通过方法的重载来实现

```java
package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        // 从键盘接收数据

        // next方式接收字符串
        System.out.println("next方式接收：");
        // 判断是否还有输入
        if (scan.hasNext()) {
            String str1 = scan.next();
            System.out.println("输入的数据为：" + str1);
        }
        scan.close();
    }
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/6834333a39674ff3869a8e62487c2dbc.png)

```java
String str1 = scan.nextLine();
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/1d35021e5ea74d49af1dde5e9c011b8f.png)
`Ctrl+左键`点击`Scanner`可以查看源代码
![在这里插入图片描述](https://img-blog.csdnimg.cn/1b9f770924ec4870973246a4b521777b.png)

图标有个小锁表示JDK自带的文档，禁止改动这里面的代码
![在这里插入图片描述](https://img-blog.csdnimg.cn/2575cb315b3149528138c3331ae2f205.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



# 0.4 Number（包装类）
`Number`类是使用面向对象的思想重新定义了数据类型，将全部的数字数据类型变成一个对象，并且全部继承`Number`类中，对这些数据类型进行维护，并且为这些数据类型提供相应的方法

这些对象式的数据类型和原始数据类型最大的区别就是有无方法的支持



> 所有的包装类（Integer、Long、Byte、Double、Float、Short）都是抽象类 Number 的子类。
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/b43b58ad1cbf4ce8ad36e7c646ec1dc1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_16,color_FFFFFF,t_70,g_se,x_16)
> 这种由编译器特别支持的包装称为装箱，所以当内置数据类型被当作对象使用的时候，编译器会把内置类型装箱为包装类。相似的，编译器也可以把一个对象拆箱为内置类型。Number 类属于 java.lang 包。
![在这里插入图片描述](https://img-blog.csdnimg.cn/fd81a6f587104aa6a3896e7c43234bc1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

调用方法用英文的句号
![在这里插入图片描述](https://img-blog.csdnimg.cn/cc835382cfde4b2b8494743f5f1f9a8b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_17,color_FFFFFF,t_70,g_se,x_16)

```java
public class Main {

    public static void main(String[] args) {
        Integer x = 5;//x装箱，拿来赋值
        x = x + 10;//x拆箱，拿出来用
        System.out.println(x);
    }
}
```

# 0.5 Math（工具类）

Java 的 `Math` 包含了用于执行基本数学运算的属性和方法，如初等指数、对数、平方根和三角函数

`Math`类在使用时不用new一个对象，只要`Math.方法`就可以使用这个方法，`Math`的方法都被定义为 `static` 形式，通过 `Math` 类可以在主函数中直接调用。

例如，取大的值函数为`Math.max()`，就是一个螺丝刀(`Math`)拧螺丝(`max()`)，没有必要每一次拧螺丝的时候都买一把新刀


![在这里插入图片描述](https://img-blog.csdnimg.cn/1737eceb388c462bb7ca0524947ef493.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_17,color_FFFFFF,t_70,g_se,x_16)


# 0.6 Random（父子类）
`Random`是随机数类，使用时间戳来控制生成随机数的过程

`Random`的返回值是：Returns a pseudorandom, uniformly distributed int value between 0 (inclusive) and the specified value (exclusive), drawn from this random number generator's sequence sentence，即返回一个伪随机、均匀分布的 int 值，介于 0（包括）和指定值（不包括）之间，取自该随机数生成器的序列。

```java
        System.out.println(Math.random());
```

```java
        Random random = new Random();
        int random1 = random.nextInt();
        System.out.println(random1);

        int random2 = random.nextInt(10);
        System.out.println(random2);
```



# 0.7 ThreadLocalRandom
`ThreaLocalRandom`是`Random`的子类，相对于Random的功能更全面和高效，同时线程安全，在使用的过程中也与时间戳有关，用于并发操作，`current` 表示当前线程



```java
        double i = ThreadLocalRandom.current().nextDouble(0.9, 1.5);
```

# 0.8 Date
`Data`类是一个非常简单、基础、底层的的类，已经过时(Deprecated)，但有很多用法是根据这个基础类来进行衍生，是一个对于时间非常重要的类

调出系统时间
```java
        System.out.println(new Date());
```
或者
```java
        Date date = new Date();
        System.out.println(date);
```
常见的是用字符串转换为时间，自动调用`toString`，以毫秒开始，所以需要乘1000
```java
        System.out.println(new Date(1647739190L * 1000));
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/c94f1ee72f7f408fa19cc2186d3a1baf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 0.9 DateFormat和SimpleDateFormat
是`Date`的衍生类，`DataFormat`用于对时间格式化，使用的过程中需要使用它的子类`SimpleDataFormat`

项目 | 含义|表示|示例
-------- | ----- | ----- | ----- 
y 　　　 | 　年 　　　　　　　　　 | 　　　Year 　　　 | 　1996
M 　　　 | 　年中的月份 　　　　　 | 　　　Month 　 　 | 　07
D 　　　 | 　年中的天数 　　　　　 | 　　　Number 　　 | 　189
d 　　　 | 　月份中的天数 　　　　　 | 　　Number 　　　 | 10
E 　　　 | 　星期 　　　　 | 　　　Text 　　　 | 　Tuesday; Tue
H 　　　 | 　一天中的小时数（0-23）　 | 　Number 　　 | 　0
h 　　　 | 　am/pm中的小时数（1-12） |      Number 　　 | 　12
m 　　　 | 　分钟数 　　　　　 | 　Number 　　 | 　30
s 　　 　 | 　秒数 　　　　　 | 　　Number 　　 | 　55
S 　　　 | 　毫秒数 　　　　　　　　 | 　　Number 　　 | 　978


```java
    public static void main(String[] args) {
        Date date = new Date();
        DateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        System.out.println(dateFormat.format(date));
```

```java
2022-03-20 09:41:31
```

# 0.10 Calendar(日期类)
`Calendar`类是对日期和时间进行控制的，在这个类中有许多的字段，可以直接当作工具类进行使用，在社交软件中我们可以用这个来计算年龄

```java
        Calendar calendar = Calendar.getInstance();
        int  year = calendar.get(Calendar.YEAR);
        System.out.println(year);
```

```java
2022
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/999a38f8fb7943c1a621199042dffabf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 0.11 System（系统类）

`System`类代表系统，系统级的很多属性和控制方法都放置在该类的内部

获取时间戳

```java
        System.out.println(System.currentTimeMillis());
```
```java
1649426343473
```


