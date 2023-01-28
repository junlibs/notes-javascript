# javascript核心基础笔记

## 目录 
1. 入门
2. 数据类型
3. 运算符
4. 流程控制
5. 对象
6. 函数

## chapter-01.入门
### 1.1 HelloWorld
js有三种输出方式：
1. 通过`alert()`函数输出
2. 通过`console.log()`函数输出
3. 通过`document.write()`函数输出

### 1.2 js代码编写位置
js代码有以下常见编写位置：
1. 写在`<script>写在此处</script>`标签中
2. 写在外部的js文件中，然后用script标签的src属性引入
3. 写在标签的指定属性中，如`<a href="javascript:alert(123);">`

### 1.3 基本语法
1. js的注释，分为行注释和块注释，行注释使用`//这是行注释`，块注释使用`/*这是块注释*/`
2. js严格区分大小写
3. js中的空格和换行会被忽略
4. js中每条语句以分号结尾，如果不写，会自动添加

### 1.4 字面量和变量

1. 字面量：其实就是一个值，它所代表的含义就是它的字面的意思。

   比如：1, 2, 3, "hello"，true, null......

   在js中所有的字面量都可以直接使用。

2. 变量：变量可以用来“存储”字面量，并且变量中存储的字面量可以随意修改。

   变量的使用必须先声明，一般是声明和赋值同时进行，如`let  age = 10`

   声明后如果不赋值，会默认为undefined。

### 1.5 变量的内存

变量中并不直接存储任何值，而是存储值的内存地址。

<img src="./01-入门/demo5-变量的内存/js变量的内存结构-1.png">

### 1.6 常量

在js中，使用const声明常量。常量只能赋值一次，常量时不能修改的，重复赋值会报错。常量名一般大写。

例如，`const PI = 3.14`

### 1.7 标识符

在js中，所有可以由我们自主命名的内容，都可以认为是一个标识符，如常量名、函数名、类名等。

标识符命名规定：

1. 只能由数字、字母、下划线、$组成，且不能以数字开头；
2. 不能是js中的关键字和保留字；

命名规范：

1. 通常会使用驼峰命名法-首字母小写，其余每个单词开头大写，如 maxLength；
2. 类名会使用大驼峰命名-首字母大写，每个单词开头大写，如 MaxLength；
3. 常量的字母全部大写，以下划线_分隔单词，如 MAX_LENGTH；
4. 不建议使用 内置函数或类名作为标识符。



## chapter-02.数据类型-原始值

js中数据类型可以分为7种原始值、对象两大类（函数实际上是function类型的实例，也就是说函数也是对象）。

7种原始值：数值number、大整数bitInt、字符串string、布尔boolean、空值null、未定义undefined、符号symbol。

### 2.1 数值和大整数

1. 数值 Number

   - js中所有的整数和浮点数都是Number类型；
   - js中的数值并不是无限大的，当超过一定范围后会显示近似值；
   - Infinity是一个特殊的数值，表示无穷；
   - NaN也是一个特殊的数值，表示非法的数值。

   ```javascript
   let a = 10
   console.log(a) //10
   let b = 1/0
   console.log(b) //Infinity
   let c = 1 - 'hello'
   console.lgo(c) //NaN
   ```

   

2. 大整数 BigInt

   - 大整数使用n结尾，它可以表示的数字范围是无限大。（无限大是指在内存不溢出的情况下！）

   ```javascript
   let d = 9n
   console.log(d)//9n
   ```

   

3. 其他进制数字

   - 二进制，以0b开头
   - 八进制，以0o开头
   - 十六进制，以0x开头

   ```javascript
   let e = 0b1010
   console.log(e) //10 控制台输出的是按照十进制输出
   ```

   

### 2.2 类型检查

使用typeof运算符检查不同的值的类型。

要注意的是，使用typeof检查null的结果是"object"。

```javascript
console.log(typeof 42)//"number"
console.log(typeof 11n)//"bigint"
console.log(typeof (1-'a'))//"number"
console.log(typeof 'blue')//"string"
console.log(typeof true)//"boolean"
console.log(typeof abc)//"undefined"
console.log(typeof null)//"object"
console.log(typeof Symbol(10))//"symbol"
```

> 在 JavaScript 最初的实现中，JavaScript 中的值是由一个表示类型的标签和实际数据值表示的。对象的类型标签是 0。由于 `null` 代表的是空指针（大多数平台下值为 0x00），因此，null 的类型标签是 0，`typeof null` 也因此返回 `"object"`。	——<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/typeof"> MDN</a>



### 2.3 字符串

在js中使用单引号或双引号来表示字符串。

- 字符串不能跨行，除非以下两种方式：1，使用转移字符\将换行符转义，但不推荐；2，使用模板字符串，即反引号来表示字符串。
- 模板字符串中可以嵌入变量。
- 使用typeof运算符检查字符串时，会返回"string"。

```javascript
let name = "JavaScript"
let str = `你好！${name}`
console.log(str)//你好！JavaScript
```



### 2.4 其他数据类型

1. 布尔值 Boolean

   - 只有true和false；

   - 使用 typeof检查时返回"string"。

