@[TOC](目录)
# 1. 异常的介绍
**Throwable有两个子类**

1.错误 `Error`

 - 不常见
 - 基本上不能解决
 - 尽量避免

2.异常 `Exception`

 - 常见
 - 可以定位，通过修改代码解决
 - 不是编译失败问题，代码语法没有问题

# 2. 异常举例以及解决常见错误bug方案

 - 定位错误：编写好程序后，运行程序，在输入运行结果栏中会存在异常提示，红色中蓝色链接，就能找到自己的代码错误
 - 解决错误：先阅读异常提示，如果了解就直接修改，如果不了解那就搜索异常提示，了解问题所在，解决问题

最经典异常展示
![在这里插入图片描述](https://img-blog.csdnimg.cn/c6b224d7f07f4a209e289fa66d48f00e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 3. RuntimeException
异常类有两个主要的子类：`IOException` 类和 `RuntimeException` 类

1.运行时异常
 - 运行时异常可修改也可不修改，不会对项目运行产生影响
 - 运行时异常像游戏漏洞，它不影响我们玩游戏，但是我们有一些漏洞可以捡，比如更新以后某个英雄的技能，在某个时间可以无限的放或者平A就能秒死人
 
 2.非运行时异常
 - 非运行时异常必须修改，因为这样会使得项目直接无法运行（现在的编译器比较智能，一定会让你`try  catch`）
 - 但是非运行时异常导致你进不去游戏



编译器中，运行时异常不会要求你捕获，但是非运行时异常会强制要求你捕获，所以我们在编写自定义异常的时候不会定成运行时异常



# 4. trycatch作用，闲扯淡诱骗毕业设计
**`try catch`的作用**

 - 定位一个代码块的异常，运行完成这个代码块后，抛出这个代码块的异常
 - `try  catch`可以搭配`finally`使用，意思是在捕获完成以后使用，也可以不搭配
 - 但使用`finally`就必须搭配`try  catch`
 - try  catch的捕获内容可以自定义，可以让它抛出异常，也可以不让它抛出异常，所以根据这个小漏洞，你可以去骗毕业设计，**但工作中绝对不能用！**

抛出异常，正常捕获，运行可以通过，但会显示异常的结果和定位异常
![在这里插入图片描述](https://img-blog.csdnimg.cn/2a70d53dc75f40f5b9d8c22e6e1cf51e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



不抛出异常，欺骗老师，运行还是通过，但不会定位异常

![在这里插入图片描述](https://img-blog.csdnimg.cn/ff3118251794418a9936c33287d390f8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/b821205378444ae5a1235694810c8956.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)








# 5. NullPointerException空指针异常
**空指针异常的情况**

 - `Calling the instance method of a null object.` 调用空对象的实例方法
 - `Accessing or modifying the field of a null object.`访问或修改空对象的字段
 - `Taking the length of null as if it were an array.`将null的长度当作一个数组
 - `Accessing or modifying the slots of null as if it were an array.`访问或修改null的插槽，就好像它是一个数组一样
 - `Throwing null as if it were a Throwable value.`将null视为Throwable值

在有关对象判断类中会有抛出空指针异常的情况

![在这里插入图片描述](https://img-blog.csdnimg.cn/a7db89b1eaad4b9aabf1f07bd157db79.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 6. throws
**`throw`的作用就是抛出异常，有什么用呢？**

 - 通过捕获异常的功能，我们可以写判断或抛出异常的方法
 - 在不通过的情况下提醒程序员，这样程序员可以快速的更改代码，以防止程序在后面出现更严重的问题

![在这里插入图片描述](https://img-blog.csdnimg.cn/0552ace9e41f44f78e7b0c8b7356f988.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 7. throws和trycatch区别，用途区别

**`throw`和`try catch`的区别**

 - `throw`是用来抛出异常的，而`try  catch`是尝试运行并捕获
 - 两者结合可以达到十分好的效果

创建`MyException`类，`Alt+Insert`调出`Generate`，选择`Constructor`

![在这里插入图片描述](https://img-blog.csdnimg.cn/5ffe865b11c74d40b533ba7d043a55f1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_15,color_FFFFFF,t_70,g_se,x_16)
全选`Exception`
![在这里插入图片描述](https://img-blog.csdnimg.cn/c1251fd571304ef3b6449926856a54f8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_11,color_FFFFFF,t_70,g_se,x_16)
由此抛出编译异常
![在这里插入图片描述](https://img-blog.csdnimg.cn/ba42ece896ee47c1b38928d0245700cd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

在`StringTest`类中测试抛出异常

![在这里插入图片描述](https://img-blog.csdnimg.cn/1781f6c39c494c3f81e69ec08f17d3b1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
也可以通过调用函数的形式抛出异常

![在这里插入图片描述](https://img-blog.csdnimg.cn/a8b525df38bf4fabbbd801c368b10916.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
如果未抛出异常，则会显示编译异常，未报告的异常错误，必须对其进行捕获或声明以便抛出

![在这里插入图片描述](https://img-blog.csdnimg.cn/2d55bd9c4a114a019303065bee445ceb.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
而如果把`MyException`改成`RuntimeException`，就不会抛出编译异常，而是出现运行异常
![在这里插入图片描述](https://img-blog.csdnimg.cn/79e99f3a44bc4a87956ec9d8f440652b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 8. 手把手教你编写装X自定义异常
创建`ErrorCode`接口
![在这里插入图片描述](https://img-blog.csdnimg.cn/9e9eea93c2804adf91a9e3f6f228760e.png)
编写自定义异常代码

```java
public interface ErrorCode {
    /**
     * 获取错误码
     * @return
     */
    String getcode();


    /**
     * 获取错误信息
     * @return
     */
    String getMsg();
}
```


创建`MyCodeEnum`枚举类
![在这里插入图片描述](https://img-blog.csdnimg.cn/578d88764cd94ad39e0edf160df4f208.png)
编写代码实现接口中的所有方法

```java
public enum MyCodeEnum implements ErrorCode{
    NOT_FOUND_PAGE("404","找不到网站资源"),
    NOT_FOUND_FILE("888","找不到文件"),
    NOT_O_TEN("bad", "只能求10以内的加法")
    ;

    MyCodeEnum(String code, String msg) {
        this.code = code;
        this.msg = msg;
    }

    private final String code;
    private final String msg;

    @Override
    public String getcode() {
        return code;
    }

    @Override
    public String getMsg() {
        return msg;
    }
}
```


创建`MyException`类继承`RuntimeException`
```java
public class MyException extends RuntimeException{

    public MyException(ErrorCode errorCode) {
        super(errorCode.getMsg());
    }
}
```

在`String Test`类中抛出异常，并可枚举选择异常形式
![在这里插入图片描述](https://img-blog.csdnimg.cn/fc597348ba2d4d74af2069ecda50cbc9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/8586373b4ee14786a2e63433ba021afb.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


