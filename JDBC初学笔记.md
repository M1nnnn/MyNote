# 将date类型的数据导入MySQL错误

## java.util.Date cannot be cast to java.sql.Date

```java
 java.util.Date date = sdf.parse("2001-03-28");
 //ps.setDate(3, (java.sql.Date) new Date(date.getTime()));//错误示例
ps.setDate(3,  new java.sql.Date(date.getTime()));//正确导入
```

# 连接Mysql8.0驱动路径

```
driverClass=com.mysql.cj.jdbc.Driver
```

## 连接MySQL5.0驱动路径

```
driverClass=com.mysql.jdbc.Driver
```

# Mysql配置文件区别和注意事项

com.mysql.jdbc.Driver 是 mysql-connector-java 5中的， 
com.mysql.cj.jdbc.Driver 是 mysql-connector-java 6以及以上中的

## 在使用com.mysql.jdbc.Driver时，配置是需要下面这样的：

```java
driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/test?useUnicode=true&characterEncoding=utf8&useSSL=false
username=root
password=
```

## 在使用com.mysql.cj.jdbc.Driver时，则是需要下面这样的配置的：

```java
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/test?serverTimezone=UTC&?useUnicode=true&characterEncoding=utf8&useSSL=false
username=root
password=
```

## **注意：**

需要指定时区（serverTimezone=UTC）和 使用SSL （useSSL=false）

在设定时区的时候，如果设定serverTimezone=UTC，会比中国时间早8个小时，如果在中国，可以选择Asia/Shanghai或者Asia/Hongkong，像下面这样配置：

```java
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/test?serverTimezone=Asia/Shanghai&?useUnicode=true&characterEncoding=utf8&useSSL=false
username=root
password=
```

# [为什么使用Junit Test而不用普通java main方法来完成测试?]

## [(https://www.cnblogs.com/super-chao/p/6066706.html)

　　因为在程序里边，一个接口对应一个实现方法，而在接口中常常会定义相关的很多方法，所以在测试的时候，如果都在main方法里边进行测试，main方法就会显得臃肿，而且不便于以后其他人测试以及查看测试数据，用Junit Test测试的话，一个方法对应一个测试方法，简单明了，也方便别人查看测试方法以及测试数据。

 

