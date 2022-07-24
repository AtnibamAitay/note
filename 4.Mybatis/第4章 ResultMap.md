# 第四章 ResultMap

## 4.1 要解决的问题

pojo类中的属性名和数据库中的字段名不一致

比如pojo中为

```java
private String pwd;
```

数据库中的字段名为password

## 4.2 解决办法

### 4.2.1 方法一

为列名指定别名 , 别名和java实体类的属性名一致

```xml
<select id="selectUserById" resultType="User">
  select id,name,pwd as password from user where id = #{id}
</select>
```

### 4.2.2 方法二

使用结果集映射 -> ResultMap 【推荐】

将 resultType="User"

```xml
<select id="getUserById" resultType="User">
  select * from mybatis.user where id = #{id}
</select>
```

改成resultMap=""，值为自己取的名字UserMap

```xml
<select id="getUserById" resultMap="UserMap">
  select * from mybatis.user where id = #{id}
</select>
```

还需要在select标签上面加一个resultMap标签进行映射

```xml
<!-- type中的User是扫描过后的，见2.6 mappers（映射器） -->
<resultMap id="UserMap" type="User">
  <!-- column数据库中的字段，property实体类中的属性 -->
  <!-- 啥不一样映射啥就行 -->
  <result column="pwd" property="password"/>
</resultMap>
```

## 4.3 resultMap

resultMap 元素是 MyBatis 中最重要最强大的元素，其设计思想是，对简单的语句做到零配置，对于复杂一点的语句，只需要描述语句之间的关系就行了。