2. 空值 Null

   - 空值用来表示空对象
   - 空值只有一个 null
   - 使用typeof检查空值时会返回"object"

3. 未定义 Undefined

   - 当声明一个变量而没有赋值时，它的值就是undefined
   - 使用typeof检查时会返回"undefined"

4. 符号

   - 用来创建一个唯一的标识
   - 使用typeof价差符号时会返回"symbol"

```javascript
let bool = true
console.log(bool)//true
console.log(typeof bool)//"boolean"

let a = null
console.log(a)//null
console.log(typeof a)//"object"

let b
console.log(b)//undefined
console.log(typeof b)//"undefined"

let c = Symbol()//调用Symbol()函数创建了一个符号
console.log(c)//Symbol()
console.log(typeof c)//"symbol"
```

### 2.5 类型转换-转到字符串

类型转换，就是将一种数据类型转换为其他类型。本节介绍各种类型转换到字符串类型，有两种显式转换方式：

1. 调用toString()方法将其他类型转换为字符串；
2. 调用String()函数，将其他类型转换为字符串。

```javascript
//number——>string
let a = 10
let b = a.toString()//根据a的值10创建一个字符串"10"，但是a的值不会发生变化
console.log(typeof b, b)//"string" "10"
console.log(typeof a, a)//"number" 10

//bitint——>string
let aa = 11n
let bb = aa.toString()
console.log(typeof bb, bb)//"string" "11" 转换为字符串后，把n剔除了

//boolean——>string
let bool = true
let strbool = bool.toString()
console.log(typeof strbool, strbool)//"string" "true"

//symbole——>string
let symb = Symbol(11)
let strsymb = symb.toString()
console.log(typeof strsymb, strsymb)//"string" "Symbol(11)"

//null——>string
//由于null和undefined中没有toString()方法，所以对这两个调用toString()时会报错。
let c = null
let d = String(c)
console.log(d, d)//"string" "null"

//undefined——>string
let x
let y = String(x)
console.log(typeof y, y)
```

### 2.6 类型转换-转换到数字

将其他类型转换为数值，就是通过`Number()`函数。对于字符串来说，除了利用Number()函数，还有两种专门将字符串转换为数值的函数，即，`parseInt()`和`parseFloat()`。

- 注意：字符串利用Number()函数转换时，只有字符串是合法数字时才会转换为对应的数字；如果为空串或空格串，则转换为0；如果不是合法的数字，则会转换为NaN
- 布尔值，true转换为1，false转换为0
- null转换为0
- undefined转换为NaN

parseInt()：将字符串转换为一个整数

- ```
  解析时，会自左向右读取一个字符串，直到读取到字符串中所有的有效整数。
  也可以使用paseInt()来对一个数字进行取整。
  ```

parseFloat()：将一个字符串转换为浮点数

- ```
  解析时，会自左向右读取一个字符串，直到读取到字符串中所有的有效小数
  ```

```javascript
//parseInt()示例
a = '123'
b = parseInt(a)
console.log(typeof b, b)//"number" 123

a = '123a'
b = parseInt(a)
console.log(typeof b, b)//"number" 123  这里就是与Number()的区别了

a = '123.45'
b = parseInt(a)
console.log(typeof b, b)//"number" 123

a = 123
b = parseInt(a)//虽然a不是字符串，但是在处理的时候，会先根据a值生成它的字符串
console.log(typeof b, b)//"number" 123

//parseFloat()示例
a = '123.45'
b = parseFloat(a)
console.log(typeof b, b)//"number" 123.45
```



### 2.7类型转换-转到布尔值

其他类型转换到布尔值，显式转换使用Boolean()函数即可。

- 对于number类型，0和NaN，转换为false；其余是true
- 对于string类型，空串转换为false，其余是true
- 对于null，转换为false
- 对于undefined，转换为false



## chapter-03.运算符

### 3.1 算术运算符

算术运算符有：

- 加 +
- 减 -
- 乘 *
- 除 /
- 取余 %
- 幂运算 **

需要注意的是：

- 除法运算不是整除，结果会有小数位。除数为0不会报错，会返回Infinity
- js是弱类型语言，当进行运算时，会通过自动的类型转换来完成运算：
  - 算术运算时，除了字符串的加法，其他运算的操作数是非数值时，都会转换为数值，然后再运算；
  - 当任意一个值和字符串做加法运算时，它会先将其他值转换为字符串，然后再做拼串操作。

```js
let a = 10 / 5
console.log(a)//2

a = 10 / 3
console.log(a)//3.333333333 注意：结果并不取整

a = 10 / 0
console.log(a)//Infinity

//字符串参与加法运算（隐式类型转换）
a = 2 + '3'
console.log(a)//"2" + "3" => "23"

a = 'hello' + 'js'
console.log(a)//"hellojs"

a = true + ''
console.log(a)//"true"

//其他类型参与运算（隐式类型转换）
a = 10 - '5'
console.log(a)//10-5 => 5

a = 10 + true
console.log(a)//10+1 => 11

a = 5 + null
console.log(a)//5+0 => 5

a = 6 - undefined
console.log(a)//6-NaN => NaN
```







