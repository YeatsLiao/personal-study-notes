# 目录
# 零、数据库的产生
1. 什么是数据库 database
2. 抛出问题，数据库的产生
3. 数据库萌芽阶段的发展历程
4. CRUD
5. 层次模型
6. 网状模型
7. 关系型数据库
8. 企业和我们都选什么数据库呢？

> **详见：[零、数据库的产生](https://blog.csdn.net/qq_46207024/article/details/119919224)**

# 一、安装、连接以及配置MySQL
1. windows两种安装方式，入门选手推荐第二种(win10演示)
2. 更改终端，放弃cmd作为主要终端，使用一流终端
3. MYSQL服务的启动与停止
4. 连接mysql
5. 初始化data数据文件夹

> **详见：[一、安装、连接以及配置MySQL](https://blog.csdn.net/qq_46207024/article/details/119942470)**

# 二、数据库的基本操作
1. 数据库的显示讲解
2. 创建数据库
3. 删除数据库
4. 查看创建的数据库的SQL
5. 创建数据库指定字符编码以及查看字符编码
6. 修改数据库字符编码
7. 数据库操作的结束语

> **详见：[二、数据库的基本操作](https://blog.csdn.net/qq_46207024/article/details/119966422)**

# 三、表的基本操作
1. 提出问题，引入“表“的概念与思维模式 table
2. 引用数据库和查看数据库中的表
3. 创建表
4. 创建表（企业用，有B格）
5. 查看表结构
6. 删除表
7. 修改表

> **详见：[三、表的基本操作](https://blog.csdn.net/qq_46207024/article/details/119988070)**

# 四、数据操作
1. 插入数据
2. 一次性插入多条数据
3. 删除数据
4. 清空表
5. 小细节
6. 更新数据
7. 查询表数据（基本）
8. SQL语句区分
9. 表结束语
10. 字符集编码问题

> **详见：[四、数据操作](https://blog.csdn.net/qq_46207024/article/details/120030026)**

# 五、数据类型
1. 数据库的数据类型问题
2. int数值类型
3. int类型实际操作和注意事项
4. 浮点数类型
5. 定点数类型
6. 字符串与文本类型
7. 布尔类型
8. 枚举类型
9. 枚举类型的另类存储方式
10. 枚举类型的好处，为何要用枚举类型，企业可能用在哪？
11. set类型
12. 时间日期类型

> **详见：[五、数据类型](https://blog.csdn.net/qq_46207024/article/details/120148025)**

# 六、列属性完整性
1. 列属性问题
2. Primary key主键作用以及企业用途
3. 删除主键、组合键、选择主键
4. 复合主键究竟有什么用？
5. unique唯一键的作用以及使用
6. 唯一键扩展
7. 主键和唯一键区别
8. sql内注释代码注释
9.  数据库完整性
10. 引用数据表的完整性问题，抛出外键的概念
11. 外键
12. 什么时候设计外键呢？
13. 更正上节课错误，删除外键
14. 外键三种操作：严格、置空、级联的使用场景以及介绍
15. 置空和级联演示

> **详见：[六、列属性完整性](https://blog.csdn.net/qq_46207024/article/details/120344327)**

# 七、数据库设计思维
1. 数据库设计的基本概要
2. 实体和实体之间的关系
3. Codd第一范式：确保每列原子性
4. Codd第二范式：非键字段必须依赖与键字段 
5. Codd第三范式：消除传递依赖

> **详见：[七、数据库设计思维述](https://blog.csdn.net/qq_46207024/article/details/120403789)**

# 八、单表查询
1. 开端
2. select
3. from
4. dual
5. where
6. in
7. between...and
8. is null
9. 聚合函数
10. 第三方客户端的使用
11. like模糊查询
12. order by 排序查询
13. group by 分组查询
14. group_concat
15. having
16. limit
17. distinct all

> **详见：[八、单表查询](https://blog.csdn.net/qq_46207024/article/details/120410558)**

# 九、多表查询
1. union联合查询
2. inner join内联查询
3. inner join注意事项
4. left join
5. rigth join
6. cross join
7. natural join
8. 无公共同名字段的自然返回笛卡尔积
9. using
10. 哪一个实用？

> **详见：[九、多表查询](https://blog.csdn.net/qq_46207024/article/details/120487446)**

# 十、子查询
1. 子查询基本语法
2. in 和 not in
3. exists 和 not exists
4. 基础结束语

> **详见：[十、子查询](https://blog.csdn.net/qq_46207024/article/details/120487544)**

# 十一、高级部分
 （一）view 视图
1. 开场
2. view视图创建、使用以及作用
3. 显示视图
4. 更新和删除视图
5. 视图算法： temptable, merge

（二）transaction 事务
1. 事务的提出
2. transaction
3. rollback to point
4. ACID
5. 注意事项

 （三）索引
1. 四大索引

（四）存储过程

1. delimiter
2. procedure存储过程的用途

（五）有趣的函数

1. number
2. string
3. others

> **详见：[十一、高级部分](https://blog.csdn.net/qq_46207024/article/details/120487558)**

# 十二、企业规范约束
1. ★库表字段约束规范
2. 索引规范
3. ★SQL开发约束规范
4. 其他规范

> **详见：[十二、企业规范约束](https://blog.csdn.net/qq_46207024/article/details/120487576)**

![在这里插入图片描述](https://img-blog.csdnimg.cn/8c5d16a703804566ad732c97846660df.png)
**该笔记由[Yeats_Liao](https://blog.csdn.net/qq_46207024?type=blog)与[Shea_Qiu](https://blog.csdn.net/weixin_45924718?type=blog)共同完成**

**以上所有内容来自课程个人笔记：[「MySQL」从零到删库精品课程-Frank](https://www.bilibili.com/video/BV18i4y187i3)**
