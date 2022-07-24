# 第三章 作用域（Scope）和生命周期

错误的使用作用域和生命周期会导致严重的并发问题。

## 2.6.1 Mybatis的执行过程

![图片](图表/640)

### 2.6.2 作用域理解

#### 2.6.2.1 SqlSessionFactoryBuilder

作用在于创建 SqlSessionFactory，创建成功后，SqlSessionFactoryBuilder 就失去了作用。因此 SqlSessionFactoryBuilder 实例的最佳作用域是方法作用域（也就是局部方法变量）。

#### 2.6.2.2 SqlSessionFactory

可被认为是一个数据库连接池，它的作用是创建 SqlSession 接口对象。因为 MyBatis 的本质就是 Java 对数据库的操作，所以 SqlSessionFactory 的生命周期存在于整个 MyBatis 的应用之中，一旦创建，就要长期保存，直至不再使用 MyBatis 应用，所以可以认为 SqlSessionFactory 的生命周期就等同于 MyBatis 的应用周期。

由于 SqlSessionFactory 是一个对数据库的连接池，所以它占据着数据库的连接资源。若创建多个，那么就存在多个数据库连接池，这样不利于对数据库资源的控制，也会导致数据库连接资源被消耗光，出现系统宕机等情况。因此在一般的应用中我们往往希望 SqlSessionFactory 作为一个单例，让它在应用中被共享。

SqlSessionFactory 的最佳作用域是应用作用域。

#### 2.6.2.3 SqlSession

相当于一个数据库连接（Connection 对象），可在一个事务里执行多条 SQL，然后通过它的 commit、rollback 等方法，提交或者回滚事务。所以它应该存活在一个业务请求中，处理完整个请求后，应该关闭这条连接，让它归还给 SqlSessionFactory，否则数据库资源就很快被耗费精光，系统就会瘫痪，所以用 try...catch...finally... 语句来保证其正确关闭。

SqlSession 的最佳的作用域是请求或方法作用域。