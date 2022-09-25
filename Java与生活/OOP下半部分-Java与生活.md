@[TOC](目录)
# 面向对象三大特性：封装 继承 多态
# 2-1-1 需求重定义

**我们的宠物系统要如何维护呢？**

人们养宠物会有很多的选择，除开狗以外还会有猫、老鼠、熊、猪等等等

# 2-1-2 继承
**如何将这些重复的代码进行一个归类和总结呢？**

 - 我们会有许多方法去维护这个软件，如果要把所有动物的类都写上去，你会发现写上的都是重复的代码，我们需要将重复代码进行总结，由此提出概念：继承

**什么是继承？**

 - 泛指把前人的作风、文化、知识等接受过来
 - 把重复的代码放在一块，让其他的动物接受过来，这也是一种继承


我可以创造一个类叫"动物"，这样其他的动物都可以在"动物"类中继承相同的地方，继承的关键词是 `extends`
![在这里插入图片描述](https://img-blog.csdnimg.cn/988b2c3e8b1f44f4b89f5f3cad5d6e9a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
我们把原来属于Dogs的内容转移到了`Animal`中，使用 `extends` ，最后在主函数中像之前一样`Dogs`类

并且 `Cat`在继承`Pet`以后也可以像狗一样实践，这样就使得我们的代码的复用性很强，也符合了大众化


# 2-2-2 饿狼传说之多层继承
**什么是多层继承 ？**

 - 像灰太狼家族，一层一层的继承，爷爷传承到爸爸、爸爸传承到孙子
 - 一个类不能直接继承多个类，java是单继承语言，不支持多继承
 - 不能写成 `class A extends B,C` 
 - 但可以实现继承多个类 `class A extends B，class C extends A` 这样C就同时继承了B和A两个类了

```java
public class Dogs extends Animal{
}
```

```java
public class Labrador extends Dogs {
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/8137339517e040be9728fd2c72a2697f.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 2-2-3 方法的重写
**如果要对继承中某个方法进行修改怎么办？**

 - 在类继承了另外一类，但是对一些方法需要进行修改的时候就需要用到方法的重写，比如动物的叫声不同

```java
    @Override
    public void breaking() {
//        super.breaking();
        System.out.println("喵喵");
    }
```

```java
    @Override
    public void breaking() {
//        super.breaking();
        System.out.println("汪汪");
    }
```


动物叫，这是它自己拥有的特性，是他自己写的，不是来自他爸的，他从爸爸那革新了

子类自己认为，应该打破它父亲的传统，进行革新，革新的内容就是方法体

`super` 这个函数是继承父类的所有方法，如果要改写就需要将这个注释掉
![在这里插入图片描述](https://img-blog.csdnimg.cn/45d435c0be584761a61e351f5065562a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
**重写(Override)与重载(Overload)的区别是啥？**

 - 重写(Override)是子类对父类的允许访问的方法的实现过程进行重新编写, 返回值和形参都不能改变
 - 重载(Overload)是在一个类里面，方法名字相同，而参数不同。返回类型可以相同也可以不同
> **参考：**
>  - **[Java 重写(Override)与重载(Overload)-菜鸟教程](https://www.runoob.com/java/java-override-overload.html)**

# 2-2-4 super啃老
引用父类的方法
![在这里插入图片描述](https://img-blog.csdnimg.cn/e37dd9ae609149e39fea2cbe69999385.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 2-2-5 啃老啃到彻底
**构造方法的重写**

继承无法继承父类的构造函数，所以还需要重写构造方法，这样才可以进行对象的初始化

![在这里插入图片描述](https://img-blog.csdnimg.cn/53a18ef66ed24413bd3c2434a02debdc.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/29576c51887d4efb93f7eb8b93ed12a5.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_11,color_FFFFFF,t_70,g_se,x_16)

```java
    public Animal(String name, String variety, int age, String food) {
        this.name = name;
        this.variety = variety;
        this.age = age;
        this.food = food;
    }

    public Animal() {

    }
```

```java
    public Cat(String name, String variety, int age, String food) {
        super(name, variety, age, food);
    }

    public Cat() {
    }
}
```

```java
    public Dogs(String name, String variety, int age, String food) {
        super(name, variety, age, food);
    }

    public Dogs() {
    }
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/67199bfd4be14eb0ab7533648feb9c4c.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/1673d186efa74cdab6fd9b98140e23dc.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 2-2-6 final
**遗产没人继承了，也不可能继承--final**

