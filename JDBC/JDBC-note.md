# JDBC学习

## 1.  视频链接

https://www.bilibili.com/video/BV1eJ411c7rf/?spm_id_from=333.788.videocard.32

## 2.  JDBC笔记

### 2.1 DAY1

1. 文件为什么放在数据库中：可存储量大，方便查询，可设限制，比如字段类型、个数等。

2. IDEA创建测试类时，@test报红：直接快捷键` Enter+Alt`，导入` junit5`。` junit4和5`的区别https://zhuanlan.zhihu.com/p/144763642。

3. 如果mysql是8.0版本的，对应的驱动也需要下载8.0版本的。并且在后续不需要按照教程修改驱动。链接：https://dev.mysql.com/downloads/file/?id=477058

4. mysql8.0以上的用 

   ```java
   driverClass=com.mysql.cj.jdbc.Driver
   url=jdbc:mysql://localhost:3306/test?characterEncoding=utf8&useSSL=false&serverTimezone=UTC&rewriteBatchedStatements=true
   ```

   

   ![image-20201217162506810](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201217162506810.png)

   ![image-20201217160026522](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201217160026522.png)

   连接成功。

5. IDEA提示代码需要处理异常，直接函数抛出异常即可，如果使用try catch，函数中可能很多地方都需要try catch，前一种方法可以一键解决。

6. IDEA进行statement的测试时，控制台不能输入：https://blog.csdn.net/qq_37714755/article/details/104213537?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control

7. IDEA中的快捷键 ctrl+alt+t（如果失效：https://blog.csdn.net/weixin_41231928/article/details/99411348）
    选中想要包裹的代码，按住此快捷键，会出现以下内容：选中某个即可

   ![image-20201217185253452](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201217185253452.png)

8. IDEA设置自动生成作者，时间等

   ![image-20201217190335678](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201217190335678.png)

9.  输入/** ,点击“Enter”，自动根据参数和返回值生成注释模板

10. 第一个出现的T，是定义一个范型名为T，当然可以为任何一个或多个字母。后面出现两个T都是在使用范型，前一个代表返回T类型变量，后一个是只接受T类型变量的可变参数（可变参数:一个或者多个，其实最后会被转化成数组）。

    ![image-20201218171422149](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201218171422149.png)

### 2.2DAY2

今天莫问题莫问题！

### 2.3DAY3

1. 在事务处理时，演示修改增删改通用函数的数据库连接时，一定要**删掉增删改通用函数里的连接**，在测试函数中连接数据库，否则即使在测试函数中连接并关闭，也不会有回滚的效果。

2. IDEA如何进行junit单元测试：https://jingyan.baidu.com/article/f7ff0bfccd661d2e26bb131a.html

3. java的内存泄漏：内存中存在对象不能被回收

4. IDEA解决不能创建XML文件：https://blog.csdn.net/li1325169021/article/details/93158207

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <configuration>
       
   </configuration>
   ```


### 2.4DAY4

1. 在给**c3p0**配置文件写**jdbcUrl** 时报错：

   ![image-20201220103324697](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220103324697.png)

   解决：做为配置文件，&要写成`&amp;`配置文件中&字符需要进行转义，所以写成`&amp;`就相当于&。主要就是&符号的区别。

2. c3p0配置文件中一定不要有，否则会报错`<configuration>`

   ![image-20201220103942965](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220103942965.jpg)

3. IDEA代码分屏显示

   ![img](https://img-blog.csdn.net/20180807223717386?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29veWhhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

4. 写dbcp的配置文件时，要注意配置信息名的大小写，比如“password”不能写成“passWord”。

   ![屏幕截图 2020-12-20 113652](C:\Users\蔲丫丫\Desktop\屏幕截图 2020-12-20 113652.jpg)

## JDBC复习

### 01-JDBC概述

#### 1.1 数据的持久化：

持久化(persistence)：**把数据保存到可掉电式存储设备中以供之后使用**。

#### 1.2 JDBC的理解：

JDBC(Java Database Connectivity)是一个**独立于特定数据库管理系统、通用的SQL数据库存取和操作的公共接口**（一组API）

简单理解为：JDBC，是SUN提供的一套接API，使用这套API可以实现对具体数据库的操作（获取连接、关闭连接、DML、DDL、DCL）

#### 1.3 图示理解：

![image-20201220162446479](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220162446479.png)

好处：

![image-20201220162750176](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220162750176.png)

> 从开发程序员的角度：不需要关注具体的数据库的细节
>
> 数据库厂商：只需要提供标准的具体实现

#### 1.4 数据库的驱动：

数据库厂商针对于JDBC这套接口，提供的具体实现类的集合。

类似：

![正在安装驱动](C:\Users\蔲丫丫\Desktop\尚硅谷_宋红康_JDBC核心技术(2019新版)\3-资料\正在安装驱动.png)



#### 1.5 面向接口编程的思想

**JDBC是sun公司提供一套用于数据库操作的接口，java程序员只需要面向这套接口编程即可。**

**不同的数据库厂商，需要针对这套接口，提供不同实现。不同的实现的集合，即为不同数据库的驱动。**

### 02-数据库的连接

#### 2.1 数据库连接最终实现方法：

```java
 /**
     * @Description 获取数据库的连接
     * @Author oo
     * @return
     * @Date 2020-12-17 19:04
     * @throws Exception
     */
    public static Connection getConnection() throws Exception {
//        1.读取配置文件中的4个基本信息
        InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("jdbc.properties");
        Properties pros = new Properties();
        pros.load(is);
        String user = pros.getProperty("user");
        String password = pros.getProperty("password");
        String url = pros.getProperty("url");
        String driverClass = pros.getProperty("driverClass");

//        2.获取驱动
        Class.forName(driverClass);
//        3.获取连接
        Connection conn = DriverManager.getConnection(url,user,password);
        return conn;
    }
