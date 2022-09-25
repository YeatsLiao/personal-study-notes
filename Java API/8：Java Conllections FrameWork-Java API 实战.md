@[TOC](目录)
# 1. 原生数组带来的问题，抛出问题

 - 原生数组容易造成超出边界，如果非要使用传统的数组，增删改查，就要用到数据结构，非常复杂
 - CRUD是指在做计算处理时的增加(Create)、读取查询(Retrieve)、更新(Update)和删除(Delete)几个单词的首字母简写

由此引出**Java Conllections FrameWork**即Java集合框架，也可称为函数库
![在这里插入图片描述](https://img-blog.csdnimg.cn/ee74861c44ea41f6b1b99c9026a6590d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 2. Conllections家族

 - Java集合框架是一个包含一系列实作可重复使用集合的数据结构的类别和界面集合
 - Java集合大致可以分为两大体系，一个是`Collection`，另一个是`Map`

> 这里是引用java.util.Collection下的接口和继承类关系简易结构图：![在这里插入图片描述](https://img-blog.csdnimg.cn/930ceeb2170340beb379081d0c1911af.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

> java.util.Map下的接口和继承类关系简易结构图：
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/6998f984734d481498ff089fc4273090.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



# 3. 黑帮的帮规

 - `lterables`集合层次结构中的根接口，可以理解成帮派老大
 - 当我们要帮派帮忙时，一般请它下面的小弟来办事，所以用的时候找类来实现
 - 所有类和接口都自身相关的规定，也必须遵守总集合的规定

![在这里插入图片描述](https://img-blog.csdnimg.cn/02f5d6d1258d46b583b5d1a074caca01.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)





# 4. ArrayList第一讲
`ArrayList` 类是一个可以动态修改的数组，与普通数组的区别就是它是没有固定大小的限制，我们可以添加或删除元素。

`ArrayList` 继承了 `AbstractList` ，并实现了 `List` 接口可以自动扩容

![ ](https://img-blog.csdnimg.cn/1c0dba02209c4db2bffbc4e2e92c5eed.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_14,color_FFFFFF,t_70,g_se,x_16)
泛型限定是指将类型做限定，可设置成只能存放`String`类型
![在这里插入图片描述](https://img-blog.csdnimg.cn/f5a096714afa4b29a2178dc1c7055cc1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_17,color_FFFFFF,t_70,g_se,x_16)



如果要进行CRUD，可以创建一个`Student`类
![在这里插入图片描述](https://img-blog.csdnimg.cn/4e58dec7b7b14fcfbc9179b69421f251.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_19,color_FFFFFF,t_70,g_se,x_16)

正常来说`Student`并不是以数组的形式输出的，而是`toSring`，如果要再添加一个对象扩容的话，又要`getter` `setter`一遍
![在这里插入图片描述](https://img-blog.csdnimg.cn/288335c5c47c4f6fa7805b59624ad4f4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_17,color_FFFFFF,t_70,g_se,x_16)
如果换成集合形式输出， 效果会大不同

![在这里插入图片描述](https://img-blog.csdnimg.cn/f0f133d836854a5fbbcebb0319dade94.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_18,color_FFFFFF,t_70,g_se,x_16)
这下扩容就方便多了，只需`.add()`即可，也不用担心数组下标，不用像传统输出写一个for循环了
![在这里插入图片描述](https://img-blog.csdnimg.cn/6cdc2827d4f74532a691fd83ebe3938a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 5. ArrayList第二讲

`.add()`方法可以添加元素和替换元素
![在这里插入图片描述](https://img-blog.csdnimg.cn/3fac1d15628640d39a53ec52d75c07c4.png)
`.add(0, 4)`表示在第0个下标处插入元素4
![在这里插入图片描述](https://img-blog.csdnimg.cn/b84f57d735214350a7b4ec4866a3b407.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

`.addAll()`表示合并元素，讲`arrayList_2`合并到`arrayList_1`之后
![在这里插入图片描述](https://img-blog.csdnimg.cn/8d8da891d2d94e5bafee15cd5feea561.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
查看源代码中，集合是先转换为数组，再拷贝到一份新数组返回
![在这里插入图片描述](https://img-blog.csdnimg.cn/ff6e2bac10534e66971f917d9c471e0e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.toarray()`方法表示返回集合的数组形式
![在这里插入图片描述](https://img-blog.csdnimg.cn/27c00598508842688c25b6c4d869a47d.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/fa7ddcceda994b9694dd66082a307cb0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


`.clear()`方法表示清楚数据
![在这里插入图片描述](https://img-blog.csdnimg.cn/e899244fd7d149fb96be05c67ca548ec.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.contaions()`方法用于判断字符串中是否包含指定的字符或字符串
![在这里插入图片描述](https://img-blog.csdnimg.cn/55546872cd7843df8d66fab9d2e1edb1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.get()`方法获得集合里的元素，for循环遍历具有操作性，集合的长度要用`.size()`，数组的长度用`.length()`

![在这里插入图片描述](https://img-blog.csdnimg.cn/23826d9b900d45f6b655154864a6181a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.get()`的源代码中，是先检查指是否存在，在返回元素值
![在这里插入图片描述](https://img-blog.csdnimg.cn/ac023150333c425aa54e70d4577f27a2.png)
如何对集合中每个元素操作呢？增强for循环 `for each` ,可以实现对每个元素值都加1
![在这里插入图片描述](https://img-blog.csdnimg.cn/45661679c2b74d0484276c5b53d4645e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 6. ArrayList第三讲
索引(下标)是从0开始的
`.indexOf()`方法用于查找元素首个下标
`.lastIndexOf()`方法用于查找元素最后一个下标
![在这里插入图片描述](https://img-blog.csdnimg.cn/7ce17cc9f36f4035ade628554dc8404e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

`.isEmpty()`方法用于检查集合是否为空
![在这里插入图片描述](https://img-blog.csdnimg.cn/304107200ff546b5abe05c9f05b6f7ce.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.remove()`方法用于删除元素，默认根据下标删除，可以根据`object`和`index`删除

![在这里插入图片描述](https://img-blog.csdnimg.cn/eb24086375ee471a82c8763cf60f1fbf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

`.removeAll()`方法用于移除所有元素
![在这里插入图片描述](https://img-blog.csdnimg.cn/06b6a12670454024ad18ab14748889e3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.replaceAll()`方法用于替换所有元素
`.toLowerCase()`用于转换成小写
`.toUpperCase()`用于转换成大写
![在这里插入图片描述](https://img-blog.csdnimg.cn/d6181eaeb4e94231be4126010b84b0e7.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.retainAll()`方法用于取交集
![在这里插入图片描述](https://img-blog.csdnimg.cn/61dd18bf50084bb787ee4a0725db3f70.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.set()`方法用于给指定的下标元素设置值
![在这里插入图片描述](https://img-blog.csdnimg.cn/1195a37c0b154b8e900106f06b05ecab.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.sort()`方法用于排序，默认从小到大

![在这里插入图片描述](https://img-blog.csdnimg.cn/0f2c4c5930dd407e81c108df03005bd4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

`.reverse()`方法用于置反集合
![在这里插入图片描述](https://img-blog.csdnimg.cn/0a0f95177b55493ebf8e5314d929834f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`.subList()`方法用于切割容器，需要注意截止于前一个元素
![在这里插入图片描述](https://img-blog.csdnimg.cn/e096861d9ca4474e829cc1f7b21d10dd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 7. Linked链表

 - `ArrayList`数组集合，增删慢，查询快
 - `LinkedList`链表集合，增删快，查询慢

# 8. LinkedList一带而过

 - 链表是数据结构，是一种线性表，但是并不会按线性的顺序存储数据，而是在每一个节点里存到下一个节点的地址
 - 链表可分为单向链表和双向链表
 - Java `LinkedList`类似于 `ArrayList`，是一种常用的数据容器

![在这里插入图片描述](https://img-blog.csdnimg.cn/66ea226c54fc4649b80db47369d9bf18.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 9. 提醒

 - 多看JDK文档，多练习，把基础打好

# 10. iterator 迭代器初试

 - 迭代是重复反馈过程的活动，其目的通常是为了接近并到达所需目标或结果
 - 每一次对过程的重复被称为一次“迭代”，而每一次迭代的结果会被用来作为下一次迭代的初始值

迭代器`Iterator`，不管用于`ArrayList`还是`LinkedList`都可以迭代输出
![在这里插入图片描述](https://img-blog.csdnimg.cn/be908715f9da40019cd7aada825c2558.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/1957861d44cf42d5b202b83f03e60473.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
迭代器类似用链表的形式去迭代，也可以指定泛型

![在这里插入图片描述](https://img-blog.csdnimg.cn/6c284c8cce96481f940ae3e706f29cfd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# 11. fori、增强for、迭代器的区别、注意事项和分别用途

 - `fori`适合数据的读取与修改
 - `for each`适合数据的读取
 - `Iterator`不要使用嵌套，适合数据的读取与修改

`for each`绝对不能与`.remove()`方法一起使用，危险会导致所有数据删除
![在这里插入图片描述](https://img-blog.csdnimg.cn/84b3489ed872491a9d05b2cb859feea1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_19,color_FFFFFF,t_70,g_se,x_16)
`for each`已经是一个小型的迭代器了，如果一定要修改集合的话可以使用迭代器，但不建议在`for each`中使用对象引用去修改元素

![在这里插入图片描述](https://img-blog.csdnimg.cn/7790f7c19ec7465ba222741568580be2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_19,color_FFFFFF,t_70,g_se,x_16)


# 12. 谈谈三者性能


**比较时间复杂度，foreach和迭代器谁更快呢？**

 - 如果是 `ArrayList` ，用三种方式遍历的速度是`for`>`Iterator`>`foreach`，速度级别基本一致，一般都会用`for`或者`for each`，因为`Iterator`写法相对复杂一些
 - 如果是 `LinkedList`，则三种方式遍历的差距很大了,数据量大时越明显，`Iterator`>`foreach`>>>`for`，推荐使用`foreach`或者`Iterator`

> **参考：[List遍历：for，foreach Iterator 速度比较](https://blog.csdn.net/qq_31459039/article/details/79411998)**

# 13. Set和HashSet

 - `HashSet` 基于 `HashMap` 来实现的，是一个不允许有重复元素的集合，允许有 null 值，是无序的，即不会记录插入的顺序
 - `HashSet` 不是线程安全的， 如果多个线程尝试同时修改 `HashSet`，则最终结果是不确定的，必须在多线程访问时显式同步对`HashSet` 的并发访问

`HashSet` 实现了 `Set` 接口

> ![这里是引用](https://img-blog.csdnimg.cn/da34060eac234ed591e7a625f8ff8ff1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

使用`Hash`函数实现`HashSet`，元素无序，且不重复

![在这里插入图片描述](https://img-blog.csdnimg.cn/ad9436c538e140aab5bb7d4b20fe70ef.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



> **参考：[关于Java的Hash算法的深入理解](https://blog.csdn.net/sinat_31011315/article/details/78699655)**

# 14. LinkedHashSet
如果要创建有序集合呢？`LinkedHashSet`便是有序的
 
![在这里插入图片描述](https://img-blog.csdnimg.cn/94b9efe7dee542989cbe32e6008b0629.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 15. Map、HashMap、Entry

> java.util.Map下的接口和继承类关系简易结构图：
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/901308565e5c43d8bdd8b4ea1b5d5960.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

`HashMap`是映射关系，即键`Key`值`Value`对

![在这里插入图片描述](https://img-blog.csdnimg.cn/f2020c0059ce4628abf6609c55e4e146.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
`HashMap`不能使用迭代器`Iterator`

![在这里插入图片描述](https://img-blog.csdnimg.cn/4c7ed550b1a74e2da9cb0e5f050ac205.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16) 
`.replace()`方法可以替换键`Key`对应的值`Value`
![在这里插入图片描述](https://img-blog.csdnimg.cn/60d6d5048a9c4da786766081f0e3ea3f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
让`Key`以集合形式输出，`.keySet()`方法返回值是`HashMap`中`Key`值的集合
![在这里插入图片描述](https://img-blog.csdnimg.cn/191ee118db6c42d88c3cae46e42f6dcd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
让`HashMap`以集合形式输出， `.entrySet()`方法的返回值也是Set集合
![在这里插入图片描述](https://img-blog.csdnimg.cn/4175ce26315942478d25dfc5d7c3855a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 16. Map注意点
已经存在的键值对，再次`.put()`会替换原来的，`.get()`不存在的值会返回`null`
![在这里插入图片描述](https://img-blog.csdnimg.cn/d7770b1fcb1e450b9e1ee1f900ce4298.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 17. Entry与Map转换Set之后遍历： Iterator<Entry<Integer,Integer>> iterator = entrySet.iterator(); （什么？看不懂这行？）

 - `Entry`就是用来管理键值对对象的，将对象包裹起来，提供遍历的方式
 - `Entry`可以使用迭代器，筛选值，但只适合在内存中使用，不适用于JDBC

![在这里插入图片描述](https://img-blog.csdnimg.cn/cdf84861a4e942d3ab0439185491c0db.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)




# 18. 提及 LinkedHashMap以及课后作业

`HashMap`是无序的，可以自定义泛型，而`LinkedHashMap`相当于有序的`HashMap`，可以自己写一个包括增删改查的学生管理系统了
![在这里插入图片描述](https://img-blog.csdnimg.cn/b7e2b7d666e8409c8007e85d67415fbc.png)



# 19. 集合框架部分结束
剩下的类需要自己去学习了！了解各类是怎么实现的，以及其之间的区别，JDK的新特性暂时用不到，还没学习到框架