例如我们创建一个拉布拉多类继承`Dogs`类，并用`final`定义 

 - 用`final`定义的类不能再被继承
 - 用`fianl`定义的方法不能再被重写
 - 用`final`定义的变量是常量且不能再被修改

方法也有重写，拿狗是否能导航来举例，`Dogs`类不加`final`结果：
```java
    public boolean isGudieBlindness(){
        return false;
    }
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b2709076fa0e4a2e8dab78ab9d449cb4.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`Dogs`类加`final`结果：
```java
    public final boolean isGudieBlindness(){
        return false;
    }
```
`Labrador`类不能重写`fianl`的方法
```java
'isGudieBlindness()' cannot override 'isGudieBlindness()' in 'com.microsoft.demo.Dogs'; overridden method is final
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/949bc97ad7aa49389708d7788db6dce8.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

再例如，用`final`定义的变量是常理，而在命令规范中，常理必须大写，单词用下划线隔开
```java
    private static final String COMMUNITY_NAME ="NanG";
    public static String getCommunityName(){
        return COMMUNITY_NAME;
    }
```
快捷键：
`ctrl +shift+u`一键大写
`shift+f6`一键更改变量

# 2-2-7 提出新的问题
**那new Animal()是不是没用了？——抽象概念的引出**

 - 在这个系统中`Animal`类是一个没有抽象的类，就像你养一只动物肯定是具体猫或狗等，因此，`Animal`这个类是不会能被 `new`的，这样就涉及了抽象类的概念
 - `Animal`类是用来继承的，没人会用`Animal`，我们创建对象的时候只会用到猫猫狗狗类
 - 如果子类继承了父类，但是并未给子类写行为的具体内容，这样子类调用行为的时候出现的是父亲的行为，也就是说，如果我们定义仓鼠叫，输出的是"动物叫"，而不是仓鼠的具体叫声

万一我们创建的仓鼠类，没有定义叫声怎么办？抽象类来解决这个问题
# 2-3-1 抽象与具体——抽象类的衍生
**你不能养一个抽象"动物"，而是具体养了"什么"**

 - `Animal`本质来说是没有人用的，它是一个抽象的，它抽取了这些猫狗的共性，作为使用
 - 抽象的反义词是具体，抽象的目的是为了概括(解释)这些具体事物
 - 加入抽象类的关键词是 `abstract` ，抽象类是不能再被 `new` 的类，但是它可以被其他的类继承

# 2-3-2 抽象方法和抽象类的使用
**如何理解抽象方法的作用呢？**

 - 你会发现，想像一下，动物的叫声太多了，我们可以统一叫这个行为，但是我们不能统一他们的叫的方式一样（叫声一样），所以我们要在具体类中具体他们的叫声
 - 同时使用抽象方法可以起到提示作用，因为抽象方法必须重写，如果忘记重写就会有报错
 - `Animal`类中抽象方法是不能有实际意义的

