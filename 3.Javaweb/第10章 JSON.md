# 第10章 JSON

## 10.1 JSON

JSON (JavaScript Object Notation) 是一种轻量级的数据交换格式。 易于人阅读和编写。同时也易于机器解析和生成。 它基于 JavaScript Programming Language, Standard ECMA-262 3rd Edition - December 1999 的一 个子集。 JSON 采用完全独立于语言的文本格式，但是也使用了类似于 C 语言家族的习惯（包括 C, C++, C#, Java, JavaScript, Perl, Python 等）。 这些特性使 JSON 成为理想的数据交换语言。

轻量级是与xml作比较

数据交换指的是客户端和服务器之间的业务数据的传递格式。

### 10.1.1 JSON 在 JavaScript 中的使用

#### 10.1.1.1 JSON的定义

JSON是由键值对组成，并且由花括号（大括号）包围，每个键由引号引起来，键和值之间使用冒号进行分割，多组键值对之间进行逗号进行分隔。

json.html

```json
var jsonObj = {
	"key1":12,
	"key2":"abc",
	"key3":true,
	"key4":[11,"arr",false],
	"key5":{
		"key5_1" : 551,
		"key5_2" : "key5_2_value"
	},
	"key6":[{
		"key6_1_1":6611,
		"key6_1_2":"key6_1_2_value"
	},{
		"key6_2_1":6621,
		"key6_2_2":"key6_2_2_value"
	}]
};
```

#### 10.1.1.2 JSON 对象的访问

JSON 本身是一个对象，里面的 key 就是对象的属性。访问一个对象的属性，只需要用【对象名.属性名】的方式访问即可。

```json
alert(jsonObj.key1);
```

因此，访问JSON中的JSON对象可以

```json
alert(jsonObj.key5.key5_1);
```

访问JSON中的数组时

```json
alert(jsonObj.key4);  //输出数组[11,"arr",false]
```

还可以输出JSON对象

```json
alert( jsonObj.key6 );  //输出 [object Object],[object Object]
```

### 10.1.2 JSON的两种常用方法

JSON的存在有两种形式，一种是对象的形式，叫Json对象，一种是字符串的形式，叫Json字符串。

JSON 对象和字符串对象的互转

一般操作Json中的数据时，需要Json对象的格式

一般要在客户端和服务器之间进行数据交换时，使用Json字符串

| 方法                      | 功能                                 |
| ------------------------- | ------------------------------------ |
| JSON.stringify( json );   | 把一个 json 对象转换成为 json 字符串 |
| JSON.parse( jsonString ); | 把一个 json 字符串转换成为 json 对象 |

#### 10.1.2.1 转换为字符串

Json.html

```json
// 把json对象转换成为 json字符串
var jsonObjString = JSON.stringify(jsonObj); // 特别像 Java中对象的toString
alert(jsonObjString)
```

输出：

```
{"key1":12,"key2":"abc","key3":true,"key4":[11,"arr",false],"key5":{"key5_1":551,"key5_2":"key5_2_value"},"key6":[{"key6_1_1":6611,"key6_1_2":"key6_1_2_value"},{"key6_2_1":6621,"key6_2_2":"key6_2_2_value"}]}
```

#### 10.1.2.2 转换为对象

Json.html

```json
var jsonObj2 = JSON.parse(jsonObjString);
alert(jsonObj2.key1);
alert(jsonObj2.key2);
```

输出：

```
12
abc
```

### 10.1.3 JSON在Java中的使用

需要导入gson包

#### 10.1.3.1 JavaBean 和 Json 的互转



#### 10.1.3.2 List 和 Json 的互转



#### 10.1.3.3 map 和 Json 的互转