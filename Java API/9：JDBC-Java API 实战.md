@[TOC](目录)
# 1. 说明


用Java语言操作Mysql，首先需要学习Mysql

> **安装教程详见：[一、安装、连接以及配置MySQL](https://blog.csdn.net/qq_46207024/article/details/119942470)**
> **Mysql基础教程详见：[「MySQL」从零到删库](https://blog.csdn.net/qq_46207024/article/details/119900462)**

# 2. JDBC的由来以及定义
**JDBC是什么？**

 - Java数据库连接(Java Database Connectivity)简称JDBC
 - JDBC是Java操作各数据库的一种规范，是Java语言中用来规范客户端程序如何来访问数据库的应用程序接口，提供了诸如查询和更新数据库中数据的方法。JDBC是面向关系型数据库的

**打个比方？**
 - 假设Java公司是布料厂，那么各SQL数据库公司就是服装设计厂
 - Java公司规定JDBC接口，允许去操作各数据库，相当于提供原材料
 - 各SQL公司去实现接口，相当于拿原材料设计出自己的服装
![在这里插入图片描述](https://img-blog.csdnimg.cn/b3d6917004f1469d821d6dc68c4097af.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 3. JDBC体验，statement.executeQuery() 查询
首先要导入MySQL jar包，其相当于物流公司，将布料厂的原材料运输到服装设计厂里，让服装厂设计
> **Java MySQL Connector/J 包下载详见：[MySQL Connector/J](https://mvnrepository.com/artifact/mysql/mysql-connector-java)**

![在这里插入图片描述](https://img-blog.csdnimg.cn/548274aef8c346cea5ee9ae6328aaf66.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
下载好的jar包拖入lib文件夹下
![在这里插入图片描述](https://img-blog.csdnimg.cn/5cf28c07a5ca400d94471dbd33e74064.png)


引入jar包并导入库中
![在这里插入图片描述](https://img-blog.csdnimg.cn/4b2c15503f7040b694f79687ca73f72e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_14,color_FFFFFF,t_70,g_se,x_16)
连接数据库并创建一个Info表
![在这里插入图片描述](https://img-blog.csdnimg.cn/9bc650eed93e4413a99ec946620521b4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
创建JDBCDemo类写入代码，导入包所用到的方法都是在 java.sql里的，`import java.sql.*`
![在这里插入图片描述](https://img-blog.csdnimg.cn/f8e8fe0ccbb643819f130f83edacdc12.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


# 4. 整理和释放

规范代码

```java
public class JDBCDemo01 {
    public static final String URL = "jdbc:mysql://127.0.0.1:3306/student";
    public static final String USER = "root";
    public static final String PASSWORD = "xxxxxx";
    public static final String DRIVER = "com.mysql.jdbc.Driver";

    public static Connection connection;
    public static Statement statement;
    public static ResultSet resultSet;
    public static void main(String[] args) {
        try {
        //1.加载驱动程序，给布料厂打电话，我是mysql公司的
        Class.forName(DRIVER);
        //2.获得数据库的连接，告诉物流具体走什么路线
        connection = DriverManager.getConnection(URL, USER, PASSWORD);
        //3.获取数据库操作对象，货送到了，然后卸货到仓库
        statement = connection.createStatement();
        //4.从仓库中筛选出要用的货，查询Sql语句
        resultSet = statement.executeQuery("SELECT * FROM info");            
        while (resultSet.next()){
            int id = resultSet.getInt(1);
            String name = resultSet.getString(2);
            int age = resultSet.getInt(3);

            System.out.println("[" + id + ","+ name+ "," + age + "]");
        }
        //5.完成所有操作，关闭结果，关闭仓库，再关闭数据库连接
        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            try {
                resultSet.close();
                statement.close();
                connection.close();
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }
}
```

# 5. 封装JDBCUtils
如果每次查询都要重新写配置文件是件很麻烦的事，可以将配置文件封装起来，在src下创建db.properties配置文件，写入配置项
![在这里插入图片描述](https://img-blog.csdnimg.cn/5e91e5a4a2ec4ffa9822318929edf8ab.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

创建`com.google.util`包，创建`JDBCUtils`类

```java
public class JDBCUtils {
    private static String url;
    private static String user;
    private static String password;
    private static String driver;
    //静态代码，做预处理
    static {
        try {
            //JDBCUtils.class.getClassLoader()
            //读取配置文件
            InputStream inputStream = ClassLoader.getSystemResourceAsStream("db.properties");
            //加载对象
            Properties properties = new Properties();
            properties.load(inputStream);

            //读取配置项
            url = properties.getProperty("url");
            user = properties.getProperty("user");
            password = properties.getProperty("password");
            driver = properties.getProperty("driver");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
    //4.测试是否加载成功
    public static void init(){
        System.out.println("加载成功");
    }
    //5.创建单例，获取配置项
    public static Connection getConnection() throws SQLException{
        return DriverManager.getConnection(url, user, password);
    }
    //6.释放，关闭结果，关闭仓库，关闭数据库连接
    public static void close(Connection connection, Statement statement, ResultSet resultSet) throws SQLException {
        if (resultSet != null){
            resultSet.close();
        }
        if (statement != null){
            statement.close();
        }
        if (connection != null){
            connection.close();
        }
    }
    public static void close(Connection connection, Statement statement) throws SQLException {

        if (statement != null){
            statement.close();
        }
        if (connection != null){
            connection.close();
        }
    }
}
```
创建测试类，测试能否加载`JDBCUtils`
![在这里插入图片描述](https://img-blog.csdnimg.cn/9d1e7022ee434cb7b118818f1b1bc1df.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# 6. 增删改 —— executeUpdate()
确认获取数据库连接和操作对象信息
![在这里插入图片描述](https://img-blog.csdnimg.cn/f7f539550f7246d5ae78b4b7f29e031e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
只有查询是`executeQuery()`，增删改都是`executeUpdate()`
![在这里插入图片描述](https://img-blog.csdnimg.cn/fcc7ce7470174812a0a38612ff1bca89.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
运行代码查看数据库已经插入成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/810dd3d1ad63444bbea6d28206514c20.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
更新或者删除，也是同理
![在这里插入图片描述](https://img-blog.csdnimg.cn/73ae27eabcd946e3ac6d6d7e4cd443fa.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
运行代码查看数据库已经更新成功

![在这里插入图片描述](https://img-blog.csdnimg.cn/f9b78855d1e440d1a47dffa715c5dd1a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
```java
    public void UpdateTest(){
        try {
            //1.获取数据库连接和操作对象
            connection = JDBCUtils.getConnection();
            statement = connection.createStatement();
            //2.更新一条数据
            String sql = "update info set name ='Pig' where id = 4";
            int res = statement.executeUpdate(sql);
            //3.判断数据是否更新成功
            if (res != 0){
                System.out.println("Update success");
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            try {
             //4.调用重载方法，关闭仓库和数据库连接
                JDBCUtils.close(connection, statement);
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
```

# 7. 字符编码问题
**如果插入中文时乱码怎么办？**

 - 字符编码问题，需要更改数据库、IDE、终端的编码格式为`UTF-8`，在配置项中添加字符编码

![在这里插入图片描述](https://img-blog.csdnimg.cn/c3f96a5767e640ddb3fd4b411f3424b3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_13,color_FFFFFF,t_70,g_se,x_16)
![在这里插入图片描述](https://img-blog.csdnimg.cn/18082a53ef93442aa8433f58f9ac7991.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/9b8b663b27e9444baf12877040ee8c93.png)

```java
url = jdbc:mysql://127.0.0.1:3306/student?characterEncoding=utf-8
user = root
password = xxxxxx
driver = com.mysql.jdbc.Driver
```
> **参考：[2.6 修改数据库字符编码](https://blog.csdn.net/qq_46207024/article/details/119966422)**

# 8. PreparedStatement和问号占位符
**如果要求用户输入数据，需要用户手动编写sql语句吗？**

 - 不需要，用`PreparedStatement`就可以

**PreparedStatement是什么？**

 - `PreparedStatement`是预编译的，可以简化执行查询或者更新数据表数据，对于批量处理可以大大提高效率，也叫JDBC存储过程
 - `public interface PreparedStatement extends Statement;`

**Statement和PreparedStatement的区别？**

 - 使用`Statement`需要进行拼写SQl语句

```java
        resultSet = statement.executeQuery("SELECT * FROM info");
        while (resultSet.next()){
            int id = resultSet.getInt(1);
            String name = resultSet.getString(2);
            int age = resultSet.getInt(3);
            System.out.println("[" + id + ","+ name+ "," + age + "]");
        }
```

 - 使用`PreparedStatement`是`Statement`的子接口，可以传入带占位符的SQL语句，提供了补充占位符变量的方法，`preparedStatement()`要求写入sql语句
```java
preparedStatement = connection.prepareStatement(sql);
```

```java
package com.company;
import com.google.util.JDBCUtils;
import org.junit.Test;
import java.util.*;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Scanner;

/**
 * @author:Yeats
 * @description:
 * @date: 4/4/2022
 * @time: 4:35 PM
 */
public class JDBCDemo03 {
    public static Connection connection;
    public static PreparedStatement preparedStatement;

    public static void main(String[] args) {
        try {
            //1.获取数据库连接和操作对象
            connection = JDBCUtils.getConnection();

            //2.用户输入信息，使用占位符的sql语句，更新一条数据
            String sql = "INSERT INTO info(name, age) values(?, ?)";
            System.out.println("请先输入姓名，再输出年龄，用回车隔开：");
            Scanner scanner = new Scanner(System.in);
            String name = scanner.nextLine();
            int age = scanner.nextInt();

            //3.preparedStatement传入带占位符的sql语句，set方法设置每一个位置的值，并执行更新操作
            preparedStatement = connection.prepareStatement(sql);
            preparedStatement.setString(1, name);
            preparedStatement.setInt(2, age);
            int res = preparedStatement.executeUpdate();

            //4.判断数据是否更新成功
            if (res != 0){
                System.out.println("Update success");
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            try {
            //5.调用重载方法，释放资源
                JDBCUtils.close(connection, preparedStatement);
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }

    }
}
```

注意，`parameterindex`是指传入问号的下标
![在这里插入图片描述](https://img-blog.csdnimg.cn/430eef6a0f094095aa3e640694b4ff49.png)

同时需要更改配置文件`JDBCUtils`类中的`Statement`成`PreparedStatement`

```java
package com.google.util;

import javax.swing.*;
import java.io.InputStream;
import java.sql.*;
import java.util.Properties;

/**
 * @author:Yeats
 * @description:
 * @date: 4/4/2022
 * @time: 9:30 AM
 */
public class JDBCUtils {
    private static String url;
    private static String user;
    private static String password;
    private static String driver;
    //静态代码，做预处理
    static {
        try {
            //JDBCUtils.class.getClassLoader()
            //读取配置文件
            InputStream inputStream = ClassLoader.getSystemResourceAsStream("db.properties");
            //加载对象
            Properties properties = new Properties();
            properties.load(inputStream);

            //读取配置项
            url = properties.getProperty("url");
            user = properties.getProperty("user");
            password = properties.getProperty("password");
            driver = properties.getProperty("driver");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
    //4.测试是否加载成功
    public static void init(){
        System.out.println("加载成功");
    }
    //5.创建单例，获取配置项
    public static Connection getConnection() throws SQLException{
        return DriverManager.getConnection(url, user, password);
    }
    //6.释放资源，关闭结果，关闭仓库，关闭数据库连接
    public static void close(Connection connection, PreparedStatement preparedStatement, ResultSet resultSet) throws SQLException {
        if (resultSet != null){
            resultSet.close();
        }
        if (preparedStatement != null){
            preparedStatement.close();
        }
        if (connection != null){
            connection.close();
        }
    }
    public static void close(Connection connection, PreparedStatement preparedStatement) throws SQLException {

        if (preparedStatement != null){
            preparedStatement.close();
        }
        if (connection != null){
            connection.close();
        }
    }
}
```

运行成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/5a3e3e8d1f7e466e8d2ec81c3d762ec3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

![在这里插入图片描述](https://img-blog.csdnimg.cn/8a75610849124a3d98f3c4736b802131.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
如果要执行查询操作，需要将`excuteUpdate()`改成`excuteQuery()`，大体上与`Statement`形式相同
# 9. 最终Demo说明
最好一次性学完，做好准备，头脑清晰再去学

# 10. 对象的封装，重构代码， 学生管理系统模块化编程

> **项目源代码下载详见：[面向对象大胆向前！Java API实战-视频和资料-Frank](https://www.yuque.com/frank-93a7b/fuck/mobhay)**

IDEA导入有jar包的Java项目(版本2019.3.2)，点击import

![在这里插入图片描述](https://img-blog.csdnimg.cn/ea4a72777b7a4a92ba5b58266bbc708b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
找到项目的位置，点OK
![在这里插入图片描述](https://img-blog.csdnimg.cn/05e419c8b8544a768160a8a162be7481.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_13,color_FFFFFF,t_70,g_se,x_16)
选择从已存在的源文件创建项目
![在这里插入图片描述](https://img-blog.csdnimg.cn/0b9b58769f5645549e93ceddcaa6106e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
确认项目名称与路径
![在这里插入图片描述](https://img-blog.csdnimg.cn/233b4d53a5fb43f6bc78c7a9c2633c1c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

已找到项目的源文件，请选择被添加到项目的根中，确认项目根目录

![在这里插入图片描述](https://img-blog.csdnimg.cn/5c34d1b2e3ef42dbac31c87d73572a8a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
检查导入的jar包，并勾选jar包
![在这里插入图片描述](https://img-blog.csdnimg.cn/050a6b5fe89648079f1a988dbe3c58c1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)

审查建议的项目模块结构。在此阶段，您可以设置模块名称，从项目中排除特定模块，合并或拆分单个模块。所有模块之间的依赖关系都将自动更新，就像库中的依赖项一样

![在这里插入图片描述](https://img-blog.csdnimg.cn/e591eb797eef4e76aec8644f0b7fc286.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)
查看项目结构，手动导入所有jar包


![在这里插入图片描述](https://img-blog.csdnimg.cn/7ceb9fcd810a48da990c7778b45c5db2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_20,color_FFFFFF,t_70,g_se,x_16)


![在这里插入图片描述](https://img-blog.csdnimg.cn/a936d6e208924976b144fa7b58686ba2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAWWVhdHNfTGlhbw==,size_12,color_FFFFFF,t_70,g_se,x_16)
直接运行项目会抛出SQL异常，需要更改`db.properties`代码，将`localhost`改成`127.0.0.1:3306`

```java
url = jdbc:mysql://127.0.0.1:3306/student?characterEncoding=utf-8
user = root
password = xxxxxx
driver = com.mysql.jdbc.Driver
```