![在这里插入图片描述](https://img-blog.csdnimg.cn/d2d4a82a763e4583b71e38bf0ff74221.png)
 应该这么写
```java
    public abstract void breaking();
```

继承抽象类(`Animal`类)的子类(`Cat`类)必须重写父类的抽象方法，且抽象方法必须在抽象类中
![在这里插入图片描述](https://img-blog.csdnimg.cn/210aeea938004553981feea97ab1d7a8.png)
同时子类也无法`super`父类了，因为父类没有这个方法
![在这里插入图片描述](https://img-blog.csdnimg.cn/0a4ed562dce743f2b7498f9811257454.png)




# 2-3-3 接口
**如果方法全是抽象的怎么办？**

 - 在抽象类中有抽象方法，如果把抽象类里的方法全部变成抽象方法，可以用接口来替代这个抽象类

`New Java Class`	选择`Interface` 
![在这里插入图片描述](https://img-blog.csdnimg.cn/85ed147eca9044c285ce8ae237bdded3.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_16,color_FFFFFF,t_70,g_se,x_16)
接口里面所有方法都是抽象的，实现接口的类，会把接口中定义的方法全部重写
![在这里插入图片描述](https://img-blog.csdnimg.cn/bd32224d40ca457bbadabe06dfd72917.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/d647ceedf5db417594ddf2cf9224aab7.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_13,color_FFFFFF,t_70,g_se,x_16)

```java
public interface Human {
    public void eat();

    public void run();

}
```

```java
public class Chinese implements Human{
    @Override
    public void eat() {
        System.out.println("吃中餐");
    }

    @Override
    public void run() {
        System.out.println("小跑");
    }
}
```

```java
public class Westerner implements Human{
    @Override
    public void eat() {
        System.out.println("吃西餐");
    }

    @Override
    public void run() {
        System.out.println("大步跑");
    }
}
```

```java
public class Application {
    public static void main(String[] args) {
        Chinese chinese = new Chinese();
        chinese.eat();
        chinese.run();

        Westerner westerner = new Westerner();
        westerner.eat();
        westerner.run();
    }
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/d5e68ca71043428991539b9074609901.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 2-3-4 class和interface的区别哲学气息
**接口和抽象类本质上有什么区别？**

 - 抽象类是针对具体的事物进行抽象
 - 接口是针对动作、行为进行抽象，且接口中避免出现名词

# 2-4.1 多态——花木兰替父从军


**多态是什么？**

 - 多态是同一个行为具有多个不同表现形式或形态的能力
 - 多态就是同一个接口，使用不同的实例而执行不同操作

**多态存在的三个必要条件**

 - 继承
 - 重写
 - 父类引用指向子类对象：`Parent p = new Child();`

**向上转型**

 - 子类引用的对象转换为父类
 - 此处父类对象可以是接口
 - 花木兰替父从军就是向上转型，隐藏子类

```java
Animal a = new Cat();
```

**向下转型**

 - 把父类对象转为子类对象
 - 前提是父类对象指向的是子类对象，即在向下转型之前，它得先向上转型
 - 向下转型只能转型为本类对象（猫是不能变成狗的）
 - 做回自己就是向下转型，开始变换

```java
Cat c = ((Cat) a);
```

> **参考：**
>  - **[Java 中的多态-菜鸟教程](https://www.runoob.com/w3cnote/java-polymorphism.html)**

# 2-4-2 匿名内部类
**为什么叫匿名内部类？**

 - 匿名内部类也就是没有名字的内部类
 - 如果某个局部类你只需要用一次，那么你就可以使用匿名内部类
 - 使用匿名内部类必须继承一个父类或实现一个接口

抽象类是不能被`new`的，但是接口可以，`new`接口时会自动创建重写

```java
public class Application {
    public static void main(String[] args) {
     Human xiaoming = new Human() {
         @Override
         public void eat() {
             System.out.println("吃中国菜");
         }

         @Override
         public void run() {

         }
     };
     xiaoming.eat();
    }
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/8ab64a0971be4676be343faaf22cc2c3.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_13,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/c578bbcb25c44d7482b6b0318ace9864.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 3-1-1 权限修饰符

> **参考：**
>  - **[Java 修饰符-菜鸟教程](https://www.runoob.com/java/java-modifier-types.html)**

# 3-1-2 Object
`Java Object` 类是所有类的父类， Java 的所有类都继承了 `Object`，子类可以使用 `Object` 的所有方法

我们创建一个类时，如果没有明确继承一个父类，那么它就会自动继承 `Object`，成为 `Object` 的子类


> **参考：**
>  - **[Java Object 类-菜鸟教程](https://www.runoob.com/java/java-object-class.html)**


