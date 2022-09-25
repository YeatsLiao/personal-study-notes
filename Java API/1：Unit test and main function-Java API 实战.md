@[TOC](目录)


# 1. 抛出企业问题，脱离main测试，模块化编程

**main方法是什么？**

 - `main`方法就是进入程序的一扇门，而这个门只负责开和关，打开门可以实现某些功能，但这些功能只由门里面的东西来决定，而不是门
 - `main`是一个程序的入口点，而不应该是处理逻辑或者功能模块的点，`main`方法中的语句不应该有逻辑性的语句，而且代码应该是非常之少的，更复杂的东西不应该出现在`main`里，应该抽离`main`



```java
	//以往的方式
public static void main(String[] args) {

    //2.本地测试
    
    //3.调用函数
    
    //4.看输出，查看结果是否符合预期

    //5.预期结果和测试结果是通过人工计算的
    
    //1.编写功能函数（方法）
    }
```




# 2. Junit单元测试的含义和用途
**在项目中也只有一个`main`函数，但是一个项目是由多人完成的，我们不能总是合并全部的工作测试，然后再修改，这个问题如何解决呢？**

 - Junit单元测试，即测试框架
 - “单元测试”很容易想到小学的英语单词单元听写，单元就是将一个大的块头分小，测试看是否与预期相同。小学一本英语教材有100个单词，分成五个单元去背，然后老师在一定的时间内听写这个单元的单词，查看学生掌握程度，就是单元测试
 - 在面向对象的过程中也是一样，将一个程序划分成单个类和单个方法，需要对这些方法进行测试看是否达到预期

# 3. 怎么获取各种Jar包？Maven Repository 获取各类各个版本的jar，这就是仓库。脱离老师发送给你的jar。



> **Junit的Java包下载详见：[maven repository-JUnit](https://mvnrepository.com/artifact/junit/junit)**


![在这里插入图片描述](https://img-blog.csdnimg.cn/4638752ffed44d51806ca606ebf76519.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 4. 使用Junit

**1.导入jar包**

在`Dome`中`New`一个`Directory`，命名为`lib`

![在这里插入图片描述](https://img-blog.csdnimg.cn/47caaaa6c2544c66a43a7517dd9744a9.png)

将桌面上的`jar`包直接拖拽到`lib`中
![在这里插入图片描述](https://img-blog.csdnimg.cn/70dc38ab0b2a4273a72b4b2bebf31e16.png)
右键单击`jar`包`Add as library ...`
![在这里插入图片描述](https://img-blog.csdnimg.cn/c82c8ac0a46449ab82b692a845c2c40f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_11,color_FFFFFF,t_70,g_se,x_16)


**2.Junit的使用**

先创建一个类专门用来对另外一个类做测试
![在这里插入图片描述](https://img-blog.csdnimg.cn/61161cd7f61b47c686ba071ded8b8483.png)

在非测试类中编写方法， 在编写方法体时要`static`和`return`


```java
   package com.study.shea;
   
   public class Calc {
      public static int sum (int numberA, int numberB){
          return numberA + numberB;
      }
   }
 
```


使用注释`@Test`调用Junit


```java
   package com.study.shea;
  
   import org.junit.Test;
   
   public class CalcTest {
   
       @Test//使用这条注释来调用函数
       public void sum(){
          int sum = Calc.sum(1,2);
          System.out.println("sum = " + sum);
       }
   }
```

   最后的预期结果会显示在原来的调试框中
![在这里插入图片描述](https://img-blog.csdnimg.cn/e77dff57a7b64029bf8fab769c4ca767.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


**遗留问题：测试的结果还是人工计算，并不是计算机帮忙完成的**
# 5. Assert断言

在上面的操作中我们已经脱离了`main`方法的测试，但是还是没有脱离`print`打印的测试，这时就要用到Junit的断言测试方法`Assert.assertEquals()`，用来比较预期值与结果的差别

在这个测试过程中我们没有自己进行计算，没有使用`main`方法运行，也没有使用`print`进行打印，最后的结果就是测试的通过
![在这里插入图片描述](https://img-blog.csdnimg.cn/4703d783f0b1479688ea709b468717ec.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


![在这里插入图片描述](https://img-blog.csdnimg.cn/a523e3eb60ce4fb6bd7afe6cc346761d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

但是这个测试还是十分有限的，如果只有`1+2`可以通过，那这个函数还是有问题的


# 6. 更进一步，合理编写随机测试，完善代码案例

进行随机测试，给的数是随机的，并不由人工干预，这样可以使得测试会更有说服力
![在这里插入图片描述](https://img-blog.csdnimg.cn/273b8db853ec454ca92112d351bc7017.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

同时，各测试之间互相并不干扰，`sub`和`sum`测试可以同时进行，当有一个测试出错时，并不会影响到另外一个函数的测试
![在这里插入图片描述](https://img-blog.csdnimg.cn/3d749f0604af4427a152e6b0c6959ce2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/aad24782770b4281b957da9a83662f12.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)





