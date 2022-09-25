@[TOC](目录)

# 1. 引言

 - 文件要区别绝对路径和相对路径，在Win系统中的文件路径和Linux/nuix系统中的路径是不一样的

# 2. 绝对路径和相对路径？先学送快递吧！

 - 分清文件、文件夹、文件路径
 - 买东西填收货地址就是绝对路径，无论在哪都能确定
 - 例如绝对路径上海徐汇区微软大厦，对于闵行区XX小区而言是相对路径

# 3. 绝对路径

 - Win中是从盘符开始，使用`\`一层一层向下，`D:\DevTools\Git\bin`
 - Linux中是从根目录`/`开始，使用`/`一层一层向下，`/home/shea/Documents/pdf`

# 4. 相对路径

 - 相对路径是已知一个绝对路径，然后另外一个路径与这个文件夹的关系

以VSCode为例右键文件

 - `Cpoy Path`复制绝对路径`D:\Project\ideaProject\Demo2\src\com\company\Calc.java`
 - `Copy Relative Path`复制相对路径`src\com\company\Calc.java`

![在这里插入图片描述](https://img-blog.csdnimg.cn/41e8f5d668054333bc4affcd71068d6c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_14,color_FFFFFF,t_70,g_se,x_16)

在编译器中表示路径要有两个斜杠`D:\\DevTools\\Git\\bin`，在编译语言中`\`是转译符号，要让编译器识别`\`必须要写两个斜杠 

# 5. File类

 - 使用`File`类`new`一个对象时一定要使用绝对路径，这个类中不仅包含了对文件的操作，还有对文件夹的操作
 - 文件流中最重要的是对文件路径的了解，调用文件流中的类

![在这里插入图片描述](https://img-blog.csdnimg.cn/8497a14760bc47ab89d1cc861585bf5a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/4d4f037d5f9d4243917245ca832ffac1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
判断是否为文件，以及字节长度
![在这里插入图片描述](https://img-blog.csdnimg.cn/5ab146c1d86542f79d06db4220c79f78.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
输出文件夹名字
![在这里插入图片描述](https://img-blog.csdnimg.cn/96c073965f394d9bbd92adea65080d75.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 6. Linux上的绝对路径有所不同

 - Linux上的绝对路径从根目录开始，表示的方式是一个斜杠`/` ，没有转义字符的含义；而Windows中 `\\`表示转义字符

下面用用`WSL`来演示，`cd`命令进入文件夹

![在这里插入图片描述](https://img-blog.csdnimg.cn/d5c0c7b6f7c64925974ca682c90117de.png)
`ls`命令查看当前文件夹下面的文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/b789f9138fed4a0a881e9e5fa6bf1eeb.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

