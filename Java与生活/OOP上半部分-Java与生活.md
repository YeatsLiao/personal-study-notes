@[TOC](目录)

# 1-1-1 问题产生和引导
假设有一个养狗系统
面向过程     | 面向对象
-------- | ------
流水线  | 模块化
一件事"该怎么做"  | 一件事"该让谁来做"
狗饿了，狗吃了食物  | 属性:狗、食物、饿；动作:狗吃食物
强调的是“吃”，“狗”只是一个参数  | 强调的是“狗”，“吃”只是一个动作

  一件事“该让谁来做”，那个“谁”就是对象，他要怎么做是他自己的事，最后一群对象合力能把事做好了

# 1-1-2 烦人
**首先我们要明白什么是对象？**

 - 根据词典指行动或思考时作为目标的事物
 - 简单来说就是你现在所干的事情的目标是为了啥

# 1-1-3 变换思维
**思考什么是过程？**

 - 第一步怎么做，第二步怎么做，接着怎么做……最后怎么做(return 0)
 - 走一步看一步，目标不明确，我们不可能把所有过程写一遍，不适用于大众


**面向过程编程：（POP：Procedure Oriented Programming）**
 - 分析解决问题所需要的步骤，然后用函数把这些一步步实现，使用的时候按顺序依次调用
 - 代码线性，严格按着顺序，侧重解决步骤，着眼局部或者具体

**面向对象编程：（OOP：Object Oriented Programming）**

 - 该程序，要大众化

 - 明确目标吗，对象就是目标，目标就是对象

 - 不强调过程

# 1-1-4 规划明确目标站在更高层次思考问题
**明确目标**
- 计划、规划 设计它
- 当你执行完计划时候，达到目标
- OOP:站在更高的层次看待事物

# 1-1-5 上代码，设计体验面向对象编程，实例和对象


**首先我们要明白什么是对象(实例)？**

 - 根据词典指行动或思考时作为目标的事物，简单来说就是你现在所干的事情的目标
 - 显示生活的一个东西，对抽象的东西进行表示出来的产物，是一个活生生存在的事物，它是唯一的


现在要制作一个What‘s Animal 的软件，那这里面所有的对象就是大家会养的宠物，比如猫猫狗狗等

这个时候就比如设置一个狗`Dogs`的类(class)，这个class就是一个狗的基础模型

```java
public class Dogs {
    public String name;
    public String variety;
    public int age;
    public String food;
    public void eat(){
        System.out.println("eat food");
    }
    public void sleep(){
        System.out.println("狗睡觉");
    }
}
```




`myDog` 就是一个对象(实例)了，当我们看到 `myDog` 的时候只会觉得这是一只狗，但是我们不能知道
它具体的样子

我们就要继续对这个狗进行描述操作，然后它就会浮现出一个具体的样子

然后在另外一个`main()`方法里面`new`一个`Dogs`对象(实例)

```java
public class main {
    public static void main(String[] args) {
        Dogs myDog = new Dogs();
        myDog.name = "Tom";
        myDog.age = 2;
        myDog.variety = "哈士奇";
        myDog.sleep();
    }
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f3679b484f52493eb2d01eacdc8a7f05.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_17,color_FFFFFF,t_70,g_se,x_16)

# 1-1-6 去你md成员变量行为类和this

**在了解什么是属性的时候，我们先思考什么是类(class)？**

 - 我比较倾向把它理解成**分类**的类，回到What‘s Animal 这个软件当中
 - 软件中有很多的宠物，很多类型的宠物，有猫、狗、猪等等，那我们最好的分类方式就是对不同的动物分类

这样我们就去创建一个`Dogs`类

```java
public class Dogs {

}
```

**什么是属性(共性、特性)？**

 - 属性是事物的性质与事物之间关系的统称。
 - 事物的性质——事物的形状、颜色、气味、善恶、优劣、用途等
 - 事物的关系——大于、小于、压迫、反抗、朋友、热爱、同盟、矛盾等
 - 任何属性都是属于某种对象的
 
类当中的变量和方法都称为属性(共性、特性)或者成员变量，它们组成和构成了类，所以我们这么命令，它们是类的重要组成部分

例如同一类动物的特征有身高、体重、毛皮颜色等，会作出吃饭、睡觉等行为，这些特征和行为就是属性

```java
public class Dogs {
    public String name;
    public String variety;
    public int age;
    public String food;
}
```
这些方法(函数)在类中叫行为
```java
    public void eat(){
        System.out.println("eat food");
    }