```

#### 2.2 配置文件说明

其中，配置文件 `jdbc.properties` ：此配置文件声明在工程的 `src` 下  。

> 说明：
>
> 1. password为你的数据库账户的密码。
> 2. 此url以及driverClass的设置对应于mysql8.0版本。

```java
user=root
password=*****
url=jdbc:mysql://localhost:3306/test?characterEncoding=utf8&useSSL=false&serverTimezone=UTC&rewriteBatchedStatements=true
driverClass=com.mysql.cj.jdbc.Driver
```

### 03-JDBCUtil.java

```java
package com.oo.util;

/**
 * @Description 操作数据库的工具类
 * @Author oo
 * @Version
 * @Date 2020-12-17 19:04
 */
public class JDBCUtils {

    /**
     * @Description 获取数据库的连接
     * @Author oo
     * @return
     * @Date 2020-12-17 19:04
     * @throws Exception
     */
    public static Connection getConnection() throws Exception {
//        1.读取配置文件中的4个基本信息
        InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("jdbc.properties");
        Properties pros = new Properties();
        pros.load(is);
        String user = pros.getProperty("user");
        String password = pros.getProperty("password");
        String url = pros.getProperty("url");
        String driverClass = pros.getProperty("driverClass");

//        2.获取驱动
        Class.forName(driverClass);
//        3.获取连接
        Connection conn = DriverManager.getConnection(url,user,password);
        return conn;
    }

