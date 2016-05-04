title: Javascript之数据类型
date: 2016-01-10 23:14:26
categories: Javascript
tags:
- Javascript
---
Javascript中有5种基本数据类型Undefined, Null, Boolean, Number, String和一种复杂数据类型Object.

由于Javascript是弱类型语言，所以提供了typeof操作符来检测语言类型。typeof 针对这几种数据类型返回表示不同类型的字符串。

### Undefined
Undefined类型只有一个值undefined。 对于未定义的变量和使用var声明但为进行初始化的变量执行typeof都会返回字符串undefined。

``` javascript
var message;
typeof messsage; //"undefined"
typeof(infomation); //"undefined"
//typeof为操作符，所以在使用typeof的时候可以使用括号，也可以不用
```

### Null
Null类型同样只有一个值null。由于null表示空对象指针，所以对null执行typeof操作会返回object字符串。

``` javascript
typeof(null); //"object"
```
需要注意的是null和undefined的相等性测试会返回true。

```javascript
null == undefined; //true
```
### Boolean
Boolean类型有两个值，true和false。其他所有类型的值都可以转化成与这两个值等价的值。

| Boolean    |     true        | false      |
| ---------- |:---------------:|:----------:|
| String     | 任何非空字符串	    | ""或者''	 |
| Number     | 任何非零数字      | 0或者NaN    |
| Object     | 任何非空对象      | null       |
| Undefined  |                 | undefined	 |


### Number
Number包括整数和浮点数。

除十进制外还支持八进制和十六进制
八进制以0开头，如果其中有数字超过八进制数字(0~7会忽略前面的0当作十进制数。

```javascript
var num1= 072; //58的八进制表示
var num2=079;  //无效八进制数字，解析为十进制数79
```

八进制不能在严格模式下使用。

十六进制以0x开头来表示。
```Javascript
var num1= 0x8; //十六进制的8
var num2=0x2F;  //十六进制的47
```

由于保存浮点数的内存是整数的两倍，如果	小数点后面没有除0以外的任何数字，会被转换成证书保存
```Javascript
var num = 10.000  //被转换成整数10
```

由于精度的问题，浮点数在进行算术运算是会产生误差，比如下面的例子，所以不要对浮点数进行相等性测试

```javascript
0.1 + 0.2          //0.30000000000000004
0.1 + 0.2 == 0.3   //false
```

由于内存的限制，如果运算的数值超过了Javascript的数值范围，会返回Infinity。Infinity表示正无穷大，-Infinity表示负无穷大。
```javascript
Number.MAX_VALUE + Number.MAX_VALUE  //Infinity
Infinity + Number.MIN_VALUE          //Infinity
Infinity + Infinity                  //Infinity
-Infinity + Infinity                 //NaN
```
NaN是一个特殊值，用来表示应该返回而未返回数值的情况。任何数和NaN的运算都会返回NaN。NaN与任何值都不相等，包括NaN本身。因此Javascript提供isNaN方法来检测NaN。 如果能转化成数值就返回false，否则返回true。
```Javascript
NaN + 1      //NaN
NaN == NaN   //false

isNaN(NaN)        //true
isNaN("string")  //true
isNaN(10)        //false
isNaN("10")      //false
isNaN(false)     //false
```

Javascript提供了三个数值转换的函数Number()、parseInt()、parseFloat()。
Number的转换规则参考下面代码
```javascript
Number(true)        //1
Number(false)       //0
Number(null)        //0
Number(undefined)   //Nan
Number("")          //0
Number("1N")        //NaN 包含非数字字符串
Number("-10")	    //-10
Number("10")        //10
Number("0xA")       //10 转换为十进制数
Number(0xA)       //10 转换为十进制数
Number("10.4")      //10.4
Number("   3")      //3
Number(07)          //数字直接作为十进制数返回
```


parseInt()和Number()不同，对于Boolean，null，undefined，空字符串均返回NaN。
对应字符串，parseInt()会忽略数字后面的非数字字符串。
parseInt()可以传入第二个参数作为转换基数。

```javascript
parseInt(true);        //NaN
parseInt(false);       //NaN
parseInt(null);       //NaN
parseInt(undefined);   //Nan
parseInt("");          //NaN
parseInt("1N");         //1 忽略数字后面的非数字字符串
parseInt("-10");        //-10
parseInt("10");         //10
parseInt("0xA");        //10 转换为十进制数
parseInt(0xA);        //10 转换为十进制数
parseInt("10.4");       //10
parseInt("   3");       //3
parseInt(07);           //数字
```

parseFloat()对于十六进制字符串始终会被转换成0。如果可以转换成整数，parseFloat()会返回整数。
```javascript
parseFloat(0xF)       //15
parseFloat("0xF")     //十六进制字符串始终为0
parseFloat("123.4.4") //123.4忽略第二个小数点
```

### String
在Javascript中，字符串是不可变的。如果要改变某个变量的字符串，Javascript会先销毁原来的字符串然后创建一个新的字符串赋值给变量。

除null，undefined之外，其他类型都可以调用toString()函数返回字符串。
使用String()函数可以避免null和undefined的问题。因为如果有toString()方法，就调用该方法返回字符串。null 或者undefined则直接返回其字面值。