```

**this 是啥？**

 - 当我们在做英语阅读理解的时候，会看到一种题目叫做文中的xx段xx行的this代表指代的是前文的啥？
 - 那这个问题就和这个阅读理解一样，计算机在做英语的阅读理解啦，计算机一般比我们聪明些总是能正确的回答
 - this的中文意思是“这个”，当我创建好一个对象，并且将它实例化以后，我使用这个对象进行一个操作`myDog.sleep()`：

![在这里插入图片描述](https://img-blog.csdnimg.cn/56ee46ac239e4ea391c02ba479fef1e6.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
这个时候回到类里 `sleep()` 这个方法里，里面有一个`this`，那很显然这个 `this` 调用的就是 `myDog` ，那 `myDog.name` 不就是Tom嘛

要是我的英语阅读理解题有这么简单就好了



# 1-1-7 注销账户和null空指针异常
使用软件要进行账户的注册，我们姑且把账户注册等同于制造一个新的对象

填写完注册信息之后，我们就变成了一个实例，假如我们想注销，这个过程就会把我们的信息从软件上抹去

这个时候我们对代码进行这样的操作
```java
public class main {
    public static void main(String[] args) {
        Dogs zhangDog = new Dogs();
        zhangDog.name = "Tom";
        zhangDog.age = 2;
        zhangDog.variety = "哈士奇";
        //张大爷想注销账户
        zhangDog = null;
        System.out.println("zhangDog.name = " + zhangDog.name);
    }
}
```

注销之后如果你就找不到张大爷了！空指针异常啦
![在这里插入图片描述](https://img-blog.csdnimg.cn/d4695edc27d545be838f1b045d142565.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`zhangDog`相当于一个指针，在内存里指向对象，注销后，指针就指向了一块空的区域，接下来讲说明如果解决这个问题

# 1-2-1 OOP封装
**为什么要进行封装？**

 - 如果狗的年龄被改成-30怎么办？这不是出错了吗，或者如果没封装起来，我岂不是可以修改支付宝余额为9999999
 - 在上数字电路实验课的时候，会发现它比模拟电路的实验更加简单，而数字电路中，时序逻辑电路，又比门电路简单，这是一步一步的集成所达到的效果，会让东西用起来更简单，但是内部复杂的模拟电路和门电路就不需要去理会
 - OOP的封装也是如此，我们在一些类里已经写好了很多功能，用户在使用的过程中，不需要理会在类里面写了什么，只要根据自己想实现的功能使用就可以了

**那OOP是如何封装的呢？**

 - 首先我们要明白一个道理就是，我们的集成电路里面的模拟电路、门电路是看不到的，也取不出来，它的原理对设计它的公司来说是私密的，那我们在封装的过程中也要将变量变成私密的

但这个时候`main()`就会出现错误提示
![在这里插入图片描述](https://img-blog.csdnimg.cn/83ac94c95bc94c31aad44d054f75e582.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
那我们就无法操作这个类的属性了，就像你集成完电路后没有留外接口，这个时候我们就要请上 `getter` `setter` 函数了

![在这里插入图片描述](https://img-blog.csdnimg.cn/086d9edacd7a48559fd9283bf8c39790.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


把成员变量做的安全，使用`private`代替`public`(公共的，用户可以修改此属性)成员变量的特性，另外提供`getter and setter` ，这种方式叫做oop封装

`getter` `setter` 可以看作是一个按钮，这就是封装，而在按钮设置的过程中，你可以对按钮编程，让它符合条件以后才可以被启动



# 1-2-2 jar导入和lombok
下载`lombok`插件
![在这里插入图片描述](https://img-blog.csdnimg.cn/1c3c8742f5d24b09aef8e8d7933cd2a1.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_10,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/d47fd431866646d6a74269cc1c14a176.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

>  **lombok插件下载导致idea出现字体bug，详见 idea_bugs文件夹下 “0-0-0 字体bug"视频**
> 

> **lombok的Java包下载详见：[maven repository-Project Lombok](https://mvnrepository.com/artifact/org.projectlombok/lombok/1.18.12)**

![在这里插入图片描述](https://img-blog.csdnimg.cn/9f20b9a83cfd4556bd417257e948cf0e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/46739dd301a043a4bbbe721470d705cf.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
将下载好的`jar`文件拖入`jar`文件夹下
![在这里插入图片描述](https://img-blog.csdnimg.cn/ed232111dad54cc388f3bdd67f2a1eec.png)
右击选择`Add as Library`
![在这里插入图片描述](https://img-blog.csdnimg.cn/ade3c9987f6141cca24f6e223d63e6bc.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_15,color_FFFFFF,t_70,g_se,x_16)
选择`Projcet Library`
![在这里插入图片描述](https://img-blog.csdnimg.cn/7db1d937370d4fc5816281aa3f4ceaf1.png)
此时在类中输入注释，并导入包


```java
@Getter
@Setter
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/73937e7f6945453780ec8a1c4d06afde.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/38aafad055834834b22d375093748eda.png)

