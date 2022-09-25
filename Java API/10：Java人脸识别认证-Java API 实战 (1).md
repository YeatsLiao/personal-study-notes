@[TOC](目录)
# 1. 提出问题，引入SDK的概念
**什么是SDK？**

 - 我们并不具备开发人脸识别的能力，但我们可以用大公司已经开发好的工具或者功能，来实现人脸识别，而大公司提供的就叫SDK(Software Development Kit)
 - 软件开发工具包广义上指辅助开发某一类软件的相关文档、范例和工具的集合
# 2. 选择平台
大部分人脸识别平台都是要钱的，虹软(ArcSoft) 公司很良心，免费，并且提供离线版本

> **详见：[ArcFace 3.0 免费离线人脸识别SDK](https://ai.arcsoft.com.cn/product/arcface.html)**

# 3. SDK下载和文档说明

> **详见：[虹软开发者中心](https://ai.arcsoft.com.cn/ucenter/resource/build/index.html#/index)**

注册并使命认证后，选择免费SDK，人脸识别(ArcFace)

![在这里插入图片描述](https://img-blog.csdnimg.cn/e9ba7ea04aa646739c5603e3a1177668.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/56d00312476f462283692a50b4af8b83.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_19,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/cfe794cc30de429b9d3a5062a32bd537.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_18,color_FFFFFF,t_70,g_se,x_16)
点击确认创建完成，下载SDK

![在这里插入图片描述](https://img-blog.csdnimg.cn/3b16e9cc6a564305a7e05e59208cd801.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)




# 4. 人脸检测
SDK包结构
![在这里插入图片描述](https://img-blog.csdnimg.cn/4c961b666f6345bc97948791f56b48e4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

导入SDK，也就是刚下载的包
![在这里插入图片描述](https://img-blog.csdnimg.cn/d62a8f374ecb4a40ba55021d3986c2e3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/406da7bdf17d42b0ad5eb5932dfbf0ca.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/052cff569405450795d6c67f965e294b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
导入成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/db1e85e01d154b3b97a97e5f3eee5d4c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
从官网获取`appId`和`sdkKey`，将`libs`文件路径设置好

![在这里插入图片描述](https://img-blog.csdnimg.cn/6a56e9184619437f8c38f727ed9275ff.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
创建一个`Test`文件，将代码块只保留到初始化引擎，初次运行，没有任何提示，表示成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/6e35ba0dad5f4c38858ccab43541b19a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


放两张图片，设置好图片文件路径
![在这里插入图片描述](https://img-blog.csdnimg.cn/aba0adc866174194b251073f4f717b9c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

首次验证需要联网，运行人脸检测成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/58988a8b8a3840848c8eefcf0fb53483.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)



# 5. 人脸对比

加入两个人脸检测，进行特征对比
![在这里插入图片描述](https://img-blog.csdnimg.cn/f45ad1a38b8e4b6981b1b3c9eca9faec.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 6. 建议和结束语

 - 初始化不应该出现在server层，可以将其封装起来
 - 可以自己把人脸检测封装在函数中，方便应用

