@[TOC](目录)
#	认识Java
# 0-0 前言
 **课程基础： [C语言教程(全网最具有比喻形象的)-Frank-FuckPPT](https://www.bilibili.com/video/BV1qE411d7Zx?spm_id_from=333.999.0.0)**
 - 学Java前需要学C，至少学到结构体，C语言课程是基础

 - 指针、算法、数据结构不好也没关系，师父领进门，修行靠个人

# 1-1 Java是怎么执行的？说好的exe呢？
对比Java与C构建模式
| JAVA                          | C                                  |
| ----------------------------- | ---------------------------------- |
| java执行时会生成`.class`文件  | C执行的时候会生成`.exe`文件（win） |
| java要运行必须有jdk、jre和jvm | C执行的时候不需要这些文件          |
| java`.class`跨平台效果好      | C`.exe`跨平台效果不好（win）       |

 - **jdk(Java Development Kit)：**  java程序开发工具包
 - **jre(Java runtime environment)：** java运行环境
 - **jvm(Java Virtual Machine)：** java虚拟机

# 1-2 package



`Java package` 如同文件夹一样，工程文件主要分为`idea`、`out`、`src`、`web`四个大包

**1.idea文件夹**

 - `.idea`存放项目的配置信息，包括历史记录，版本控制信息等

 **2.iml文件夹**

 - `iml`(infomation of module)是IntelliJ IDEA 自动创建的模块文件

 - 用于Java应用开发，存储一些模块开发相关的信息，还可能会存储一 些模块路径信息， 依赖信息以及别的一些设置

 **3.src文件夹**

 - 即`source`，存放的是项目的源文件(.java后缀与配置文件)

 - 分成几个包的目的：对代码的优化、实现高聚合、低耦合特点、便于以后的扩展和更改

**4.External Libraries** 

 - Java外部库

**5.Scratches and Consoles**

 - Intellij IDEA 提供了两种临时的文件编辑环境，两种 Scratches 分别是`Scratch files` 和 `Scratch buffers`




> Scratch files ：Scratch files 有着完整的运行和 debug 功能等等，这些文件需要指定编程语言类型并且指定后缀。
> Scratch buffers : Scratch buffers仅仅是为了简单的编辑记录，所以不需要指定编程语言并且指定后缀，默认文件类型是 .txt。需要注意的是，Scratch buffers最多只能创建 5 个，超过 5 个将开始重用以前的，并且以前文件的内容会被重置。


**6.项目视图**
默认是将`package`层级以简洁显示的,非精简模式
![在这里插入图片描述](https://img-blog.csdnimg.cn/17627d177f4f4b8c93bd3bd6627f063e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_11,color_FFFFFF,t_70,g_se,x_16)
对`packages`单击右键，点击`Compact Middle Packages`即可切换成精简模式
![在这里插入图片描述](https://img-blog.csdnimg.cn/7fd52a8d1e4f4990bbf4b1c57d87afc3.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_10,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/31f5b3c4d4ad4989bbd35b3e0491b497.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_11,color_FFFFFF,t_70,g_se,x_16)


# 1-3 第一个程序的讲解

```java
package com.microsoft.demo; //定位你的Java代码放在src文件夹下的位置

//公共的  类   类名（开头字母必须大写和文件名相同）
public class Main{ 
    
    //mian函数的固定格式
    public static void main(String[] args){
        
        //语句
        System.out.println("Hello");
    }
    
    //java函数
    public static int sum(int number_a,int number_b){
        return number_a+number_
    }
    //函数的调用和C是一样的
}
```


`ctrl+alt+v` 在调用函数的时候自动生成变量

`.soutv` 打印最靠近的变量，也可以是你自己选定的变量

>**参考： [IDEA——JAVA的快捷语法](https://www.cnblogs.com/wangyang0210/p/14185086.html)**

# 1-4 注释和文档

**1.基本注释**

 - 和C语言一样有单行注释和段落注释
 - 单行注释  `// ……`
 - 多行注释  `/* ...... */` 注释内容不会出现在javadoc 生成的文档中

 **2.方法注释和类注释**
 

 - 即文档注释 : `/** ...... */` 注释内容写入javadoc生成的文档
 - 注释格式`/** ...... */`里面的内容有介绍函数，还有方法中用到的参数和返回值
 - 这个可以快速生成一个方法文档（想要生成文档可以在快捷键里查doc）
 - IntelliJ IDEA 里查看一个函数注释的方法是 `ctrl+q`




# 2-0 一带而过

> **参考：**
>  - **[Java 基本数据类型- 菜鸟教程](https://www.runoob.com/java/java-basic-datatypes.html)**
>  - **[Java修饰符- 菜鸟教程](https://www.runoob.com/java/java-modifier-types.html)**
>  - **[Java 运算符- 菜鸟教程](https://www.runoob.com/java/java-operators.html)**

# 2-1 字符串演示


**C语言如何定义字符串?**

```c
char data[3] = {'a', 'b', 'c'};
char data[] = {'a', 'b', 'c', '\0'};
char data[] = "abc";
```

**Java如何定义字符串?**
```java
String s1 = "Hello World!";                 
String s2 = new String("Hello World!");
```

 - `String`是java中定义字符串的类，方便快捷，使用面向对象的方式还有很多骚操作
 - 获取字符串长度：`字符串名.length()`
 - 使用`.concat()`连接字符串
 - 使用`+`连接字符串


# 2-2 字符串结束符的那些事儿
**C语言种的字符串是怎样的？**

 - C语言中没有专门的字符串变量，通常用一个字符数组来存放一个字符串
 - 字符串本质上就是以`'\0'`作为结尾的特殊字符数组
 - 因此当把一个字符串存入一个数组时，也把结束符 `'\0'`存入数组，并以此作为该字符串是否结束的标志

**为什么Java里没有/0？**

 - 严格控制字符串，防止内存泄漏
 - 这是Java为了保护程序以及开发者友好，强制并自动为我们加了`'\0'`

# 2-3 自动类型那些事儿
**自动类型转换**

 - 整型、实型（常量）、字符型数据可以混合运算
 - 运算中，不同类型的数据先转化为同一类型，然后进行运算
 - 小品《主角与配角》象征性代表了`int`取代`char`的地位

```java
低  ------------------------------------>  高
byte,short,char—> int —> long—> float —> double 
```

#	2-4 import导包和API文档

 - `import`和C中的`#include`一样，导入一些自带的方法

 

 - 有一些包中的函数是不需要导入的，使用同一个`package`下的包不需要`import`
 - `java.lang.*`是java默认自带的

# 2-5 Java中的数组


对比C和Java静态数组定义方式

| 定义方式   | Java                        | C                      |
| ---------- | --------------------------- | ---------------------- |
| 初始化法   | `int[ ] arr ={1,2,3}`       | `int arr [] = {1,2,3}` |
| 分配空间法 | `Type[] arr=new Type[size]` | `int arr[size]`        |


普通的静态数组有缺陷：长度是固定的，不能扩容，没有灵活性 

==注意：==  **`String`的length带括号，数组里的length不带括号**

```java
str.length();
arr.length;
```

增强for循环
```java
for (int i: arr_2) {
     System.out.println(arr_2[i]);
}
```


```java
for(double element:myList){
	System.out.println(element);
}
```

# 2-6-1 Arrays第一讲
提供方法对数组进行操作，练习以后记录笔记

例如：排序`sort()`
```java
int[] arr_1 = {1, 2, 3, 6, 7, 8,111,1111,112,1235,123};
        Arrays.sort(arr_1);
        for (int element:arr_1) {
            System.out.print(element + " ");
        }
```

#	2-6-2 Arrays第二讲

例如：二分查找 `Arrays.binarySearch(arr_1,6)`

```java
		int result_index = Arrays.binarySearch(arr_1,6);
        System.out.println("result_index = " + result_index);
```
相同顺序下，数组是否相等`Arrays.equals(arr_1, arr_2)`

```java
 		int[] arr_1 = {1,2,3};
        int[] arr_2 = {1,2,3};
        boolean b = Arrays.equals(arr_1, arr_2);
        System.out.println("b = " + b);
```

# 2-7-1 函数和方法

**什么是方法?**

 - Java方法是语句的集合，它们在一起执行一个功能
 - 方法和C里的函数是一模一样的

>  **参考：**
>  - **[Java 方法-菜鸟教程](https://www.runoob.com/java/java-methods.html?_t_t_t=0.9364758810464391)**

# 2-7-2 方法的重载
方法名相同，参数个数或者参数类型不同
```java
package com.microsoft.demo;
import java.util.Arrays;
public class main {
    public static void main(String[] args) {
        int sum = sum(1, 2);
        double value = sum(1.2 , 3.4);
        System.out.println("sum = " + sum);
        System.out.println("value = " + value);
    }
    public static int sum (int x, int y){
        return x + y;
    }
    public static double sum ( double x, double y){
        return x + y;
    }
}
```

# 2-8-1 规范约束第一讲

> **详见：[阿里巴巴Java开发手册-alibaba/p3c](https://github.com/alibaba/p3c)**

# 2-8-2 规范第二课
# 2-8-3 规范约束第三讲