    /**
     * @Description 关闭连接和Statement的操作
     * @param conn
     * @param ps
     */
    public static void closeResource(Connection conn, Statement ps){
        try {
            if(ps != null)
                ps.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
        try {
            if(conn != null)
                conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }

    }

    /**
     * @Description 关闭资源操作
     * @param conn
     * @param ps
     * @param rs
     */
    public static void closeResource(Connection conn, Statement ps,ResultSet rs){
        try {
            if(ps != null)
                ps.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
        try {
            if(conn != null)
                conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
        try {
            if(rs != null)
                rs.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

### 04-Statement接口实现CRUD操作（了解）

#### 4.1 弊端

- **问题一：存在拼串操作，繁琐**

  ```java
  Scanner scanner = new Scanner(System.in);
  String user = scanner.next();
  ......
  String sql = "SELECT user,password FROM user_table WHERE user='"+ user +"' AND password= '" + password + "'";
  ```

- **问题二：存在SQL注入问题**

  SQL 注入是利用某些系统没有对用户输入的数据进行充分的检查，而在用户输入数据中注入非法的 SQL 语句段或命令(如：SELECT user, password FROM user_table WHERE user='a' OR 1 = ' AND password = ' OR '1' = '1') ，从而利用系统的 SQL 引擎完成恶意行为的做法。

  ```java
  SELECT user,password FROM user_table WHERE user='1' or ' AND password= '=1 or '1' = '1'
  
      //传入的user:1' or    password:=1 or '1' = '1
  ```

- **其他问题**

1. **statement**没办法操作**Blob**类型变量
2. **statement**实现批量插入时，效率较低

### 05-PreparedStatement替换Statement实现CRUD操作

#### 5.1 PreparedStatement的理解：

- PreparedStatement是Statement的子接口。
- An object that represents a precompiled SQL statement。
- 可以解决Statement的sql注入问题，拼串问题。

#### 5.2 使用PreparedStatement实现通用的增、删、改的方法：

```java
//通用的增删改操作
public void update(String sql,Object ...args){//sql中占位符的个数应该与可变形参args的个数一致
    Connection conn = null;
    PreparedStatement ps = null;
    try {
        conn = JDBCUtils.getConnection();
        ps = conn.prepareStatement(sql);
        for (int i=0;i<args.length;i++)
        {
            ps.setObject(i+1,args[i]);//注意i+1
        }
        ps.execute();
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(conn,ps);
    }
}
```

#### 5.3 使用PreparedStatement实现通用的查询操作：

```java
//返回多条查询记录的集合
public <T> List<T> getForList(Class<T> clazz,String sql,Object ...args){
    Connection conn = null;
    PreparedStatement ps = null;
    ResultSet rs = null;
    try {
        conn = JDBCUtils.getConnection();
        ps = conn.prepareStatement(sql);
        for (int i=0;i<args.length;i++) {
            ps.setObject(i + 1, args[i]);
        }
        rs = ps.executeQuery();
        ResultSetMetaData rsmd = rs.getMetaData();
        int columnCount = rsmd.getColumnCount();
        //创建集合对象
        ArrayList<T> list = new ArrayList<T>();
        while (rs.next()){
            T t = clazz.newInstance();
            for (int i=0;i<columnCount;i++) {
                Object columnValue = rs.getObject(i + 1);
                String columnLabel = rsmd.getColumnLabel(i + 1);
                Field field = clazz.getDeclaredField(columnLabel);
                field.setAccessible(true);
                field.set(t, columnValue);
            }
            list.add(t);
        }
        return list;
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(conn,ps,rs);
    }
    return null;
}
```

```java
//返回一条查询记录
public <T> T getInstance(Class<T> clazz,String sql,Object ...args) {
    Connection conn = null;
    PreparedStatement ps = null;
    ResultSet rs = null;
    try {
        conn = JDBCUtils.getConnection();
        ps = conn.prepareStatement(sql);
        for (int i=0;i<args.length;i++) {
            ps.setObject(i + 1, args[i]);
        }
        rs = ps.executeQuery();
        ResultSetMetaData rsmd = rs.getMetaData();
        int columnCount = rsmd.getColumnCount();
        if(rs.next()){
            T t = clazz.newInstance();
            for (int i=0;i<columnCount;i++) {
                Object columnValue = rs.getObject(i + 1);
                String columnLabel = rsmd.getColumnLabel(i + 1);
                Field field = clazz.getDeclaredField(columnLabel);
                field.setAccessible(true);
                field.set(t, columnValue);
            }
            return t;
        }

    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(conn,ps,rs);
    }
    return null;
}
```

#### 5.4 总结

##### 5.4.1 两种思想：

面向接口编程的思想

ORM编程思想（Object relational mapping)
* 一个数据表对应一个java类
* 表中的一条记录对应java类的一个对象
* 表中的一个字段对应java类的一个属性

##### 5.4.2 两种技术：

1. 使用结果集的元数据：ResultSetMetaData

> getColumnCount()：获取列数
>
> getColumnLabel()：获取列的别名
>
> 说明：如果sql中没给字段起别名，getColumnLabel()获取的就是列名

2. 反射的使用：

   - 创建对应的运行时的类的对象
   - 在运行时，动态的调用指定的运行时类的属性、方法

3. 查询的图示：

   ![image-20201220170942161](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220170942161.png)

### 06-PreparedStatement操作Blob类型的变量

#### 6.1 写入操作的方法

```java
FileInputStream is= new FileInputStream(new File("糖糖.jpg"));
ps.setBlob(4,is);
```

#### 6.2 读取操作的方法

```java
//            将Blob类型的字段下载下来，以文件的方式保存在本地
            Blob photo = rs.getBlob("photo");
            is = photo.getBinaryStream();
            fos = new FileOutputStream("zhangyuhao.jpg");
            byte[] buffer = new byte[1024];
            int len;
            while ((len = is.read(buffer))!=-1){
                fos.write(buffer,0,len);
            }
```

#### 6.3 具体的insert

```java
//向数据表customers中插入BlobL类型的字段
@Test
public void testInsert() throws Exception {
    Connection conn = JDBCUtils.getConnection();

    String sql = "insert into customers(name,email,birth,photo) values (?,?,?,?)";
    PreparedStatement ps = conn.prepareStatement(sql);

    ps.setObject(1,"张宇豪");
    ps.setObject(2,"zhang@qq.com");
    ps.setObject(3,"1992-09-08");
    FileInputStream is= new FileInputStream(new File("糖糖.jpg"));
    ps.setBlob(4,is);

    ps.execute();

    JDBCUtils.closeResource(conn,ps);
}
```

#### 6.4 具体的query

```java
//查询数据表cutomers中的Blob类型的字段
@Test
public void testQuery() {
    Connection conn = null;
    PreparedStatement ps = null;
    ResultSet rs = null;
    InputStream is = null;
    FileOutputStream fos = null;
    try {
        conn = JDBCUtils.getConnection();
        String sql = "select id,name,email,birth,photo from customers where id = ?";
        ps = conn.prepareStatement(sql);
        ps.setInt(1,21);

        rs = ps.executeQuery();
        if(rs.next()){
//            方式1
//            int id = rs.getInt(1);
//            String name = rs.getString(2);
//            String email = rs.getString(3);
//            Date birth = rs.getDate(4);

//            方式2:不需要管顺序
            int id = rs.getInt("id");
            String name = rs.getString("name");
            String email = rs.getString("email");
            Date birth = rs.getDate("birth");

            Customer cust = new Customer(id,name,email,birth);
            System.out.println(cust);

//            将Blob类型的字段下载下来，以文件的方式保存在本地
            Blob photo = rs.getBlob("photo");
            is = photo.getBinaryStream();
            fos = new FileOutputStream("zhangyuhao.jpg");
            byte[] buffer = new byte[1024];
            int len;
            while ((len = is.read(buffer))!=-1){
                fos.write(buffer,0,len);
            }
        }
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        try {
            is.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
        try {
            fos.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
        JDBCUtils.closeResource(conn,ps,rs);
    }

}
```

#### 6.5 注意的问题

如果在指定了相关的Blob类型以后，还报错：xxx too large，那么在mysql的安装目录下，找my.ini文件加上如下的配置参数： **max_allowed_packet=16M**。同时注意：修改了my.ini文件之后，需要重新启动mysql服务。

### 07-PreparedStatement实现高效的批量插入

#### 7.1 不同层次的实现方法

 层次一：使用Statement实现

```java
Connection conn = JDBCUtils.getConnection();
Statement st = conn.createStatement();
for (int i=1;i<=20000;i++){
     String sql = "insert into goods(name)values('name_"+i+"')";
     st.execute(sql);
}
```

层次二：使用PreparedStatement替换Statement

层次三：addBatch() / executeBatch() / clearBatch()

>  1.addBatch(),executeBatch(),clearBatch()
>  2.mysql服务器默认是关闭批处理的，我们需要通过一个参数，让mysql开启批处理的支持。 ?rewriteBatchedStatements=true 写在配置文件的url后面。
>  3.使用更新的mysql 驱动：mysql-connector-java-5.1.37-bin.jar

 层次四：设置连接不允许自动提交数据

#### 7.4 最终版的代码体现

```java
//  1000000:  花费的时间为14862
@Test
public void testInsert4() {

    Connection conn = null;
    PreparedStatement ps = null;
    try {
        long start = System.currentTimeMillis();
        conn = JDBCUtils.getConnection();

        //设置不允许自动提交数据
        conn.setAutoCommit(false);

        String sql = "insert into goods(name) values(?)";
        ps = conn.prepareStatement(sql);
        for (int i = 1;i<=1000000;i++)
        {
            ps.setObject(1,"name_"+i);

            //1.攒sql
            ps.addBatch();
            if(i%500==0){

                //2.执行batch
                ps.executeBatch();

                //3.清空batch
                ps.clearBatch();
            }
        }

        //提交数据
        conn.commit();
        long end = System.currentTimeMillis();

        System.out.println("花费的时间为"+(end-start));
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(conn,ps);
    }
}
```

#### 7.5 PreparedStatement与Statement的异同？

- 指出二者的关系？ **接口**与**子接口**的关系
- 开发中，PreparedStatement替换Statement
- An object that represents a precompiled SQL statement。
- **PreparedStatement 能最大可能提高性能：**
  - DBServer会对**预编译**语句提供性能优化。因为预编译语句有可能被重复调用，所以<u>语句在被DBServer的编译器编译后的执行代码**被缓存**下来，那么下次调用时只要是相同的预编译语句就不需要编译，只要将参数直接传入编译过的语句执行代码中就会得到执行。</u>
  - 在statement语句中,即使是相同操作但因为数据内容不一样,所以整个语句本身不能匹配,没有缓存语句的意义.事实是没有数据库会对普通语句编译后的执行代码缓存。这样<u>每执行一次都要对传入的语句编译一次。</u>
  - (语法检查，语义检查，翻译成二进制命令，缓存)
- PreparedStatement 可以防止 SQL 注入 

### 08-数据库事务

#### 8.1 事务

一组逻辑操作单元,使数据从一种状态变换到另一种状态。

> 一组逻辑操作单元，一个或多个DML操作

#### 8.2 事务处理的原则

保证所有事务都作为一个工作单元来执行，即使出现了故障，都不能改变这种执行方式。

当在一个事务中**执行多个操作时，要么所有的事务都被提交(commit)**，那么这些修改就永久地保存下来；要么数据库管理系统将**放弃所作的所有修改，整个事务回滚(rollback)到最初状态**。

> 说明：
>
> 1. 数据一旦提交，就不回滚
>
> 2. 哪些操作会导致数据的自动提交
>    - DDL操作一旦执行，都会自动提交
>      - set autocommit =false 对DDL操作失效
>    - DML默认情况下，一旦执行，就会自动提交
>      - 我们可以通过set autocommit = false 的方式取消DML操作的自动提交
>    - 默认在关闭连接时，会自动提交数据

#### 8.3 代码的体现

```java
 @Test
    public void testUpdateWithTx() {

        Connection conn = null;
        try {
            conn = JDBCUtils.getConnection();
            System.out.println(conn.getAutoCommit());
//            取消数据的自动提交
            conn.setAutoCommit(false);

            String sql1 = "update user_table set balance = balance-100 where user = ?";
            update(conn,sql1,"AA");

//        模拟网络异常
            System.out.println(10/0);

            String sql2 = "update user_table set balance = balance+100 where user = ?";
            update(sql2,"BB");

            System.out.println("转账成功");

//            提交数据
            conn.commit();
        } catch (Exception e) {
            e.printStackTrace();
//            回滚
            try {
                conn.rollback();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        } finally {
            //修改为自动提交数据
            //主要针对于使用数据库连接池的使用
            try {
                conn.setAutoCommit(true);
            } catch (SQLException e) {
                e.printStackTrace();
            }
            
            JDBCUtils.closeResource(conn,null);
        }
    }
```

#### 8.4 通用的增删改操作(考虑事务)

```java
//通用的增删改操作  ----version2.0
public int update(Connection conn,String sql,Object ...args){//sql中占位符的个数应该与可变形参args的个数一致
    PreparedStatement ps = null;
    try {
        ps = conn.prepareStatement(sql);
        for (int i=0;i<args.length;i++)
        {
            ps.setObject(i+1,args[i]);//注意i+1
        }
        return ps.executeUpdate();
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(null,ps);
    }
    return 0;
}
```

#### 8.5 通用的查询(考虑事务)

```java
//通用的查询操作，用于返回数据表中的一条记录(version 2.0:考虑上事务)
    public <T> T getInstance(Connection conn,Class<T> clazz,String sql,Object ...args) {
        PreparedStatement ps = null;
        ResultSet rs = null;
        try {
            ps = conn.prepareStatement(sql);
            for (int i=0;i<args.length;i++) {
                ps.setObject(i + 1, args[i]);
            }
            rs = ps.executeQuery();
            ResultSetMetaData rsmd = rs.getMetaData();
            int columnCount = rsmd.getColumnCount();
            if(rs.next()){
                T t = clazz.newInstance();
                for (int i=0;i<columnCount;i++) {
                    Object columnValue = rs.getObject(i + 1);
                    String columnLabel = rsmd.getColumnLabel(i + 1);
                    Field field = clazz.getDeclaredField(columnLabel);
                    field.setAccessible(true);
                    field.set(t, columnValue);
                }
                return t;
            }

        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(null,ps,rs);
        }
        return null;
    }
```

#### 8.6事务中必须知道的几点

##### 8.6.1 四大属性（ACID）

1. **原子性（Atomicity）**
   原子性是指事务是一个不可分割的工作单位，事务中的操作要么都发生，要么都不发生。 

2. **一致性（Consistency）**
   事务必须使数据库从一个一致性状态变换到另外一个一致性状态。

3. **隔离性（Isolation）**
   事务的隔离性是指一个事务的执行不能被其他事务干扰，即一个事务内部的操作及使用的数据对并发的其他事务是隔离的，并发执行的各个事务之间不能互相干扰。

4. **持久性（Durability）**
   持久性是指一个事务一旦被提交，它对数据库中数据的改变就是永久性的，接下来的其他操作和数据库故障不应该对其有任何影响。

   > 多余的小知识：
   >
   > BAT：百度、阿里、腾讯
   >
   > BBA：奔驰、宝马、奥迪
   >
   > TMD：头条、美团、滴滴

##### 8.6.2 数据操作过程中可能出现的问题(针对隔离性)

1. **脏读**: 对于两个事务 T1, T2, T1 读取了已经被 T2 更新但还**没有被提交**的字段。之后, 若 T2 回滚, T1读取的内容就是临时且无效的。
2. **不可重复读**: 对于两个事务T1, T2, T1 读取了一个字段, 然后 T2 **更新**了该字段。之后, T1再次读取同一个字段, 值就不同了。
3. **幻读**: 对于两个事务T1, T2, T1 从一个表中读取了一个字段, 然后 T2 在该表中**插入**了一些新的行。之后, 如果 T1 再次读取同一个表, 就会多出几行。

##### 8.6.3 数据库中的四种隔离级别

一致性和并发性：一致性越好，并发性越差。

![1555586275271](file://C:\Users\蔲丫丫\Desktop\尚硅谷_宋红康_JDBC核心技术(2019新版)\1-课件\课件-md\尚硅谷_宋红康_JDBC.assets\1555586275271.png?lastModify=1608457562)

- Oracle 支持的 2 种事务隔离级别：**READ COMMITED**, SERIALIZABLE。 Oracle 默认的事务隔离级别为: **READ COMMITED** 。


- Mysql 支持 4 种事务隔离级别。Mysql 默认的事务隔离级别为: **REPEATABLE READ。**

##### 8.6.4 如何查看并设置隔离级别

1. 查看当前的隔离级别: 

   ```mysql
   SELECT @@tx_isolation;
   ```

2. 设置当前 mySQL 连接的隔离级别:  

   ```mysql
   set  transaction isolation level read committed;
   ```

3. 设置数据库系统的全局的隔离级别:

   ```mysql
   set global transaction isolation level read committed;
   ```


### 09-DAO及其子类

#### 9.1 BaseDAO.java

```java
/**
 * DAO：data(base) access object
 * @Description 封装了针对数据表的通用的操作
 * @Author oo
 * @Version
 * @Date 2020-12-19 17:14
 */
public abstract class BaseDAO<T> {

    private  Class<T> clazz = null;

    {
        //获取当前BaseDAO的子类继承的弗雷中的泛型
        Type genericSuperclass = this.getClass().getGenericSuperclass();
        ParameterizedType paramType = (ParameterizedType) genericSuperclass;
        Type[] typeArguments = paramType.getActualTypeArguments();//获取父类的泛型参数
        clazz = (Class<T>) typeArguments[0];//泛型的第一个参数
    }

    //通用的增删改操作  ----version2.0
    public int update(Connection conn, String sql, Object ...args){//sql中占位符的个数应该与可变形参args的个数一致
        PreparedStatement ps = null;
        try {
            ps = conn.prepareStatement(sql);
            for (int i=0;i<args.length;i++)
            {
                ps.setObject(i+1,args[i]);//注意i+1
            }
            return ps.executeUpdate();
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(null,ps);
        }
        return 0;
    }

    //通用的查询操作，用于返回数据表中的一条记录(version 2.0:考虑上事务)
    public T getInstance(Connection conn,String sql,Object ...args) {
        PreparedStatement ps = null;
        ResultSet rs = null;
        try {
            ps = conn.prepareStatement(sql);
            for (int i=0;i<args.length;i++) {
                ps.setObject(i + 1, args[i]);
            }
            rs = ps.executeQuery();
            ResultSetMetaData rsmd = rs.getMetaData();
            int columnCount = rsmd.getColumnCount();
            if(rs.next()){
                T t = clazz.newInstance();
                for (int i=0;i<columnCount;i++) {
                    Object columnValue = rs.getObject(i + 1);
                    String columnLabel = rsmd.getColumnLabel(i + 1);
                    Field field = clazz.getDeclaredField(columnLabel);
                    field.setAccessible(true);
                    field.set(t, columnValue);
                }
                return t;
            }

        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(null,ps,rs);
        }
        return null;
    }

    //通用的查询操作，用于返回数据表中的多条记录(version 2.0:考虑上事务)
    public List<T> getForList(Connection conn,String sql, Object ...args){
        PreparedStatement ps = null;
        ResultSet rs = null;
        try {
            ps = conn.prepareStatement(sql);
            for (int i=0;i<args.length;i++) {
                ps.setObject(i + 1, args[i]);
            }
            rs = ps.executeQuery();
            ResultSetMetaData rsmd = rs.getMetaData();
            int columnCount = rsmd.getColumnCount();
            //创建集合对象
            ArrayList<T> list = new ArrayList<T>();
            while (rs.next()){
                T t = clazz.newInstance();
                for (int i=0;i<columnCount;i++) {
                    Object columnValue = rs.getObject(i + 1);
                    String columnLabel = rsmd.getColumnLabel(i + 1);
                    Field field = clazz.getDeclaredField(columnLabel);
                    field.setAccessible(true);
                    field.set(t, columnValue);
                }
                list.add(t);
            }
            return list;
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(null,ps,rs);
        }
        return null;
    }
//  用于查询特殊值
    public <E> E getValue(Connection conn,String sql,Object ...args) {
        PreparedStatement ps = null;
        ResultSet rs = null;
        try {
            ps = conn.prepareStatement(sql);
            for (int i = 0; i < args.length; i++) {
                ps.setObject(i + 1, args[i]);
            }
            rs = ps.executeQuery();
            if (rs.next()) {
                return (E) rs.getObject(1);
            }
            JDBCUtils.closeResource(null, ps, rs);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(null,ps,rs);
        }
        return null;
    }
}
```

#### 9.2 CustomerDAO.java

```java
/**
 * 此接口用于规范于customers表的常用操作
 */

public interface CustomerDAO {

    /**
     * 将cust对象添加到数据库中
     * @param conn
     * @param cust
     */
    void insert(Connection conn, Customer cust);

    /**
     * 根据指定的id删除表中的一条记录
     * @param conn
     * @param id
     */
    void deleteById(Connection conn, int id);

    /**
     * 针对内存中的cust对象，去修改数据表中指定的记录
     * @param conn
     * @param cust
     */
    void update(Connection conn, Customer cust);

    /**
     * 针对指定的id查询得到对应的customer对象
     * @param conn
     * @param id
     */
    Customer getCustomerById(Connection conn,int id);

    /**
     * 查询表中的所有记录构成的集合
     * @param conn
     * @return
     */
    List<Customer> getAll(Connection conn);

    /**
     * 返回数据表中的数据的条目数
     * @param conn
     * @return
     */
    Long getCount(Connection conn);

    /**
     * 返回数据表中最大的生日
     * @param conn
     * @return
     */
    Date getMaxBirth(Connection conn);
}
```

#### 9.3 CustomerDAOImp.java

```java
/**
 * @Description
 * @Author oo
 * @Version
 * @Date 2020-12-19 19:13
 */
public class CustomerDAOImpl extends BaseDAO<Customer> implements CustomerDAO {


    @Override
    public void insert(Connection conn, Customer cust) {
        String sql = "insert into customers(name,email,birth) values(?,?,?)";
        update(conn,sql,cust.getName(),cust.getEmail(),cust.getBirth());
    }

    @Override
    public void deleteById(Connection conn, int id) {
        String sql = "delete from customers where id = ?";
        update(conn,sql,id);
    }

    @Override
    public void update(Connection conn, Customer cust) {
        String sql = "update customers set name=?,email=?,birth=? where id=?";
        update(conn,sql,cust.getName(),cust.getEmail(),cust.getBirth(),cust.getId());
    }

    @Override
    public Customer getCustomerById(Connection conn, int id) {
        String sql = "select id,name,email,birth from customers where id=?";
        Customer cust = getInstance(conn,sql, id);

        return cust;
    }

    @Override
    public List<Customer> getAll(Connection conn) {
        String sql = "select id,name,email,birth from customers";
        List<Customer> list = getForList(conn, sql);
        return list;
    }

    @Override
    public Long getCount(Connection conn) {
        String sql = "select count(*) from customers";
        return getValue(conn,sql);
    }

    @Override
    public Date getMaxBirth(Connection conn) {
        String sql = "select max(birth) from customers";
        return getValue(conn,sql);
    }
}
```

#### 9.4 总结

1. 获取连接

   ```java
   Connection conn = JDBCUtils.getConnection();	//方式1：手动获取连接 方式2：数据库连接池
   
   conn.setAutoCommit(false);			//体现事务
   ```

2. 如下的多个DML操作，作为一个事务出现：

   操作1：需要使用通用的增删改查操作			//通用的增删改查如何实现

   操作2：需要使用通用的增删改查操作			//方式一：手动使用preparedStatement实现

   .......																	//方式二：使用dbutils.jar中的QueryRunner类

   操作n：需要使用通用的增删改查操作

   ```java
   conn.commit();
   ```

3. 如果出现异常，则：

   ```java
   conn.rollback();
   ```

4. 关闭资源

   ```java
   JDBCUtils.closeResource(...,...,...);	//方式一：手动关闭资源   方式二：DbUtils类的关闭实现方法
   ```

### 10-数据库连接池

#### 10.1 传统连接的问题

这种模式开发，存在的问题:

- 普通的JDBC数据库连接使用 DriverManager 来获取，每次向数据库建立连接的时候都要将 Connection 加载到内存中，再验证用户名和密码(得花费0.05s～1s的时间)。需要数据库连接的时候，就向数据库要求一个，执行完成后再断开连接。这样的方式将会消耗大量的资源和时间。**数据库的连接资源并没有得到很好的重复利用。**若同时有几百人甚至几千人在线，频繁的进行数据库连接操作将占用很多的系统资源，严重的甚至会造成服务器的崩溃。
- **对于每一次数据库连接，使用完后都得断开。**否则，如果程序出现异常而未能关闭，将会导致数据库系统中的内存泄漏，最终将导致重启数据库。（回忆：何为Java的内存泄漏？）
- **这种开发不能控制被创建的连接对象数**，系统资源会被毫无顾及的分配出去，如连接过多，也可能导致内存泄漏，服务器崩溃。 

#### 10.2 如何解决传统开发中的数据库连接问题

使用数据库连接池。

#### 10.3 使用数据库连接池的好处

**1. 资源重用**

由于数据库连接得以重用，避免了频繁创建，释放连接引起的大量性能开销。在减少系统消耗的基础上，另一方面也增加了系统运行环境的平稳性。

**2. 更快的系统反应速度**

数据库连接池在初始化过程中，往往已经创建了若干数据库连接置于连接池中备用。此时连接的初始化工作均已完成。对于业务请求处理而言，直接利用现有可用连接，避免了数据库连接初始化和释放过程的时间开销，从而减少了系统的响应时间

**3. 新的资源分配手段**

对于多应用共享同一数据库的系统而言，可在应用层通过数据库连接池的配置，实现某一应用最大可用数据库连接数的限制，避免某一应用独占所有的数据库资源

**4. 统一的连接管理，避免数据库连接泄漏**

在较为完善的数据库连接池实现中，可根据预先的占用超时设定，强制回收被占用连接，从而避免了常规数据库连接操作中可能出现的资源泄露

> 简单总结：
>
> 1. 提高程序的响应速度(减少创建连接相应的时间)
> 2. 降低资源的消耗(可以重复使用)
> 3. 便于连接的管理

#### 10.4 实现的方式 

1. **DBCP** 是Apache提供的数据库连接池。tomcat 服务器自带dbcp数据库连接池。**速度相对c3p0较快**，但因自身存在BUG，Hibernate3已不再提供支持。
2. **C3P0** 是一个开源组织提供的一个数据库连接池，**速度相对较慢，稳定性还可以。**hibernate官方推荐使用
3. Proxool 是sourceforge下的一个开源项目数据库连接池，有监控连接池状态的功能，**稳定性较c3p0差一点**
4. BoneCP 是一个开源组织提供的数据库连接池，速度快
5. **Druid** 是阿里提供的数据库连接池，据说是集DBCP 、C3P0 、Proxool 优点于一身的数据库连接池，但是速度不确定是否有BoneCP快

#### 10.5 C3P0

1. 导入jar包

   ![image-20201220181229297](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220181229297.png)

2. 测试连接的代码

   ```java
   /**
    * 使用C3P0的数据库连接池技术
    */
   //连接池只需要提供一个
   private static ComboPooledDataSource cpds = new ComboPooledDataSource("helloc3p0");
   public static Connection getConnection1() throws SQLException {
       Connection conn = cpds.getConnection();
       return conn;
   }
   ```

3. 配置文件

   ```java
   <?xml version="1.0" encoding="UTF-8"?>
   
       <c3p0-config>
           <named-config name="helloc3p0">
               <!--提供获取连接的4个基本信息-->
               <property name="driverClass">com.mysql.cj.jdbc.Driver</property>
               <property name="jdbcUrl">jdbc:mysql://localhost:3306/test?characterEncoding=utf8&amp;useSSL=false&amp;serverTimezone=UTC&amp;rewriteBatchedStatements=true</property>
               <property name="user">root</property>
               <property name="password">*****</property>
   
               <!--提供数据库连接池管理的4个基本信息-->
   
               <!-- 当数据库连接池中的连接数不够时，c3p0一次性向数据库服务器申请的连接数 -->
               <property name="acquireIncrement">5</property>
               <!-- c3p0数据库连接池中初始化时的连接数 -->
               <property name="initialPoolSize">10</property>
               <!-- c3p0数据库连接池中维护的最少的连接数 -->
               <property name="minPoolSize">10</property>
               <!-- c3p0数据库连接池中维护的最多的连接数 -->
               <property name="maxPoolSize">100</property>
               <!-- c3p0数据库连接池中维护的最多的statement的个数 -->
               <property name="maxStatements">50</property>
               <!-- 每个连接中可以最多使用的Statement的个数 -->
               <property name="maxStatementsPerConnection">2</property>
   
           </named-config>
       </c3p0-config>
   ```

#### 10.6 DBCP

1. 导入jar包

   ![image-20201220181648502](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220181648502.png)

2. 测试连接的代码

   ```java
    /**
        * 使用DBCP数据库连接池技术获取数据库连接
        * @return
        * @throws Exception
        */
       //创建一个DBCP数据库连接池
       private static DataSource source;
       static {
           try {
               Properties pros = new Properties();
   //        InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("dbcp.properties");
               FileInputStream is = new FileInputStream(new File("src/dbcp.properties"));
               pros.load(is);
               //创建DBCP数据库连接池
               source = BasicDataSourceFactory.createDataSource(pros);
           } catch (Exception e) {
               e.printStackTrace();
           }
       }
   public static Connection getConnection2() throws Exception {
   
           Connection conn = source.getConnection();
           System.out.println(conn);
           return conn;
       }
   ```

3. 配置文件

   ```java
   driverClassName=com.mysql.cj.jdbc.Driver
   url=jdbc:mysql://localhost:3306/test?characterEncoding=utf8&useSSL=false&serverTimezone=UTC&rewriteBatchedStatements=true
   username=root
   password=****
   initialSize=10
   ```

#### 10.7 Druid(最常用)

1. 导入jar包

   ![image-20201220181945760](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220181945760.png)

2. 测试连接的代码

   ```java
   /**
        * 使用Druid数据库连接池技术
        */
   
       private  static DataSource source1;
       static {
           Properties pros = new Properties();
           InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("druid.properties");
           try {
               pros.load(is);
               //获取Druid数据库连接池
               source1 = DruidDataSourceFactory.createDataSource(pros);
           } catch (Exception e) {
               e.printStackTrace();
           }
       }
       public static Connection getConnection3() throws Exception {
           Connection conn = source1.getConnection();
           return conn;
       }
   ```

3. 配置文件

   ```java
   #等号最好不要有空格，否则会产生歧义，比如说密码是否包括空格呢？
   url=jdbc:mysql://localhost:3306/test?characterEncoding=utf8&useSSL=false&serverTimezone=UTC&rewriteBatchedStatements=true
   username=root
   password=****
   driverClassName=com.mysql.cj.jdbc.Driver
   
   initialSize=10
   maxActive=10
   ```

### 11-DBUtils提供的jar包实现CRUD操作

##### 11.1 导入jar包

![image-20201220182122531](C:\Users\蔲丫丫\AppData\Roaming\Typora\typora-user-images\image-20201220182122531.png)

##### 11.2 使用现有的jar中的QueryRunner测试增、删、改的操作

```java
//测试插入
    @Test
    public  void testInsert() {

        Connection conn = null;
        try {
            QueryRunner runner = new QueryRunner();
            conn = JDBCUtils.getConnection3();
            String sql = "insert into customers(name,email,birth) values(?,?,?)";
            int insertCount = runner.update(conn, sql, "蔡徐坤", "caixukun@126.com", "1999-09-09");
            System.out.println("添加了"+insertCount+"条记录");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(conn,null);
        }
    }
```

##### 11.3 使用现有的jar中的QueryRunner测试查询的操作

```java
//测试查询

    /**
     * BeanHandler：是ResultSetHandler接口的实现类，用于封装表中的一条记录
     * @throws Exception
     */
    @Test
    public  void testQuery1() {
        Connection conn = null;
        try {
            QueryRunner runner = new QueryRunner();
            conn = JDBCUtils.getConnection3();
            String sql = "select id,name,email,birth from customers where id = ? ";
            BeanHandler<Customer> handler = new BeanHandler<>(Customer.class);
            Customer customer = runner.query(conn, sql, handler, 25);
            System.out.println(customer);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(conn,null);
        }
    }

    /**
     * BeanListHandler：是ResultSetHandler接口的实现类，用于封装表中的多条记录构成的集合
     * @throws Exception
     */
    @Test
    public  void testQuery2() throws Exception {
        Connection conn = null;
        try {
            QueryRunner runner = new QueryRunner();
            conn = JDBCUtils.getConnection3();
            String sql = "select id,name,email,birth from customers where id < ? ";
            BeanListHandler<Customer> handler = new BeanListHandler<>(Customer.class);
            List<Customer> customerList = runner.query(conn, sql, handler, 25);
            customerList.forEach(System.out::println);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(conn,null);
        }
    }

    /**
     * MapHandler：是ResultSetHandler接口的实现类，对应表中的一条记录，将字段及相应字段的值作为map中的键和值
     * @throws Exception
     */
    @Test
    public  void testQuery3() {
        Connection conn = null;
        try {
            QueryRunner runner = new QueryRunner();
            conn = JDBCUtils.getConnection3();
            String sql = "select id,name,email,birth from customers where id = ? ";
            MapHandler handler = new MapHandler();
            Map<String,Object> map = runner.query(conn, sql, handler, 25);
            System.out.println(map);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(conn,null);
        }
    }

    /**
     * MapListHandler：是ResultSetHandler接口的实现类，对应表中的多条记录，将字段及相应字段的值作为map中的键和值，将这些map添加到List中
     */
    @Test
    public  void testQuery4() {
        Connection conn = null;
        try {
            QueryRunner runner = new QueryRunner();
            conn = JDBCUtils.getConnection3();
            String sql = "select id,name,email,birth from customers where id = ? ";
            MapListHandler handler = new MapListHandler();
            List<Map<String, Object>> mapList = runner.query(conn, sql, handler, 25);
            mapList.forEach(System.out::println);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(conn,null);
        }
    }

    /**
     * ScalarHandler：是ResultSetHandler接口的实现类，用于查询特殊值
     */
    @Test
    public  void testQuery5() {
        Connection conn = null;
        try {
            QueryRunner runner = new QueryRunner();
            conn = JDBCUtils.getConnection3();
            String sql = "select count(*) from customers";
            ScalarHandler handler = new ScalarHandler();
            Long count = (Long) runner.query(conn, sql, handler);
            System.out.println(count);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(conn,null);
        }
    }

    @Test
    public  void testQuery6() {
        Connection conn = null;
        try {
            QueryRunner runner = new QueryRunner();
            conn = JDBCUtils.getConnection3();
            String sql = "select max(birth) from customers";
            ScalarHandler handler = new ScalarHandler();
            Date max = (Date) runner.query(conn, sql, handler);
            System.out.println(max);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(conn,null);
        }
    }

    /**
     * 自定义ResultSetHandler实现类
     */
    @Test
    public  void testQuery7() {
        Connection conn = null;
        try {
            QueryRunner runner = new QueryRunner();
            conn = JDBCUtils.getConnection3();
            String sql = "select id,name,email,birth from customers where id = ?";
            ResultSetHandler<Customer> handler = new ResultSetHandler<Customer>() {
                @Override
                public Customer handle(ResultSet resultSet) throws SQLException {
                    if(resultSet.next()){
                        int id = resultSet.getInt(1);
                        String name = resultSet.getString(2);
                        String email = resultSet.getString(3);
                        Date birth = resultSet.getDate(4);
                        Customer customer = new Customer(id,name,email,birth);
                        return customer;
                    }
                    return null;
                }
            };
            Customer customer = runner.query(conn, sql, handler, 12);
            System.out.println(customer);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JDBCUtils.closeResource(conn,null);
        }
    }
```

##### 11.4 使用dbutils.jar包中的dbutils工具类实现连接等资源的关闭

```java
 public static void closeResource1(Connection conn, Statement ps, ResultSet rs){
//        try {
//            DbUtils.close(conn);
//        } catch (SQLException e) {
//            e.printStackTrace();
//        }
//        try {
//            DbUtils.close(ps);
//        } catch (SQLException e) {
//            e.printStackTrace();
//        }
//        try {
//            DbUtils.close(rs);
//        } catch (SQLException e) {
//            e.printStackTrace();
//        }
        DbUtils.closeQuietly(conn,ps,rs);
    }
```