# JDBC

JDBC(Java Database Connectivity)是一个独立于特定数据库管理系统（DBMS）、通用的SQL数据库存取和操作的公共接口（一组API），定义了用来访问数据库的标准Java类库，使用这个类库可以以一种标准的方法、方便地访问数据库资源。

规范：抽象类或接口

JDBC使用步骤

​	前期：准备mysql的驱动包（比如mysql-connector-java-5.1.37-bin.jar）加载到项目中

​	1.加载驱动

​	2.获取连接

​	3.执行增删改查操作

​	4.关闭连接

简单的代码示例：

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import com.mysql.jdbc.Driver;
public class TestConnection{
	public static void main(String[] args) throws SQLException{
//1.加载驱动
DriverManager.registerDriver(new Driver());
//2.获取连接
Connection connection=DriverManager.getConnection("jdbc:mysql://localhost:3306/数据库名","root","数据库密码");
//3.执行数据库操作
//3.1 编写sql语句
//删除
String sql="delect from beauty where id=9";
//3.2 获取执行sql语句的命令对象
//createStatement()命令对象专门用于传送sql命令到数据库服务器
Statement statement = connection.createStatement();
//3.3 使用对象指向执行sql语句
//executeUpdate()能执行增删改语句，并返回受影响的函数
int update=statement.executeUpdate(sql);
//3.4 处理执行结果
System.out.println(update>0?"success":"failure");
//4.关闭连接
statement.close();
	connection.close();
	}
}
```



 

 