　　如果你的类里有多个方法，用main方法测试的话就很不方便，想测试全部方法的话就得把测试代码全部写到main里，或者你测一个重写一次。且更重要的是，这样会使测试代码与运行逻辑代码混在一起，不规范。
　　在一个正规的java项目中（尤其是使用了SSH之类的框架），几乎是不会写main方法的，写了就是无用代码，会被经理骂……
　　使用junit就方便多了，这是[单元测试](http://www.baidu.com/s?wd=单元测试&tn=44039180_cpr&fenlei=mv6quAkxTZn0IZRqIHckPjm4nH00T1YvnjfLuyN9PWw9PjwbPWKh0ZwV5Hcvrjm3rH6sPfKWUMw85HfYnjn4nH6sgvPsT6KdThsqpZwYTjCEQLGCpyw9Uz4Bmy-bIi4WUvYETgN-TLwGUv3EPHfsnW6vPj01)，你想测哪个方法就写一个对应的测试方法，然后用junit运行。每个方法之间是独立的，非常灵活。而且测试方法一般不会直接写在原类中，而是单独的测试类，这样测试代码就完全与逻辑代码分开了。
　　如果使用了maven之类的工具来管理项目，则junit的好处又会进一步体现出来：你可以编写好一大批测试类，然后用maven的一个简单命令来自动执行，想想看，全部自动测试，且测试结果自动生成文档，方便吧。
　　其实junit一点也不难学，用一两次就大体懂了。祝你学习顺利

# Mysql表名是关键字，Java操作时报错

## 解决办法

***报错信息：sql语句报错*j**ava.sql.SQLSyntaxErrorException: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ***

**关键字两边加上``**

#  JDBC连接数据库出现No value specified for parameter 1

## **1>**没有填充占位符

# JDBC连接数据库出现java.lang.NoSuchFieldException: order_id

## 原因：表的字段名和类的属性名不一致

### 解决方法：在sql语句中对字段名起别名

仍然报错原因：

```
//获取列名：相当于别名没起作用，两者仍然不一致
String columnName = metaData.getColumnName(i + 1);
```

```
// 获取列的别名
String columnName = metaData.getColumnLabel(i+1);
```

# 循环中写入return，break,continue语句输出错误

## **Return**

在循环中，Return语句，作用是结束本次循环，将函数调用栈弹栈，恢复现场。

说的简单点儿就是结束当前的函数，返回函数执行结果，回到本函数被调用处继续执行。

## **Break 语句**

在循环中，关键词Break，作用是跳出循环，一般有以下两种用法：

1. 当 break 语句出现在一个循环内时，循环会立即终止，且程序流将继续执行紧接着循环的下一条语句。
2. 它可用于终止 switch 语句中的一个 case。

如果使用的是嵌套循环，break 语句会停止执行最内层的循环，然后开始执行该块之后的下一行代码。

**注意：**

1. break语句对if-else的条件语句不起作用。

2. 在多层循环中，一个break语句只向外跳一层。

3. 由于它是用来退出循环或者switch语句的, 所以只有当它出现在这些语句的时候, 这种形式的break语句才是合法的。


## Continue 语句

C 语言中的 continue 语句有点像 break 语句，所不同的是，它不是强制终止，continue 会跳过当前循环中的代码，强迫开始下一次循环迭代。

对于 for 循环，continue 语句执行后，**自增语句仍然会执行**。

对于 while 和 do…while 循环，continue 语句**重新执行条件判断语句**。

# IDEA中单元测试使用Scanner控制台无法输入

##  1/打开IDEA安装根目录下的bin文件夹

找到idea.exe.vmoptions和idea64.exe.vmoptions这两个文件

用记事本或者EditPlus 或者直接在idea中编辑这两个文件
添加`-Deditable.java.test.console=true`
注意：是两个文件都要添加

## 2/在idea内的help中找到idea64.exe.vmoptions

```
在idea64.exe.vmoptions文件的末尾加入以下内容：
-Deditable.java.test.console=true
```

# Java中list集合为空或为null的区别是什么

## **1.判断一个list集合是否为空**

在Java中，list集合为空（集合中无元素），还是为null，这是两码事。

举例，我有一个空着的水杯（list），而你没有，那你是null，我的size为0。你想装水就需要自己去买个水杯（new ArrayList();），但是我就可以直接装水（list.add(水)）。你要是没有杯子直接倒水，水就流出去啦（空指针异常）。

## **2.那么，我们什么时候用null，什么时候用isEmpty()或list.size()呢？**

isEmpty() 或者(list.size() == 0)用于判断List内容是否为空，即集合中一个元素也没有， 但是使用isEmpty()和size()的前提是，list是一个空集合，而不是null，所以为了避免异常，建议在使用或赋值list集合之前，做一次空集合创建处理，进行内存空间分配，即：List list = new ArrayList();

## **3.list.isEmpty()和list.size()==0 没有区别**

isEmpty()判断有没有元素，而size()返回有几个元素，如果判断一个集合有无元素，建议用isEmpty()方法，看起来清晰明了。

## **4.list等于null，可理解为没有对list集合分配内存空间，实际上压根就不存在。**

### 判断List集合为空或null

**判断List集合是否为空**

Java中，判断List集合是否为空与是否为null并不相同

新建List对象，默认是为空，即没有数据，而不是null



# 数据一旦提交，就不可回滚。

## 数据什么时候意味着提交？

当一个连接对象被创建时，默认情况下是自动提交事务：每次执行一个 SQL 语句时，如果执行成功，就会
向数据库自动提交，而不能回滚。
关闭数据库连接，数据就会自动的提交。如果多个操作，每个操作使用的是自己单独的连接，则无法保证
事务。即同一个事务的多个操作必须在同一个连接下。

## JDBC程序中为了让多个 SQL 语句作为一个事务执行：

调用 Connection 对象的 setAutoCommit(false); 以取消自动提交事务
在所有的 SQL 语句都成功执行后，调用 commit(); 方法提交事务
在出现异常时，调用 rollback(); 方法回滚事务
若此时 Connection 没有被关闭，还可能被重复使用，则需要恢复其自动提交状态
setAutoCommit(true)。尤其是在使用数据库连接池技术时，执行close()方法前，建议恢复自动提交状
态。

# java.lang.NoClassDefFoundError: org/apache/commons/logging/LogFactory

## 运行时报错

下载：[commons-logging-1.1.1.jar下载及Maven、Gradle引入代码，pom文件及包内class -时代Java (nowjava.com)](https://nowjava.com/jar/detail/m02262204/commons-logging-1.1.1.jar.html)

导入commons-logging.jar包，完美解决

# DBCP连接池所用到的两个jar包下载地址

## **commons-dbcp.jar：**

http://commons.[apache](https://so.csdn.net/so/search?q=apache&spm=1001.2101.3001.7020).org/proper/commons-dbcp/download_dbcp.cgi

## **commons-pool.jar：**

http://commons.apache.org/proper/commons-pool/download_pool.cgi

# C3P0jar包

### **：https://sourceforge.net/**

# druid 的jar包

[Central Repository: com/alibaba/druid (maven.org)](https://repo1.maven.org/maven2/com/alibaba/druid/)

## useSSL=false和true的区别:

​    SSL(Secure Sockets Layer 安全套接字协议)，在mysql进行连接的时候,如果mysql的版本是5.7之后的版本必须要加上useSSL=false,mysql5.7以及之前的版本则不用进行添加useSSL=false，会默认为false，一般情况下都是使用useSSL=false，尤其是在将项目部署到linux上时，一定要使用useSSL=false！！！，useSSL=true是进行安全验证，一般通过证书或者令牌什么的，useSSL=false就是通过账号密码进行连接，通常使用useSSL=false！！！<!--没有报错，但是看见了就搜了一下-->

# Mysql的占位符

- #{}：会将其替换为？为了防止sql注入
- ${}：拼sql会存在sql注入
- 使用时机
  - 传递参数的时候#{}
  - 在表名和列名不固定的时候${} 存在sql注入

- 特殊字符的处理
  - CDATA区
  - 转义字符