还需要在设置`Annotation Processors`中将`Enable annotation processing`勾选上
![在这里插入图片描述](https://img-blog.csdnimg.cn/2fdf7dc2f81a4179b02cbcf036c22556.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
重建项目
![在这里插入图片描述](https://img-blog.csdnimg.cn/b6d6f964a9324ddbaf81bd763032584b.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
完成
![在这里插入图片描述](https://img-blog.csdnimg.cn/7ff4dd0506114a02b289ab909f013f1e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
这样就不用写`getter` `setter`了，但如果有特殊的方法则需要单独写，即方法的重写
# 1-2-3 toString()

`toString()` 这个方法可以输出相应的对象的函数，`alt + insert`一键创建`getter` `setter`函数
![在这里插入图片描述](https://img-blog.csdnimg.cn/f9a3f537410e4cbaa68e37955b48f426.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/b9778cdf0af2403a8760390976efd8cb.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_13,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/088a5bad536648c09ba4b1e4c1dc31fc.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_17,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/63f5bc638e034195acfd19478881c19e.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
当然也可以利用jar包，在类前加注解

```java
import lombok.Getter;
import lombok.Setter;
import lombok.ToString;

@Getter
@Setter
@ToString
```


`@Date`相当于包含以下三种
![在这里插入图片描述](https://img-blog.csdnimg.cn/572f5626f03f432985e1193521490114.png)

# 1-2-4 构造方法
**回忆一下数组是怎么写的?**

 - 两种不一样的定义和给数组赋值的方式，创建对象的方式和第二种先定义再赋值的方式是一样的

```java
 //1.初始化 定义+赋值
int[] arrDogs = {1, 2, 3, 4};
 
//2.先定义 后赋值
int [] arr = new int[4];
arr[0] = 1;
```


**我们如何让对象也可以初始化呢？**

这就需要构造方法 `alt+insert`
 - 构造方法不要有类型，方法名和类名一样
 - 在一般情况下要加一个空参构造方法

![在这里插入图片描述](https://img-blog.csdnimg.cn/4add459c1593485296a81b27e4d42679.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/6f1434ce54934050a8ef75db25d274f4.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_11,color_FFFFFF,t_70,g_se,x_16)
```java
    public Dogs(String name, String variety, int age, String food) {
        this.name = name;
        this.variety = variety;
        this.age = age;
        this.food = food;
    }

    public Dogs() {

    }
```

然后就可以实现对象的初始化

```java
public static void main(String[] args) {
        Dogs zhangDog = new Dogs("Tom", "哈士奇", 2,null);
    }
```




# 1-2-5 构造方法的重载与再探this
构造方法也是可以重载的
![在这里插入图片描述](https://img-blog.csdnimg.cn/35bce66a285c42369036b59deb1c324d.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 1-2-6 垃圾回收
**回到1-1-7，找不到张大爷了，空指针异常怎么办？**

 - java一般是不需要你手动回收的，如果一定要自己手动来垃圾回收，可以使用`System.gc()` 这个方法

![在这里插入图片描述](https://img-blog.csdnimg.cn/49c771ab7a1943229d1e4f462f4f6cce.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
这样就不会出现空指针异常了


# 1-2-7 静态变量和静态方法
静态变量
```java
    public static String plot ="NanG";
```
静态方法

```java
    public static void goplot(){
        System.out.println("所有狗都进了小区");
    }
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/cb69f85ffbdf45068b3d04c7638d0fee.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 1-2-8 private static
**万一静态变量被改了怎么办？**

咱们小区名被黑了
![在这里插入图片描述](https://img-blog.csdnimg.cn/367638aaf1914b789b0ccec210916032.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
这就需要用到`private static`
```java
    private static String plot ="NanG";
    public static String getPlotInstance(){
        return plot;
    }
```

```java
        System.out.println("Dogs.getPlotInstance() = " + Dogs.getPlotInstance());
```
这样定义变量和方法只能在有类名来使用，可以看作是所有类都必须做的事情，而对象无法使用，对象无权选择或者不选择。
![在这里插入图片描述](https://img-blog.csdnimg.cn/863717c0d4b9490796063bdcdc2ebd77.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 1-2-9 static单例模式
**单例模式怎么来的？**

 - `private
   static`定义变量和方法只能在有类名来使用，可以看作是所有类都必须做的事情，而对象无法使用，对象无权选择或者不选择，这里就衍生出了一种设计模式：单例模式

**单例模式怎么用？**

 - 单例模式的存在是为了保证一个类仅有一个实例，无法克隆，并提供一个访问它的全局访问点

下面就拿课程Frank讲的例子来理解一下

```java
public class Earth {
    //new 一个新的地球，只有Earth类内可以调用
    private static Earth earthInstance = new Earth();

    //外部无法new新的Earth
    private Earth(){

    }
    //Earth在外部得到Earth
    public static Earth getEarthInstance(){
        return earthInstance;
    }
    
   public void showMessage(){
      System.out.println("Hello Earth!");
   }
}
```

```java
public class main {
   public static void main(String[] args) {
 
      //不合法的构造函数
      //编译时错误：构造函数 Earth() 是不可见的
      //Earth object = new Earth();
 
      //获取唯一可用的对象
      Earth object = Earth.getEarthInstance();
 
      //显示消息
      object.showMessage();
   }
}
```

```java
"Hello Earth!"
```
> **参考：**
>  - **[单例模式-菜鸟教程](https://www.runoob.com/design-pattern/singleton-pattern.html)**
# 1-2-10 内部类扯淡系列
**内部类是啥？**

 - 类里面再来一个类
 - 静态内部类只能用静态变量
 - 方法内部类，只能在方法里面用
 - 用的比较少，十分难维护，可以自己去了解

# 1-2-11 OOP上半部分结束

