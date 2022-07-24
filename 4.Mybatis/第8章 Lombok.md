# 第八章 Lombok

Lombok是一款Java开发插件，可以通过注解来帮助我们简化和消除一些必须有但显得很臃肿的Java代码，比如常见的Getter、Setter、toString()、构造函数等等（POJO）。lombok不仅方便编写，同时也让我们的代码更简洁。

缺点是不支持参数构造器的重载。

所以使用要有取舍

## 8.1 可用注解

@Getter

@Setter

@FieldNameConstants

@ToString：toString方法

@EqualsAndHashCode

@AllArgsConstructor：全参构造器

@RequiredArgsConstructor

@NoArgsConstructor：无参构造器

@Log, @Log4j, @Log4j2, @Slf4j, @XSlf4j, @CommonsLog, @JBossLog, @Flogger, @CustomLog

@Data：get和set方法

@Builder

@SuperBuilder

@Singular

@Delegate

@Value

@Accessors

@Wither

@With

@SneakyThrows

@val

@var

## 8.2 使用步骤

1、在IDEA中安装Lombok插件

2、导入jar包

```xml
<!-- https://mvnrepository.com/artifact/org.projectlombok/lombok -->
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.20</version>
</dependency>
```

3、在实体类加注解即可。

## 8.3 示例

@Data：无参构造器、get、set、toString、hashcode、equal

```java
@Data
public class User {
    private int id;
    private String name;
    private String password;
  
    //有了@Data，就不再需要写get、set等等之类的了
    //有参构造器还是得自己写
}
```

