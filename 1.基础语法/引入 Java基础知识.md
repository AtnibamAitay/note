# 引入 Java基础知识

## 0.1 各种缩写的含义

        JavaSE：标准版。

        JavaEE：企业版。

        JavaME：微型版。

        JVM（Java Virtual Machine，Java虚拟机）使Java实现跨平台性。

        JRE（Java Runtime Environment，Java运行环境）包括Jvm、Java核心类库和支持文件，要运行Java程序，就必须安装这个。

        JDK（Java Development Kit，Java开发工具包）是开发Java用的，包括了Java开发工具[包括编译工具（javac.exe）和打包工具（jar.exe）]和JRE。

        OS（Operation System，操作系统）

## 0.2 常用DOS命令

        非图形化界面交互的程序可以通过命令行方式（cmd）使用dos命令进行交互。

        常见命令有：

| 操作     | 说明                           |
| -------- | ------------------------------ |
| dir      | 列出当前目录下的文件以及文件夹 |
| md       | 创建目录                       |
| rd       | 删除目录                       |
| cd       | 进入指定目录                   |
| cd..     | 退回到上一级目录               |
| cd/      | 退回到根目录                   |
| del      | 删除文件                       |
| exit     | 退出dos命令行                  |
| 磁盘名字 | 切换到指定磁盘                 |

## 0.3 Java程序开发运行流程

​	编写程序（Java源程序）→编译程序（Java字节码文件）→运行程序

​		编译：javac 文件名.java

​		执行：java 类名

## 0.4 其他

​	在一个java源文件中可以声明多个class，但只能有一个类声明为public，这个类是与源文件名同名的类。

​	每个执行语句都以“;”结尾。

​	编译出来会生成一个或多个字节码文件，字节码文件的文件名与java源文件中的类名相同