@[TOC](目录)

# 1. 问题的提出

**一台计算机为何能够执行多个程序？它们是怎么执行多个程序的？**

 - 电脑可以同时做很多事情，一边聊天，一边听歌，一边上网查资料等
 - 原因是电脑有多个核心(脑子)，一个核心可以做一件事情，多个核心就可以做多件事情
 - 而多线程就是一台电脑，CPU可以同时运行两个程序(表面上)，实际上是进程切换的快，第一个进程打开，第二个进程挂起，给你一种错觉

![在这里插入图片描述](https://img-blog.csdnimg.cn/f2fce168d6d448a5a9c4c872819489bf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
例如CPU的6核12线程，就相当于有6个工人去运行进程

![在这里插入图片描述](https://img-blog.csdnimg.cn/66c51b202f52411f976174af4da1f61b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 2. 核心数、进程、线程

 - 一个核心下有多个进程，而一个进程下又会有多个线程

# 3. 进程和线程的区别以及对应应用
**进程和线程的区别**

 - 线程只是一个进程中不同执行的路径
 - 进程与进程之间不会相互影响，因为它们是占有独立内存的
 - 而线程是占用共同的内存，所以一个线程出问题，那这个进程下的线程都会出问题
 - 多进程的程序要比多线程的程序健壮，而多线程运行效率更高，但是线程不能独立执行，必须依存在应用程序中，操作系统不会把线程看作多个独立应用
 - 但对于一些要求同时进行并且又要共享某些变量的并发操作，只能用线程，不能用进程。例如很多人共同抢一双鞋，就要用到多线程


**并发与并行**

 - 并发(Concurrent)指一个CPU需要进行多个进程，这样就需要不停的切换，让进程不断的交替执行
 - 并行(Parallel)指多个CPU同时执行多个进程



# 4. 多线程程序含义、多线程的作用

创建多线程`DemoThread`类，`Alt+Insert`调出`Generate`选择`Override Methods`

![在这里插入图片描述](https://img-blog.csdnimg.cn/7b8c80dde6174833804b4d54b28320e1.png)
选择`run():void`
![在这里插入图片描述](https://img-blog.csdnimg.cn/40a180f3e5b94949b8322c07609b6a28.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_11,color_FFFFFF,t_70,g_se,x_16)
`mainThread`和`DemoThread`两个字符串交替执行

![在这里插入图片描述](https://img-blog.csdnimg.cn/b970bf2c763c456a9bfb206186bff1da.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
如果用`.run()`的话会出现问题，死循环一直在跑，用`.start()`可以多开启一个线程，然后去自动调用`.run()`，再继续进行当前线程
![在这里插入图片描述](https://img-blog.csdnimg.cn/d16ec1718ec047d4984f3be0b869dce5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

显示的结果是两个死循环的内容在交替执行，其原因就是使用了`.start()`后两个线程一直在执行

# 5. 多线程的执行过程
**多线程的执行方式**

 - 一般的程序是从`main`出发，直线向下进行，只有一条主线
 - 多线程在`main`主线程序遇到线程程序时会转到线程程序，并返回到主线程序中，这样main程序和线程程序同时执行

![在这里插入图片描述](https://img-blog.csdnimg.cn/0e08009c4e1b48c0af55f42aeb1c3bbb.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



# 6. Runnable


前面我们创建线程单继承了Thread，无法继承别的类，因为Java不支持多继承

使用`Runable`接口来创建线程，要使用其方法，必须创建`Thread`对象实现


![在这里插入图片描述](https://img-blog.csdnimg.cn/09b6b5a31ddb4f768986230f7fbc9275.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

`Ctrl + 左键`查看Thread源码
![在这里插入图片描述](https://img-blog.csdnimg.cn/e4e73fd511e64a659193982cdae45dc9.png)


源码中，`Thread`类就是实现了`Runnable`接口，而在`Thread`的构造方法中也有许多方法函数需要传递`Runnable`接口类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/98c1397ba2d9466fbceede92c8ff6080.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

而我们在主函数中实现的应该是第一种传递方式，`Thread`的构造方法还有很多方式，这些构造函数都有一个特点就是全部使用`init`这个方法对线程进行实现

**`init`源码的变量注释及源码**

 - 在原始的init中名字是不能为空的，如果名字为空会报空指针异常，但是在其他的函数中，如果程序员不给`thread.name`赋值的话也可以自动生成一些值
 - 涉及线程组相关的安全问题
 - 变量的赋值和其他函数的初始化相关

![在这里插入图片描述](https://img-blog.csdnimg.cn/78636de295854d4398bf56d85d5d0595.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/1b7647546f714cc989de39aed0a85af9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

下面`init`方法是对上面的函数的衍生，是构造方法中使用的初始方法
![在这里插入图片描述](https://img-blog.csdnimg.cn/03ebd28eab4f49d28f08ec30a850e4ab.png)




# 7. 简化操作以及线程名

`Thread`源码里面有传线程名的构造方法，要在原来线程类中自动获取我们在主线程中设置的名字，使用`Thread.currentThread().getName()`方法，`.currentThread()`是指当前线程，`.getName()`是指获取名字


![在这里插入图片描述](https://img-blog.csdnimg.cn/f256bdeda84a433d8006db58c91affa5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 8. 抢购鞋——多线程案例

两种创建线程的方式，一种使用继承，一种使用接口实现，解决了线程名的问题，接下来我们模拟一个多线程的抢鞋程序

抢鞋的逻辑代码涵盖在线程当中，假设有10双鞋，有三个人来抢，一个线程就是一个用户，所以这就有三个名称不一样的线程名

使用`Runnable`接口创建

![在这里插入图片描述](https://img-blog.csdnimg.cn/6416bceef7a14542a6d781402cb051ef.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 9. 后台、守护进程的提出
**电脑任务管理器**

 - Apps是前台进程，Background processes是后台进程也叫守护进程，这些进程在电脑开机时就被启动，这样电脑才能正常且安全的运作起来，在程序中也是同理
 - 与进程同理，前台线程为用户提供服务，也有后台线程为前台线程提供的服务进行保护或者守护

![在这里插入图片描述](https://img-blog.csdnimg.cn/99b92f490f3e44a98b9822550458747e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


**后台线程的创建过程**

1. 创建一个`DaemonThread`，实现`Runnable`接口

2. 重写`run()`方法

3. 在运行类中创建先一个`DaemonThread`，再用 `Thread` 用来实现`DaemonThread`

4. 最后调用`setDaemon(true)` 设置成后台守护线程，`.start()`开启线程
![在这里插入图片描述](https://img-blog.csdnimg.cn/9d2b5097f090448e8db8fb2950c0debf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 10. 匿名内部类创建多线程——你们老师喜欢的

将`Runnable`接口进行匿名处理

![在这里插入图片描述](https://img-blog.csdnimg.cn/45bbb0375ba04e909a1da64a55a2eeac.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 11. 发现问题，提出synchronized的概念和用途

现实情况中，抢鞋肯定是有延时操作的，如果我们用`.sleep()`设置每次抢鞋之间的间隙，会产生了一个问题，就是线程不同步导致线程不安全，两个人同时抢了第7双鞋

![在这里插入图片描述](https://img-blog.csdnimg.cn/6ab40c56ffb5433b84095d38d64e29da.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


解决这个问题要用到线程同步，及时更新数据，即创建一个`synchronized`锁对象，同步数据
![在这里插入图片描述](https://img-blog.csdnimg.cn/88f7c4b982094fa5b1b1761aba2892e4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 12. synchronized同步方法
如何理解锁呢？当用户一抢到第一双鞋时，锁住第一双鞋，其它用户就无法抢了
![在这里插入图片描述](https://img-blog.csdnimg.cn/35047b8683b246aea13cf395b28eabd5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

`synchronized`可以创建成一个同步方法，将同步代码块抽离出来
![在这里插入图片描述](https://img-blog.csdnimg.cn/8d9b4c8a9c9b4317a594edfee6373e19.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 13 Lock、ReentrantLock同步锁
**synchronized与reentrantLock区别**

 - `synchronized` 不需要用户去手动释放锁，代码执行完后系统会自动让线程释放对锁的占用
 - `reentrantLock`则需要用户去手动释放锁，如果没有手动释放锁，就可能导致死锁现象

![在这里插入图片描述](https://img-blog.csdnimg.cn/7c7663ca1f404b188a286294211c0b6c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



# 14. Unlock遗留问题，释放锁
释放`reentrantLock`锁，`try catch`要放在`if`外面，最后`finally`调用`reentrantLock.unlock()`方法

![在这里插入图片描述](https://img-blog.csdnimg.cn/83363589da5e4e4e8d0d7a97d63742d8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 15. 浅谈synchroized和Lock的区别

 - JDK1.5中，`synchroized`是重量级操作，性能低效，`Lock`性能高，更稳定
 - JDK1.6中，`synchroized`加入很多优化，更加稳定了

**锁的释放** 

 - `synchronized`以获取锁的线程执行完同步代码，如果线程执行发生异常，jvm会让线程释放锁

 - `Lock`在`finally`中必须释放锁，不然容易造成线程死锁

**死锁产生**

 - `synchronized`在发生异常时候会自动释放占有的锁，不会出现死锁
 - `Lock`发生异常时候，不会主动释放，必须手动`unlock`来释放锁，可能引起死锁的发生

 **用法** 

 - `synchronized`在需要同步的对象中加入，可以加在方法上，也可以加在特定代码块中，括号中表示需要锁的对象

 - `Lock`一般使用`ReentrantLock`类做为锁，通过`lock()`加锁和`unlock()`解锁指出，在`finally`中写`unlock()`防止死锁

# 16. Thread API说明

> 参考：**[Thread (Java Platform SE 7 ) - Oracle](https://docs.oracle.com/javase/7/docs/api/index.html?java/lang/Thread.html)**

# 17. CPU线程调度、Priority线程优先级、优先级常量、剩余小问题
**CPU线程调度**

 - 每一个线程的优先使用权都是系统随机分配的，人人平等，谁先分配到谁先用
 - 可以设置优先级赋予某一个线程拥有至高适用权，最高为10，最低为1，默认为5，Java可以抢占CPU
![在这里插入图片描述](https://img-blog.csdnimg.cn/4448790a6d5d420e892d31332048b34d.png)

线程1-10中，`main()`主线程的value =  5，创建 `MaxPriorityThread` 类和`MinPriorityThread`来查看线程执行顺序

![在这里插入图片描述](https://img-blog.csdnimg.cn/a83a49c1b8594f4ea880bae630c77c97.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
在`.start()`前面加优先级`.setPriority()`方法即可越权
![在这里插入图片描述](https://img-blog.csdnimg.cn/10bb4bde986f42329014673274a0d89b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

但有时会发现优先级没有调换过来，是操作系统的原因，程序执行太快了没有反应过来，还没调度程序就结束了
![在这里插入图片描述](https://img-blog.csdnimg.cn/c4068adf43734b008c1929eb6f1895e3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 18. join线程插队
`.join()`方法可以抢占优先级，实现插队
![在这里插入图片描述](https://img-blog.csdnimg.cn/551b60f608c248ce984ac10d61922822.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 19. sleep线程休眠
还是上一个例子，使用`.sleep()`方法休眠后，`thread_1`线程插队时，会等待1000毫秒再打印出结果
![在这里插入图片描述](https://img-blog.csdnimg.cn/02c9a8ec7af64241a6b7f0fa0afa50d6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 20. yield线程让步
`.yield()`方法可以实现线程让步，让其它线程执行，`thread_1`输出一次的时候给`thread_2`让步了，有时程序运行的太快了，以至于还没打印出让步输出，`thread_2`已经输出完毕了

![在这里插入图片描述](https://img-blog.csdnimg.cn/918e917b74694bd6bd9d5fccb463579a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



# 21. 线程状态？嗯，还是来玩一盘游戏吧！
**Java中线程的状态分为6种--以斗地主为例**

1.新建(NEW)-新建一局游戏

2.可运行(RUNNABLE)-初始状态是可运行的

3.阻塞(BLOCKED)-谁出牌谁获得一个锁，导致阻塞，出好牌则疏通阻塞

4.等待(WAITING)-不出牌的等待通知

5.计时等待(TIMED_WAITING)-出牌时，其他人计时等待超时或通知

6.终止(TERMINATED)-游戏结束


![在这里插入图片描述](https://img-blog.csdnimg.cn/28af69c4e7ca4b6ebbae1d64f7b86d22.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_15,color_FFFFFF,t_70,g_se,x_16)

>**参考： [Java线程的6种状态及切换(透彻讲解)](https://blog.csdn.net/pange1991/article/details/53860651)**

# 22. 发现实际问题，抛出线程通信的含义
**线程优先级**

 - Win10任务管理器中，线程有6个优先级设置
 - 线程的调度目的就是通知另一个线程去执行，也有其它办法去通知
![在这里插入图片描述](https://img-blog.csdnimg.cn/4d3f918988e447a4a19e9d045f1c128f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 23. 线程的通信：wait和notify
**线程通信，即等待唤醒机制**

 - 最简单的例子如`Producer`生产者与`Customer`消费者和`Condom`产品的关系
 - 当产品`Condom`产品生产出来之后，消费者购买完，需要联系`Producer`厂商继续生产
 - `.notify()` 方法用于唤醒一个在此对象监视器上等待的线程
 - 一个线程在对象监视器上等待可以调用 `.wait()` 方法

![在这里插入图片描述](https://img-blog.csdnimg.cn/f88427319ba948d3b86c35f8c99b5c97.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


![在这里插入图片描述](https://img-blog.csdnimg.cn/0d79bda1e38a4f8c83e2139f46b46da8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



# 24. notifyAll
`.notifyAll()`方法用于唤醒在该对象上等待的所有线程
# 25. 提及Process进程。点到为止，章节结束语和建议。
多线程掌握基础，当学习到框架时，需要深入并发编程

> **参考：操作进程拓展[Class ProcessBuilder](https://docs.oracle.com/javase/7/docs/api/java/lang/ProcessBuilder.html)**

