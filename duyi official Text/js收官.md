# javascript（腾讯课堂）

## 数值类型

Number，String，Boolean，undefined，null

## 引用类型

array， Object，function……date，RegExp

## 加号的作用：

 1. 数值的相加

 2. 字符串的连接

    > ==任何类型数据和字符串相加都等于字符串==

赋值的顺序：自右向左，计算的顺序：自左向右



## 布尔转换

undefined， null，NaN，""，0，false ==> 转换成布尔值都是false

## &&与||

```javascript
		let a = 1;
        let b = 0;
        console.log(a || b); //1
        console.log(a && b); //0
```

||第一个为错，则返回第二个，第一个为对，返回第一个。

&&第一个为对返回第二个，第一个为错，返回第一个

## for循环原理

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-29_10-19-01.png?raw=true)





## 作业：

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-29_10-40-59.png?raw=true)

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-29_10-44-57.png?raw=true)

```javascript
        //第一题
        let res = 2;
        let n = parseInt('1');
        if (n == 0) {
            res = 1
        } else if (n >= 1) {
            for (let i = 1; i < n; i++) {
                res = res * 2
            }
        }
        console.log(res);
        
        //第二题
		let res = 1;
        let n = parseInt('2');
        for (let i = 1; i <= n; i++) {
            res = res * i
        }
        console.log(res);

		//第三题
		        let first = 1;
        let second = 1;
        let n = 6;
        let res = 0

        if (n == 1 || n == 2) {
            res = 1
        } else if (n > 2) {
            let res1 = 1;
            let res2 = 1
            for (let i = 2; i < n; i++) {
                res = res1 + res2;
                res1 = res2;
                res2 = res
                console.log(res, res1, res2);
            }

        }

        console.log(res);

		//第三题递归解法
		        let res = 1
        function test(n) {
            if (n == 1) {
                return res = 1
            }
            if (n == 2) {
                return res = 1
            }
            if (n > 2) {
                return res = test(n - 1) + test(n - 2)
            }
        }

        test(6);
        console.log(res);

		//第四题
		let a = parseInt('567');
        let num = a % 10;
        let ten = Math.floor(a / 10) % 10
        let hunderd = Math.floor(a / 100);
        console.log(hunderd);
        let res = num * 100 + ten * 10 + hunderd;
        console.log(res);

		//第五题
        function max(a, b, c) {
            if (a > b) {
                if (a > c) {
                    return a;
                }
                return c;
            } else {
                if (b > c) {
                    return b;
                }
                return c;
            }
        }
        console.log(max(5, 5, 6));

		//第六题
		let arr = [];
        for (let i = 2; i <= 100; i++) {
            let flag = true;
            for (let j = 2; j < i; j++) {
                if (i % j == 0) {
                    flag = false;
                };

            }
            if (flag == true) {
                arr.push(i)
            }
        }
        console.log(arr);

		
		
```

## typeof会返回六种类型的数据

number, string, boolean, Object, undefined, function.



## Number显示转换

|     对象名称     |    转换后的值     |
| :--------------: | :---------------: |
|  字符串：‘123’   |  123（数值类型）  |
|      布尔值      | true：1；false：0 |
|       null       |         0         |
|    undefined     |        NaN        |
|   字符串‘abc‘    |        NaN        |
| 字符串：’123abc‘ |        NaN        |

## parseInt(内容[,进制])

parseint会将内容转化成整型。parseInt('123.3') = 123；

## parseFloat(string)

将字符串转化为小数

## String（）

将内容转化为字符串

## toString([redix])

null和undefined不能使用同String()

toString()的redix参数指的是目标进制，即将现有数据转化成redix进制的数。

```javascript
        let a = 10;
        console.log(a.toString(16)); //a
        console.log(typeof (a.toString(16)));
```



## 隐式转换

|       方法名称        | 转换结果 |                           转换原理                           |
| :-------------------: | :------: | :----------------------------------------------------------: |
|        isNaN()        |  布尔值  |          先用Number转换，然后再和NaN比对返回布尔值           |
| ++/-- 和 +/-（正/负） |  Number  |                      使用Number隐式转换                      |
|       +（加号）       |  String  |                 字符串和任何类型相加位字符串                 |
|         -*/%          |  Number  |                      使用Number隐式转换                      |
|      && \|\| ！       | Boolean  |                    隐式转换为Boolean类型                     |
|       < > <= >=       | Boolean  | 数字与字符串比较先转成数字类型，返回Boolean；字符串和字符串比较，比较ASCII码。 |
|        == ；!=        | Boolean  |                       返回boolean类型                        |

## 不发生类型转换

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-29_19-41-43.png?raw=true)



> typeof的返回值是字符串类型
>
> typeof(typeof(underfined))     //结果是：string
>
> typeof(null) //Object



## 作业：

​	![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-29_19-47-19.png?raw=true)

==(window.foo || (window.foo="bar"))，问window.foo的值==

 

```javascript
        var a = '123abc';
        console.log(typeof a); 
        console.log(typeof NaN);
        console.log(typeof (+a));
        console.log(typeof null);
        console.log(typeof !!a);
        console.log(typeof a + "");
        console.log((1 == "1"));
        console.log(NaN == NaN);
        console.log(NaN == undefined);

```



## toFixed(num)

保留num位有效数字，四舍五入



## 函数

### 函数的表达方式

```javascript
 //函数声明
function abc() {};
abc.name //'abc'

//命名函数表达式
let a = function test() {}
a.name //test

//3.匿名函数表达式  --->函数表达式
let a = function() {}
a.name //a
```



### 获取参数数量

实参个数：==arguments参数==

形参个数：==函数名.length==

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-30_16-25-04.png?raw=true)



### arguments 和形参的关系

argumets中的数据变化时，形参的数据也变化；反之亦然。但是这两个数指向并不是一个对象，而是这两个对象之间存在映射关系。

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-30_16-40-43.png?raw=true)

> 当形参数量对于实参，或者实参对于形参；多出来的参数与arguments中的数据不映射。

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-30_16-46-21.png?raw=true)

### 课堂练习

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-30_16-55-09.png?raw=true)

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-30_19-31-41.png?raw=true)



## 预编译

> 1. 函数声明整体提升
> 2. 变量声明提升（var）

### 预备知识

> 1. implay global 暗示全局变量：即任何变量，如果变量未经声明就赋值，此变量就为全局变量所有。
>
> 2. 一切声明的全局变量，全是window属性
>
>    ==var a=b=123==的执行过程是：先把123赋值给b，然后声明a，最后将b赋值给a。

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-11-01_10-33-53.png?raw=true)

**==window就是全局==**



### 预编译（函数中）

==预编译发生在函数执行的前一刻==

> 预编译四部曲：
>
> 	1. 创建AO对象(执行期上下文)
> 	1. 找形参和变量声明，将变量和形参名作为AO属性名，值为undefined
> 	1. 将实参值和形参统一
> 	1. 在函数体里找函数声明，值赋予函数体

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-11-01_13-00-06.png?raw=true)



### 全局（生成的是GO（global Object === window））

现有GO再有AO

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-11-01_13-25-31.png?raw=true)

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-11-01_13-30-40.png?raw=true)

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-11-01_13-37-17.png?raw=true)



![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-11-01_14-38-40.png?raw=true)



# js收官

# 知识回顾-数据的表达1



和HTML、CSS不同，JS是一门 _命令式编程语言_，和其他命令式编程语言一样，它的本质是**处理数据**

JS 提供了三种方式来表达一个数据：

- 变量
- 字面量
- 表达式

程序中任何需要数据的地方，都可以使用上面任意一种数据表达。

## 注意点

### 标识符

程序中有些可以自行命名的地方，称之为**标识符**

> 常见的标识符有：变量名、函数名、参数名

_js_ 的标识符必须符合以下规则：

- 允许数字、字母、下划线、\$符号
- 不得以数字开头
- 不能和关键字冲突
- 建议使用驼峰命名法

一个完整的程序中，会涉及成百上千的标识符，好的名称不仅可以减少名称冲突，更有利于程序的阅读和维护。

名称要做到**望文知意**

### 转义符

| 转义符 | 含义           |
| ------ | -------------- |
| `\'`   | 普通英文单引号 |
| `\"`   | 普通英文双引号 |
| `\r`   | 回车           |
| `\n`   | 换行           |

> 小技巧：常用`\r\n`表示换行



# 知识回顾-数据的表达2



本节课主要回顾对象的表达

## 注意点

### 数据类型

原始类型：number、string、boolean、null、undefined

引用类型：对象（包含普通对象、数组、函数）

### 对象的原始写法

对象的**所有属性名都是字符串**，因此使用单引号或双引号包裹起来

```js
var obj = {
  'name': '邓哥',
  'age': 35,
  'graduate date': '2007-7-1',
  'home address': {
    'province': '黑龙江',
    'city': 'city'
  }
};
```

为了书写的方便，当对象的属性名是**纯数字**或**符合标识符规范**时，可以**省略引号**

> 小贴士
> 书写代码时我们无须关注这些规则，直接按照简写方式书写属性，若编辑器出现报错，则使用引号包裹属性名即可

读取对象属性时，使用`[]`，把要读取的属性名传递到中括号中

```js
obj['name'] // 读取obj的name属性
obj['home address'] // 读取obj的home address属性
obj['home address']['province'] // 这是啥意思？
```

若属性**符合标识符规范**，可以使用`.`符号连接属性名

```js
obj.name // 读取obj的name属性
obj.age // 读取obj的age属性
obj['home address'].province // 请自行脑补
```

# 知识回顾-数据的表达3

数组，用于表达多个同种类的数据

它的本质就是一个对象

```js
// 数组的对象结构
{
   '0': xxx,
   '1': xxx,
   '2': xxx,
   'length': 3
}
```

# 知识回顾-数据的运算



## 运算符

### 算术（数学）运算

支持：加(+)、减(-)、乘(*)、除(/)、求余(%)

值得注意的是，+和-可以放到单个数据的前面，表示正负。

算术运算的表达式一定返回数字，可以利用其特点做类型转换，参考[类型的隐式转换](#类型的隐式转换)

### 字符串拼接

当`+`的两端有一个是字符串时，不再进行算术运算，而变为字符串拼接

表达式一定返回string，可以利用其特点做类型转换，参考[类型的隐式转换](#类型的隐式转换)

### 赋值运算

涉及的运算符：`=` `+=` `*=` `/=` `-=` `%=`。

其中，`a += xxx`，等效于`a = a + (xxx)`，其他类似

> 小贴士
> 赋值表达式始终返回赋值结果，我们可以利用该特点完成连续赋值
>
> ```js
> // 将 3 同时赋值给 a、b
> a = b = 3;
> ```

### 比较运算

涉及的运算符：`==` `===` `!=` `!==` `>` `>=` `<` `<=`

> 小贴士
> 在实际开发中，没有任何理由使用`==`和`!=`，你可以当做这两个运算符并不存在。
> 应该始终使用`===`和`!==`来比较相等和不相等

> 小贴士
> 比较运算始终返回boolean，我们可以利用这一点来完成某些赋值
>
> ```js
> // 啰嗦的代码
> if(sex === '男'){
> user.isMale = true;
> }
> else{
> user.isMale = false;
> }
> 
> // 简洁优雅的代码
> user.isMale = sex === '男'
> ```

### 逻辑运算

逻辑运算会涉及到[布尔判定](#布尔判定)

运算符：`!`

对后面的数据取反，表达式一定返回boolean。

可以利用其特点做类型转换，参考[类型的隐式转换](#类型的隐式转换)

运算符：`&&`

并且，真真为真，其他为假，具有短路规则。

表达式返回**最后一个判定的数据**

> 小贴士
> 在实际的开发中，我们可以利用短路规则简化代码
>
> ```js
> // 实现功能，如果exp有值（判定为真），就输出ok
> 
> // 啰嗦的代码
> if(exp){
> console.log(exp);
> }
> 
> // 简洁的代码
> exp && console.log(exp)
> ```

运算符：`||`

或者，假假为假，其他为真，具有短路规则。

表达式返回**最后一个判定的数据**

> 小贴士
> 在实际的开发中，我们可以利用短路规则简化代码
>
> ```js
> // 实现功能，如果exp有值，就把它的值赋值给n，如果没有值，就给n赋值为默认值 1
> 
> // 啰嗦的代码
> if(exp){
> n = exp;
> }
> else{
> n = 1;
> }
> 
> // 简洁的代码
> n = exp || 1;
> ```

运算符：`? :`，格式`a ? b : c`

三目运算，判定a，为真时表达式返回b，否则返回c

> 小贴士
> 三目运算通常用于替代一些简单的if结构
>
> ```js
> // 如果exp为真，则把1赋值给n，否则，把2赋值给n
> // 啰嗦的代码
> if(exp){
> n = 1;
> }
> else{
> n = 2;
> }
> 
> // 更简洁的代码
> n = exp ? 1 : 2;
> ```


## 布尔判定

所有需要判断真假的地方都会使用下面的规则

| 数据                                      | 判定  |
| ----------------------------------------- | ----- |
| `false` `null` `undefined` `0` `NaN` `''` | false |
| 剩余所有数据                              | true  |

## 类型的隐式转换

每个运算符都有自己期望的数据，比如`*`期望两端都是数字

一旦数据不符合运算符的期望，js就会悄悄的对数据进行类型转换，把它转换成期望的值后进行运算。

值得注意的是，这种转换是 _临时_ 的，并不会对原数据造成影响

> 小贴士
> 在实际的开发中，我们可以利用类型的隐式转换完成以下功能：
>
> ```js
> var n = +a; // 不管a是啥，都会被转换成数字，保存到n中
> var s = a + ''; // 不管a是啥，都会被转换成字符串，保存到s中
> var b = !!a; // 不管a是啥，都会被转换成boolean，保存到b中
> ```



# 知识回顾-流程的切割

## 函数的作用

使用函数切割流程，不仅可以减少重复代码、还可以有效的降低整体复杂度

<img src="http://mdrs.yuanjin.tech/img/20211209124426.png" alt="image-20211209124426753" style="zoom:50%;" />

## 函数的常见问题

### **如何理解函数的参数、返回值、函数体？**

<img src="http://mdrs.yuanjin.tech/img/20211209125120.png" alt="image-20211209125120817" style="zoom:50%;" />

参数：表示完成流程所需的**必要信息**

返回值：表示完成流程后**产生的结果**

函数体：表示具体的流程

**函数的参数、返回值只取决于函数的作用，与函数体无关**

### 为什么我觉得有了函数之后，程序反而变得更复杂了？

函数的核心作用，是为了让某一段复杂的流程变得简单。

如果在函数的帮助下，反而觉得流程变得复杂了，极有可能的原因是开发思想没有做相应的切割，导致思想负担过重。

**始终记住以下两点**：

1. 定义函数时，只需要考虑这个函数如何实现即可，完全不需要考虑其他无关的东西。
2. 调用函数时，只需要考虑向其传递什么参数，如何使用它的返回结果，完全无需考虑函数的具体实现。

函数具有**三要素**：函数名、参数、返回值

只要具备三要素，就能书写函数体；只要具备三要素，就能完成函数调用。

### 学习函数时不知道该如何切割流程怎么办？

要完成一个函数声明，分为两步：

1. 设计函数

   设计函数就是如何切割流程，具体来说就是设计出函数的三要素，这一步是最难的，目前无须同学们掌握，老师会帮你把函数设计好。

2. 书写函数体

   根据设计的三要素完成函数体，这一步就是现阶段练习的重点。

# 数据的作用域

1. JS有两种作用域：全局作用域和函数作用域
   - 内部的作用域能访问外部，反之不行。访问时从内向外依次查找。
   - 如果在内部的作用域中访问了外部，则会产生闭包。
   - 内部作用域能访问的外部，取决于函数定义的位置，和调用无关
2. 作用域内定义的变量、函数声明会提升到作用域顶部



# 全局对象

无论是浏览器环境，还是node环境，都会提供一个全局对象

- 浏览器环境：window
- node环境：global

全局对象有下面几个特点：

- 全局对象的属性可以被直接访问

- 给未声明的变量赋值，实际就是给全局对象的属性赋值

  > 永远别这么干

- 所有的全局变量、全局函数都会附加到全局对象

  > 这称之为全局污染，又称之为全局暴露，或简称污染、暴露
  >
  > 如果要避免污染，需要使用**立即执行函数**改变其作用域
  >
  > 立即执行函数又称之为IIFE，它的全称是Immediately Invoked Function Expression
  >
  > **IIFE通常用于强行改变作用域**



# 原型

##  原型要解决的问题

<img src="http://mdrs.yuanjin.tech/img/20211210142340.png" alt="image-20211210142340406" style="zoom:50%;" />

上图中，通过构造函数可以创建一个用户对象

这种做法有一个严重的缺陷，就是每个用户对象中都拥有一个`sayHi`方法，对于每个用户而言，`sayHi`方法是完全一样的，没必要为每个用户单独生成一个。

要解决这个问题，必须学习原型

## 原型是如何解决的

<img src="http://mdrs.yuanjin.tech/img/20211210141850.png" alt="image-20211210141850465" style="zoom:50%;" />



1. **原型**

   每个函数都会自动附带一个属性`prototype`，这个属性的值是一个普通对象，称之为原型对象

2. **实例**

   instance，通过`new`产生的对象称之为实例。

   > 由于JS中所有对象都是通过`new`产生的，因此，严格来说，JS中所有对象都称之为实例

3. **隐式原型**

   每个实例都拥有一个特殊的属性`__proto__`，称之为隐式原型，它指向构造函数的原型



这一切有何意义？

**当访问实例成员时，先找自身，如果不存在，会自动从隐式原型中寻找**

**这样一来，我们可以把那些公共成员，放到函数的原型中，即可被所有实例共享**

<img src="http://mdrs.yuanjin.tech/img/20211210143328.png" alt="image-20211210143328533" style="zoom:50%;" />

# 这是啥？

<img src="http://mdrs.yuanjin.tech/img/20211213054951.png" alt="image-20211213054946368"  />

不同的场景，**这** 指代的含义不同，JS中的**this**关键字也是如此：

- 在全局代码中使用this，指代全局对象

  > 在真实的开发中，很少在全局代码使用this

- **在函数中使用this，它的指向完全取决于函数是如何被调用的**

  | 调用方式         | 示例                | 函数中的this指向  |
  | ---------------- | ------------------- | ----------------- |
  | **通过new调用**  | `new method()`      | 新对象            |
  | **直接调用**     | `method()`          | 全局对象          |
  | **通过对象调用** | `obj.method()`      | 前面的对象        |
  | **call**         | `method.call(ctx)`  | call的第一个参数  |
  | **apply**        | `method.apply(ctx)` | apply的第一个参数 |
  |                  |                     |                   |




# 原型链

## 什么是原型链

**所有的对象都是通过`new 函数`的方式创建的**

```js
var u1 = new User('邓', '旭明'); // 对象 u1 通过 new User 创建
var u2 = { // 对象 u2 通过 new Object 创建
  firstName: '莫',
  lastName: '妮卡'
}
// 等效于
var u2 = new Object(); 
u2.firstName = '莫';
u2.lastName = '妮卡';
```

上面的代码形成的原型图如下

![image-20210903081220607](http://mdrs.yuanjin.tech/img/20210903081220.png)

原型对象本身也是一个对象，默认情况下，是通过`new Object`创建的，因此，上面的两幅原型图是可以发生关联的

<img src="http://mdrs.yuanjin.tech/img/20210903082540.png" alt="image-20210903082540379" style="zoom:50%;" />

> `Object.prototype.__proto__`比较特殊，它固定指向null

可以看出，u1的隐式原型形成了一个链条，称之为**原型链**

当读取对象成员时，会先看对象自身是否有该成员，如果没有，就依次在其原型链上查找

## 完整的链条

![image-20210903152359095](http://mdrs.yuanjin.tech/img/20210903152359.png)

## 对开发的影响

### 在原型上更改会产生多大影响

更改构造函数的原型会对所有原型链上有该构造函数的原型的对象产生影响

### 学会利用原型链判断类型

1. `instanceof`关键字【常用】

   ```js
   object instanceof constructor
   // 判断object的原型链中，是否存在constructor的原型
   ```

2. `Object.getPrototypeOf()`【不常用】

   ```js
   Object.getPrototypeOf(object);
   // 返回object的隐式原型
   ```

### 学会创建空原型的对象

1. 利用`Object.create()`

   ```js
   Object.create(target);
   // 返回一个新对象，新对象以target作为隐式原型
   ```

2. 利用`Object.setPrototypeOf()`

   ```js
   Object.setPrototypeOf(obj, prototype);
   // 设置obj的隐式原型为prototype
   ```




# 继承

## 会员系统

视频网站有两种会员：

- 普通会员
  - 属性：用户名、密码
  - 方法：观看免费视频
- VIP会员
  - 属性：普通会员的所有属性、会员到期时间
  - 方法：普通会员的所有方法、观看付费视频

如果我们需要使用构造函数来创建会员，如何书写构造函数才能实现上面的需求？

```js
// 普通会员的构造函数
function User(username, password){
  this.username = username;
  this.password = password;
}
User.prototype.playFreeVideo = function(){
  console.log('观看免费视频')
}

// VIP会员的构造函数
function VIPUser(username, password, expires){
  this.username = username;
  this.password = password;
  this.expires = expires;
}
VIPUser.prototype.playFreeVideo = function(){
  console.log('观看免费视频')
}
VIPUser.prototype.playPayVideo = function(){
  console.log('观看付费视频')
}
```

上面的代码出现了两处重复代码：

1. VIPUser的构造函数中包含重复代码

   ```js
   this.username = username;
   this.password = password;
   ```

   这段代码和User构造函数并没有区别，可以想象得到，将来也不会有区别，即：**普通用户该有的属性，VIP用户一定有**

2. VIPUser的原型上包含了重复代码

   ```js
   VIPUser.prototype.playFreeVideo = function(){
     console.log('观看免费视频')
   }
   ```

   这个方法和User上的同名方法逻辑完全一致，可以想象得到，将来也不会有区别，即：**普通用户该有的方法，VIP用户一定有**

> 如何解决上述两处重复？

## 处理构造器内部的重复

可以将VIPUser构造器改写为

```js
function VIPUser(username, password, expires){
  User.call(this, username, password);
  this.expires = expires;
}
```

## 处理原型上的重复

只需要将原型链设置为下面的结构即可

<img src="http://mdrs.yuanjin.tech/img/20211214155347.png" alt="image-20211214155342118" style="zoom:50%;" />

仅需一句代码即可

```js
Object.setPrototypeOf(VIPUser.prototype, User.prototype)
```

至此，完美的解决了之前提到的两处重复代码的问题

## 这和继承有什么关系

继承是面向对象的概念，它描述了两个对象类型（类，构造函数）之间的关系

如果在逻辑上可以描述为：A不一定是B，但B一定是A，则：B继承A、A派生B、A是B的父类、B是A的子类

**子类的实例应该自动拥有父类的所有成员**

继承具有两个特性：

- 单根性：子类最多只有一个父类
- 传递性：间接父类的成员会传递到子类中

## 如何在JS中封装继承

```js
function inherit(Child, Parent){
  // 在原型链上完成继承 
  Object.setPrototypeOf(Child.prototype, Parent.prototype);
}
```

> 过去，由于没有提供更改隐式原型的方法，因此这一过程会比较复杂。那时候，我们使用一种称之为「圣杯模式」的办法来达到相同的目的，这里不做介绍。



# 标准库

## 包装类

如果尝试着把原始类型（number、string、boolean）当做对象使用，JS会自动将其转换为对应包装类的实例

### Number

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number

| API                                                          | 含义                             | 备注                         |
| ------------------------------------------------------------ | -------------------------------- | ---------------------------- |
| [Number.NaN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/NaN) | 表示一个数学上并不存在的数字     | 可以直接书写为`NaN`          |
| [Number.isNaN()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN) | 判断传入的值是否是NaN            | 可以直接书写为`isNaN`        |
| [Number.isInteger()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger) | 判断传入的值是否是整数           |                              |
| [Number.parseInt()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/parseInt) | 把传入的值转换为整数形式返回     | 可以直接书写为`parseInt()`   |
| [Number.parseFloat()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/parseFloat) | 把传入的值转换为小数形式返回     | 可以直接书写为`parseFloat()` |
| [Number.prototype.toFixed()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed) | 将当前数字保留指定位数的小数返回 | 传入小数位数                 |
| [Number.prototype.toString()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/tostring) | 将当前数字转换为字符串返回       | 传入进制2-36                 |

### String

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String

| API                                                          | 含义                                                         | 备注                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------- |
| [String.fromCharCode()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode) | 根据编码值得到一个字符                                       | 传入一个或多个编码值   |
| [String.prototype.length](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/length) | 得到字符串的长度                                             |                        |
| [String.prototype.charCodeAt()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt) | 得到某个下标的字符编码                                       | 传入下标               |
| [String.prototype.includes()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/includes) | 判断当前字符串是否包含某个子串                               | 传入子串               |
| [String.prototype.indexOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf) | 判断某个字符串在当前字符串中的第一个下标位置                 | 如果没有，返回-1       |
| [String.prototype.lastIndexOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/lastIndexOf) | 判断某个字符串在当前字符串中的最后一个下标位置               | 如果没有，返回-1       |
| [String.prototype.endsWith()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith) | 判断某个字符串是否以指定的字符串结束                         | 传入一个字符串         |
| [String.prototype.startsWith()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith) | 判断某个字符串是否以指定的字符串开始                         | 传入一个字符串         |
| [String.prototype.padStart()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/padStart) | 将当前的字符串按照指定的字符在字符串开始位置填充到指定的位数，返回填充后的字符串 | 传入位数、填充字符     |
| [String.prototype.padEnd()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd) | 将当前的字符串按照指定的字符在字符串结束位置填充到指定的位数，返回填充后的字符串 | 传入位数、填充字符     |
| [String.prototype.split()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split) | 把当前字符串按照某个字符串分割成一个字符串数组返回           | 传入分隔符             |
| [String.prototype.substring()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substring) | 返回一个字符串在开始索引到结束索引之间的一个子集, 或从开始索引直到字符串的末尾的一个子集 | 传入开始字符、结束字符 |
| [String.prototype.trim()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/Trim) | 从字符串的两端删除空白字符，返回新字符串                     | 无参数                 |
| [String.prototype.trimStart()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trimStart) | 从字符串的开头删除空白字符，返回新字符串                     | 无参数                 |
| [String.prototype.trimEnd()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trimEnd) | 从字符串的末端删除空白字符，返回新字符串                     | 无参数                 |
| [String.prototype.toUpperCase()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase) | 将调用该方法的字符串转为大写形式并返回                       | 无参数                 |
| [String.prototype.toLowerCase()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase) | 将调用该方法的字符串转为小写形式并返回                       | 无参数                 |
| [String.prototype.replace()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace) | 替换字符串中的==**第一个**==对应字符为新字符                 |                        |
| [String.prototype.replaceAll()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replaceall) | 替换字符串中的==**所有**==对应字符为新字符                   |                        |

## 数学

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math

| API                                                          | 含义                      | 备注            |
| ------------------------------------------------------------ | ------------------------- | --------------- |
| [Math.PI](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/PI) | 得到圆周率π               |                 |
| [Math.abs()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/abs) | 求某个数绝对值            | 传入一个数      |
| [Math.ceil()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil) | 向上取整                  | 传入一个数      |
| [Math.floor()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) | 向下取整                  | 传入一个数      |
| [Math.max()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/max) | 求一个数列中的最大值      | 把数列依次传入  |
| [Math.min()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/min) | 求一个数列中的最小值      | 把数列依次传入  |
| [Math.random()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/random) | 得到一个0-1之间的随机小数 | 无参；无法取到1 |
| [Math.round()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/round) | 返回四舍五入的结果        | 传入一个数      |

## 日期

### 时间基础知识

#### 单位

| 单位               | 名称 | 换算                  |
| ------------------ | ---- | --------------------- |
| hour               | 小时 | 1 day = 24 hours      |
| minute             | 分钟 | 1 hour = 60 minutes   |
| second             | 秒   | 1 minute = 60 seconds |
| millisecond （ms） | 毫秒 | 1 second = 1000 ms    |
| nanosecond （ns）  | 纳秒 | 1 ms = 1000 ns        |

#### GMT和UTC

世界划分为24个时区，北京在东8区，格林威治在0时区。

![时区](https://gblobscdn.gitbook.com/assets%2F-LQcTxgqTqhC05ckLpLr%2F-LikgRi0I4q8Q0a3kFgz%2F-LikgSk-E-e8AcD50vHu%2F2019-07-02-11-14-46.png?alt=media)

**GMT**：Greenwish Mean Time 格林威治世界时。太阳时，精确到毫秒。

**UTC**：Universal Time Coodinated 世界协调时。以原子时间为计时标准，精确到纳秒。

> 国际标准中，已全面使用UTC时间，而不再使用GMT时间

GMT和UTC时间在文本表示格式上是一致的，均为`星期缩写, 日期 月份 年份 时间 GMT`，例如：

```
Thu, 27 Aug 2020 08:01:44 GMT
```

另外，ISO 8601标准规定，建议使用以下方式表示时间：

```
YYYY-MM-DDTHH:mm:ss.msZ
例如：
2020-08-27T08:01:44.000Z
```

**GMT、UTC、ISO 8601都表示的是零时区的时间**

#### Unix 时间戳

> Unix 时间戳（Unix Timestamp）是Unix系统最早提出的概念

它将UTC时间1970年1月1日凌晨作为起始时间，到指定时间经过的秒数（毫秒数）

#### 程序中的时间处理

**程序对时间的计算、存储务必使用UTC时间，或者时间戳**

**在和用户交互时，将UTC时间或时间戳转换为更加友好的文本**

<img src="http://mdrs.yuanjin.tech/img/20200827163636.png" alt="image-20200827163636508" style="zoom:50%;" />

思考下面的问题：

1. 用户的生日是本地时间还是UTC时间？
2. 如果要比较两个日期的大小，是比较本地时间还是比较UTC时间？
3. 如果要显示文章的发布日期，是显示本地时间还是显示UTC时间？
4. `北京时间2020-8-28 10:00:00`和`格林威治2020-8-28 02:00:00`，两个时间哪个大，哪个小？
5. `北京的时间戳为0`和`格林威治的时间戳为0`，它们的时间一样吗？
6. 一个中国用户注册时填写的生日是`1970-1-1`，它出生的UTC时间是多少？时间戳是多少？

### 日期API

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date

构造函数：

```js
new Date(); // 得到一个当前日期对象
new Date(value); // 根据时间戳得到一个日期对象
new Date(dateString); // 根据一个标准日期字符串得到一个日期对象
new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]); // 根据年、月、日、小时、分钟、秒、毫秒得到一个日期对象
```

| API                                                          | 含义                   | 备注                     |
| ------------------------------------------------------------ | ---------------------- | ------------------------ |
| [Date.now()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/now) | 得到当前时间戳         | 无参                     |
| [Date.prototype.getFullYear()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getFullYear) | 得到年                 | 无参；本地时间；         |
| [Date.prototype.getMonth()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getMonth) | 得到月                 | 无参；本地时间；范围0-11 |
| [Date.prototype.getDate()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getDate) | 得到日                 | 无参；本地时间；         |
| [Date.prototype.getHours()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getHours) | 得到小时               | 无参；本地时间；         |
| [Date.prototype.getMinutes()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getMinutes) | 得到分钟               | 无参；本地时间；         |
| [Date.prototype.getSeconds()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getSeconds) | 得到秒                 | 无参；本地时间；         |
| [Date.prototype.getMilliseconds()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getMilliseconds) | 得到毫秒               | 无参；本地时间；         |
| [Date.prototype.toLocaleString()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString) | 得到日期本地的表示方式 |                          |

## 对象

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object

| API                                                          | 含义                                     | 备注         |
| ------------------------------------------------------------ | ---------------------------------------- | ------------ |
| [Object.assign()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) | 将多个对象的属性混合到一起               | 后面覆盖前面 |
| [Object.getPrototypeOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf) | 获取一个对象的隐式原型                   |              |
| [Object.setPrototypeOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/setPrototypeOf) | 设置一个对象的隐式原型                   |              |
| [Object.create()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create) | 创建一个新对象，同时设置新对象的隐式原型 |              |

## 数组

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array

| API                                                          | 含义                                                   | 备注                                               |
| ------------------------------------------------------------ | ------------------------------------------------------ | -------------------------------------------------- |
| [Array.prototype.concat()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/concat) | 把多个数组拼接成一个                                   |                                                    |
| [Array.prototype.includes()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) | 判断数组中是否包含某个值                               |                                                    |
| [Array.prototype.indexOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) | 得到数组中某个值的第一个下标                           | 若不存在则返回-1                                   |
| [Array.prototype.lastIndexOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf) | 得到数组中某个值的最后一个下标                         | 若不存在则返回-1                                   |
| [Array.prototype.join()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/join) | 把数组中每一项使用某个字符连接起来，形成一个字符串返回 |                                                    |
| [Array.prototype.push()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/push) | 向数组的末尾添加一项                                   |                                                    |
| [Array.prototype.unshift()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) | 向数组的开头添加一项                                   |                                                    |
| [Array.prototype.pop()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) | 删除数组最后一项                                       | 返回被删除的值                                     |
| [Array.prototype.shift()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) | 删除数组第一项                                         | 返回被删除的值                                     |
| [Array.prototype.splice()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) | 删除、修改、插入任何位置的值(==对用于删除==)           |                                                    |
| [Array.prototype.reverse()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) | 将数组中的元素顺序颠倒                                 |                                                    |
| [Array.prototype.sort()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) | 对数组进行排序                                         | 传入比较函数：0-位置不变，<0-前者在前，>0-前者在后 |
| [Array.prototype.slice()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) | 对数组进行切割                                         |                                                    |



==**注意**==：

关于sort（）：	

```js
let arr = [2, 6, 3, 78, 4, 23];
arr.sort((a, b) => {
  return a - b;  //按照升序排列：若a>b且返回正数，a<b返回负数，a=b返回0；反之按照降序排列
})

```

关于slic()

```js
let arr = [2, 6, 3, 78, 4, 23];
//slice()除了切割数组之外还可以对数组进行克隆
let arrClone = arr.slice(0);
console.log(arr === arrClone);  //false
```

```js
//将伪数组转换为数组
let fakeObj = {
  0: 'ShiJHang',
  1: 18,
  "length": '2'
}

let arr = [].slice.call(fakeObj); //[ 'ShiJHang', 18 ]
//或者
arr2 = Array.prototype.slice.call(fakeObj); //[ 'ShiJHang', 18 ]
console.log(arr);
```



## 函数

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function

| API                                                          | 含义               | 备注                     |
| ------------------------------------------------------------ | ------------------ | ------------------------ |
| [Function.prototype.apply()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) | 执行函数，绑定this | 参数列表以数组的形式传递 |
| [Function.prototype.call()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call) | 执行函数，绑定this | 参数列表依次传递         |



# WebAPI

和标准库不同，WebAPI 是**浏览器**提供的一套 API，用于操作浏览器窗口和界面

WebAPI 中包含两个部分：

- BOM：Browser Object Model，浏览器模型，提供和浏览器相关的操作
- DOM：Document Object Model，文档模型，提供和页面相关的操作

<img src="http://mdrs.yuanjin.tech/img/20211215154644.png" alt="image-20211215154639275" style="zoom:50%;" />

## BOM

BOM 提供了一系列的对象和函数，提供和浏览器本身相关的操作

### window

全局对象

https://developer.mozilla.org/zh-CN/docs/Web/API/Window/window

| API                                                          | 含义                                             | 备注                                                         |
| ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------ |
| [`open()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/open) | 打开一个新的浏览器窗口                           | 返回新窗口的 window 对象                                     |
| [`close()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/close) | 关闭浏览器窗口                                   | 只能关闭使用 open 打开的浏览器窗口                           |
| [==setTimeout()==](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/setTimeout) | 设置一个计时器<br />在一段时间后自动执行某个函数 | 参数 1：函数，无参，this 指向 window<br />参数 2：时间，毫秒<br />返回：计时器的 ID |
| [==clearTimeout()==](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/clearTimeout) | 清除指定 ID 的计时器                             | 传入计时器的 ID                                              |
| [==setInterval()==](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/setInterval) | 设置一个计时器<br />每隔一段时间自动执行某个函数 | 参数 1：函数，无参，this 指向 window<br />参数 2：时间，毫秒<br />返回：计时器的 ID |
| [==clearInterval()==](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/clearInterval) | 清除指定 ID 的计时器                             | 传入计时器的 ID                                              |
| [`alert()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/alert) | 弹出提示框                                       | 不同的操作系统外观有差异                                     |
| [`confirm()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/confirm) | 弹出确认框                                       | 不同的操作系统外观有差异                                     |

### window.location

https://developer.mozilla.org/zh-CN/docs/Web/API/Location

提供地址栏的相关操作

| API                                                          | 含义                             | 备注                   |
| ------------------------------------------------------------ | -------------------------------- | ---------------------- |
| [==Location.href==](https://developer.mozilla.org/zh-CN/docs/Web/API/Location/href) | 获取或设置页面当前地址           | 设置地址回导致页面跳转 |
| [`Location.protocol`](https://developer.mozilla.org/en-US/docs/Web/API/Location/protocol) | 获取或设置地址中的协议部分       |                        |
| [`Location.host`](https://developer.mozilla.org/zh-CN/docs/Web/API/Location/host) | 获取或设置地址中的主机名和端口号 |                        |
| [`Location.hostname`](https://developer.mozilla.org/zh-CN/docs/Web/API/Location/hostname) | 获取或设置地址中的主机名         |                        |
| [`Location.port` ](https://developer.mozilla.org/en-US/docs/Web/API/Location/port) | 获取或设置地址中的端口号         |                        |
| [`Location.pathname` ](https://developer.mozilla.org/en-US/docs/Web/API/Location/pathname) | 获取或设置地址中的路径部分       |                        |
| [`Location.search`](https://developer.mozilla.org/zh-CN/docs/Web/API/Location/search) | 获取或设置地址中的参数部分       |                        |
| [`Location.hash`](https://developer.mozilla.org/zh-CN/docs/Web/API/Location/hash) | 获取或设置地址中的 hash 部分     |                        |
| [`Location.reload()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Location/reload) | 刷新页面                         |                        |

### window.history

https://developer.mozilla.org/zh-CN/docs/Web/API/History

提供当前窗口历史记录的操作

| API                                                          | 含义                                             | 备注       |
| ------------------------------------------------------------ | ------------------------------------------------ | ---------- |
| [`History.back()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/back) | 后退                                             |            |
| [`History.forward()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/forward) | 前进                                             |            |
| [`History.go()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/go) | 根据相对当前页面的偏移量，<br />进入指定的记录页 |            |
| [`History.pushState()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/pushState) | 在历史记录中添加一条记录                         | 页面不刷新 |
| [`History.replaceState()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/replaceState) | 替换当前记录                                     | 页面不刷新 |

## DOM

DOM 是一个对象，它对应到 HTML 中的节点

<img src="http://mdrs.yuanjin.tech/img/20211215164209.png" alt="image-20211215164209559" style="zoom:50%;" />

### 获取 dom

| API                                                          | 含义                    | 备注                                                         |
| ------------------------------------------------------------ | ----------------------- | ------------------------------------------------------------ |
| document.getElementById()                                    | 根据元素 id 获取 dom    | 得到单个 dom                                                 |
| document.getElementsByTagName()<br />dom.getElementsByTagName() | 根据元素名称获取 dom    | 得到 dom 的伪数组                                            |
| document.getElementsByClassName()<br />dom.getElementsByClassName() | 根据元素类样式获取 dom  | 得到 dom 的伪数组                                            |
| ==document.querySelector()==<br />==dom.querySelector()==    | 根据 CSS 选择器获取 dom | 得到第一个匹配的 dom                                         |
| ==document.querySelectorAll()==<br />==dom.querySelectorAll()== | 根据 CSS 选择器获取 dom | 得到所有匹配的 dom<br />伪数组                               |
| ==document.documentElement==                                 | 获取 html 元素          |                                                              |
| document.body                                                | 获取 body               |                                                              |
| document.head                                                | 获取 head               |                                                              |
| ==dom.children==                                             | 获取 dom 的子元素       | 得到 dom 的伪数组                                            |
| dom.childNodes                                               | 获取 dom 的子节点       | 得到 dom 节点的伪数组<br />关于节点对象点[这里](https://developer.mozilla.org/zh-CN/docs/Web/API/Node) |
| dom.previousElementSibling                                   | 得到 dom 前一个兄弟元素 |                                                              |
| dom.nextElementSibling                                       | 得到 dom 后一个兄弟元素 |                                                              |
| ==dom.parentElement==                                        | 得到 dom 的父元素       |                                                              |

### 创建 dom

| API                          | 含义                | 备注         |
| ---------------------------- | ------------------- | ------------ |
| ==document.createElement()== | 创建一个 dom 并返回 | 传入元素名称 |

### 更改 dom 结构

这里是指更改文档树（DOM 树）

| API                                                          | 含义                                              | 备注          |
| ------------------------------------------------------------ | ------------------------------------------------- | ------------- |
| ==dom.remove()==                                             | 从文档树中删除 dom                                | 不是删除对象  |
| dom.removeChild()                                            | 删除 dom 的某个子节点                             | 传入 dom 对象 |
| [`dom.insertBefore()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Node/insertBefore) | 在 dom 的子节点中，添加一个新节点到另一个节点之前 |               |
| ==dom.appendChild()==                                        | 添加一个新节点到 dom 的子节点末尾                 | 传入 dom 对象 |

### dom 属性

本节的「属性」，是指 HTML 元素的「属性」

属性有两种：

- 标准属性：HTML 元素本身拥有的属性，例如：
  - a 元素的 href、title
  - input 的 value
  - img 的 src
  - ......
- 自定义属性：HTML 元素标准中未定义的属性

**所有标准属性均可通过 `dom.属性名` 得到，其中：**

- 布尔属性会被自动转换为 boolean

- 路径类的属性会被转换为绝对路径

- 标准属性始终都是存在的，不管你是否有在元素中属性该属性

- class 由于和关键字重名，因此需要使用 className

**所有的自定义属性均可通过下面的方式操作：**

- `dom.setAttribute(name, value)`，设置属性键值对
- `dom.getAttribute(name)`，获取属性值

自定义属性和元素源码书写是对应的，可以尝试获取 a 元素的 href 属性对比标准属性，看看有什么不同。

### dom 内容

| API               | 含义                       | 备注                           |
| ----------------- | -------------------------- | ------------------------------ |
| ==dom.innerText== | 获取或设置元素文本内容     | 设置时会自动进行 HTML 实体编码 |
| ==dom.innerHTML== | 获取或设置元素的 HTML 内容 |                                |

### dom 样式

在 JS 中，有两种样式：

- 内联样式：元素的 style 属性中书写的样式
- 计算样式（最终样式）：元素最终计算出来的样式

**JS 可以获取内联样式和计算样式，但只能设置内联样式**

下面罗列了样式的常见操作：

- `dom.style`：获取元素的内联样式，得到样式对象
  - 对象中的所有样式属性均可以被赋值，赋值后即可应用样式到元素的 style 中
- `getComputedStyle(dom)`：获取元素的计算样式，得到一个样式对象
  - 该样式对象中的属性是只读的，无法被重新赋值

关于**样式对象**，注意：

- 当给样式赋值为空字符串时，相当于删除内联样式
- 当给样式的赋值不合法时，赋值语句无效，不会报错
- CSS 的短横线命名法，在属性名中表现为驼峰命名法

### 监听 dom 事件

监听事件可以描述为一句话：

**某个 DOM**发生了**某件事**之后，我需要做**某些处理**

- 某个 DOM：监听谁？
- 某件事（事件类型）：它发生了什么？
- 某些处理（处理函数）：我要做什么？

下面是一段事件监听代码：

```js
// 为dom注册点击事件，当被点击时，自动运行事件处理函数
dom.onclick = function () {
  console.log('dom 被点击了');
};
```

#### 事件类型

https://developer.mozilla.org/zh-CN/docs/Web/Events

##### 表单类事件

| 事件名称   | 触发时机                                                     | 备注                              |
| ---------- | ------------------------------------------------------------ | --------------------------------- |
| ==submit== | 表单被提交时触发                                             | 注册到 form 元素上                |
| ==input==  | 文本框改变后立即出发                                         | 注册到 input、textarea 上         |
| ==change== | 文本框改变后、失去焦点时触发<br />下拉列表、多选框、单选框改变后立即触发 | 注册到 input、select、textarea 上 |
| reset      | 表单被重置时触发                                             | 注册到 form 元素上                |
| focus      | 元素聚焦时触发                                               |                                   |
| blur       | 元素失去焦点时触发                                           |                                   |

##### 鼠标类事件

| 事件名称       | 触发时机                     | 备注 |
| -------------- | ---------------------------- | ---- |
| ==click==      | 鼠标按下抬起后触发           |      |
| contextmenu    | 右键菜单显示前触发           |      |
| ==mousedown==  | 鼠标按下时触发               |      |
| ==mouseup==    | 鼠标抬起时触发               |      |
| ==mousemove==  | 鼠标在元素上移动时触发       |      |
| ==mouseenter== | 鼠标进入元素时触发（不冒泡） |      |
| ==mouseleave== | 鼠标离开元素时触发（不冒泡） |      |
| mouseover      | 鼠标进入元素时触发（冒泡）   |      |
| mouseout       | 鼠标离开元素时触发（冒泡）   |      |
| wheel          | 鼠标滚轮滚动时触发           |      |

##### 键盘事件

| 事件名称 | 触发时机           | 备注 |
| -------- | ------------------ | ---- |
| keydown  | 某个键被按下时触发 |      |
| keyup    | 某个键被抬起时触发 |      |

#### 注册事件

JS 提供了三种方式注册事件

方式 1：将事件注册写到元素上，这种方式基本被弃用

```html
<button onclick="js代码">按钮</button>
```

==方式 2：使用 dom 属性注册事件==

属性名为`on+事件类型`

```js
// 监听事件
dom.onclick = function () {
  // 处理函数
};
// 移除监听事件
dom.onclick = null;
```

这种方式的特点是：

- 优点：易于监听、覆盖、移除
- 缺点：只能注册一个处理函数
- 缺点：某些事件不支持用这种方式注册

==方式 3：使用 addEventListener 方法注册事件==

```js
dom.addEventListener('click', function () {
  // 处理函数1
});
dom.addEventListener('click', function () {
  // 处理函数2
});
```

这是最完美的事件注册方式，如果要移除用这种方式注册的事件，需要改写代码

```js
function handler1() {
  // 处理函数1
}
function handler2() {
  // 处理函数2
}

dom.addEventListener('click', handler1);
dom.addEventListener('click', handler2);

dom.removeEventListener('click', handler1); // 移除监听函数1
```

#### 事件处理函数

当事件发生时，会自动调用事件处理函数，并向函数传递一个参数，该参数称之为事件对象，里面包含了事件发生的相关信息，比如鼠标位置、键盘按键等等

```js
dom.addEventListener('click', function (e) {
  console.log(e.clientX); //打印鼠标的横坐标
});
```

常见的事件对象有：[鼠标事件对象](https://developer.mozilla.org/zh-CN/docs/Web/API/MouseEvent)、[键盘事件对象](https://developer.mozilla.org/zh-CN/docs/Web/API/KeyboardEvent/KeyboardEvent)

另外，在事件处理函数中，`this`始终指向注册事件的 dom

### dom 进阶

#### 事件默认行为

某些元素的某些事件，浏览器会有自己的默认行为

比如：

- a 元素的 click 事件，浏览器会跳转页面
- form 元素的 submit 事件，浏览器会提交表单，最终导致页面刷新
- 文本框的 keydown 事件，浏览器会将按键文本显示到文本框中
- ......

如果我们要阻止浏览器的默认行为，就需要在对应时间中加入以下代码：

```js
// e为事件对象
e.preventDefault();
```

#### dom 尺寸和位置

<img src="http://mdrs.yuanjin.tech/img/20211216104505.png" alt="尺寸1" style="zoom:50%;" />

![尺寸2](http://mdrs.yuanjin.tech/img/20220406223123.png)

![尺寸3](http://mdrs.yuanjin.tech/img/20220213212313.png)

<img src="http://mdrs.yuanjin.tech/img/20211216104405.jpg" alt="尺寸4" style="zoom:50%;" />

> 调用`dom.scrollTo(x, y)`可以设置元素的滚动位置，x 和 y 分别表示 scrollLeft 和 scrollTop
>
> 该方法通用元素回到元素顶部`dom.scrollTo(0, 0)`
>
> 如果要监听元素的滚动，可以监听事件类型：==scroll==

[Element.getBoundingClientRect()](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/getBoundingClientRect)

![element-box-diagram](http://mdrs.yuanjin.tech/img/202210151248555.png)

> 上图中的 top、left、right、bottom 均相对于视口

#### 事件传播机制

<img src="http://mdrs.yuanjin.tech/img/20211216105521.jpg" alt="事件流" style="zoom: 50%;" />

```js
// 在冒泡阶段触发
div.onclick = function () {};

// 在捕获阶段触发事件
div.addEventListener('click', function () {}, true);

// 在冒泡阶段触发事件（默认）
div.addEventListener('click', function () {}, false);
```

```js
// 事件处理函数
function handler(e) {
  e.target; // 获取事件源（目标阶段的dom）
  e.stopPropagation(); // 阻止事件继续冒泡
}
```



# 正则表达式

## 创建正则对象

```js
// 构造函数
new RegExp('规则', '标识')
// 字面量书写
/规则/标识
```

## 正则常用方法

```js
// reg是正则对象
reg.test('字符串'); // 验证字符串是否满足规则
```

```js
// reg是正则对象，str是字符串
str.replace(reg, '替换目标'); // 将字符串中匹配正则的部分替换为目标

// 将字符串中匹配正则的部分传入到回调函数的参数中，将函数的返回结果进行替换
str.replace(reg, function(s){
  return '替换目标'
})
```

## 标识

| 标识字符 | 含义                                     |
| -------- | ---------------------------------------- |
| i        | 不区分大小写                             |
| g        | 全局匹配，如果没有此标识，只会匹配第一个 |
| m        | 多行匹配                                 |

## 规则

详见：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions

### 字符匹配规则

| 规则书写               | 含义                                     |
| ---------------------- | ---------------------------------------- |
| `直接书写一个普通字符` | 匹配书写的字符                           |
| `[字符规则]`           | 匹配[]中出现的所有字符规则               |
| `[^字符串规则]`        | 匹配[]中**没有**出现的字符规则           |
| `.`                    | 匹配任意字符                             |
| `\d`                   | 匹配数字，等价于 `[0-9]`                 |
| `\D`                   | 匹配非数字                               |
| `\s`                   | 匹配空白字符，包括空格、回车、换行、制表 |
| `\S`                   | 匹配所有非空白字符                       |
| `\w`                   | 匹配单词字符，等价于 `[A-Za-z0-9_]`      |
| `\W`                   | 匹配非单词字符，等价于 `[^A-Za-z0-9_]`   |
| `^`                    | 匹配字符串开始，写到规则开始位置         |
| `$`                    | 匹配字符串结束，写到规则结束位置         |
| `\\`                   | 匹配`\`                                  |

### 连续的规则

多个规则可以连续书写，用以匹配多个字符，例如：

```js
/\d[a-zA-Z]/  // 匹配以1个数字紧跟一个字母
```

若多个规则是一个或者的关系，使用`|`分割

```js
/\d[a-zA-Z]|[a-zA-Z]\d/ // 匹配以1个数字紧跟一个字母，或者一个字母紧跟一个数字
```

### 规则的重复（量词）

一个或一段规则之后，可以紧跟一个量词，表示前面的规则出现的次数

```js
/[a-zA-Z]\d{3}/  // 匹配1个字母，后面跟上连续的3个数字，{3}是量词，应用的规则是\d
```

```js
/([a-zA-Z]\d){3}/  // {3}是量词，应用的规则是 [a-zA-Z]\d
```

| 量词     | 含义                         |
| -------- | ---------------------------- |
| `{n}`    | 出现n次                      |
| `{n, m}` | 出现n-m次                    |
| `{n,}`   | 至少出现n次                  |
| `*`      | 出现0次或多次，等价于`{0,}`  |
| `?`      | 出现0次或一次，等价于`{0,1}` |
| `+`      | 出现1次或多次，等价于`{1,}`  |

# 浏览器的渲染流程

## 解析HTML

浏览器从网络或本地文件中获取到HTML源代码，然后从上到下的解析源代码

若解析过程中，读取到CSS或JS，**停止解析（阻塞）**，转而解析CSS或执行JS

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link rel="stylesheet" href="./css/index.css">
</head>
<body>
  <h1>Hello World!</h1>
  <script src="./js/index.js"></script>
  <p>Lorem</p>
</body>
</html>
```

<img src="http://mdrs.yuanjin.tech/img/20211222115309.png" alt="image-20211222115303832" style="zoom:50%;" />

> **为什么要将CSS写到页面的开头，而JS写到页面的最后？**
>
> 将CSS写到页面开头，是为了让浏览器尽快读取并解析样式，避免给用户看到丑陋的页面，也是为了避免页面闪烁
>
> 将JS代码写到最后，是为了让浏览器尽快呈现页面给用户，然后再执行JS完成交互功能

## 生成DOM树

**浏览器会一边解析HTML，一边生成DOM树**，我们在JS中获取到的DOM就是DOM树中的DOM

<img src="https://xiejie-typora.oss-cn-chengdu.aliyuncs.com/2021-11-20-091428.png" alt="image-20211120171428854" style="zoom:50%;" />

> 当DOM树完全生成好后，会触发`DOMContentLoaded`事件
>
> ```js
> document.addEventListener("DOMContentLoaded", function() {
> console.log("DOM树已全部生成完毕");
> });
> ```
>
> 当页面中的所有外部资源全部加载完毕后，会触发`load`事件
>
> ```js
> window.onload = function(){
> console.log("所有资源已加载完成");
> }
> ```
>
> `load`事件也可以针对单个外部资源使用，资源加载完成后触发

## 生成渲染树

**浏览器一边生成DOM树，一边计算DOM树中每个节点的样式规则，最终形成渲染树**。

CSS属性的计算过程，发生在这一个步骤

<img src="https://xiejie-typora.oss-cn-chengdu.aliyuncs.com/2021-11-20-091551.png" alt="image-20211120171550663" style="zoom:50%;" />

## 布局 layout / 重排 reflow

这个步骤又称之为**reflow（回流、重排）**，是指浏览器一边生成渲染树，一边计算每个元素最终的尺寸和位置

完成后，页面中的所有元素的位置和尺寸就确定下来了，即将被渲染到页面。

这个步骤会在页面之后的运行过程中不断的重复，**下面的JS操作均会导致reflow**：

- 获取元素的尺寸和位置
- 直接或间接改变元素的尺寸和位置

> reflow非常耗时，浏览器为了提升性能，对JS中**连续**导致reflow的代码，把reflow的时间点延迟到结束后进行，但在此过程中，如果遇到了获取尺寸和位置的代码，浏览器会迫不得已立即reflow
>
> ```js
> dom.style.width = '100px'
> dom.style.height = '200px'
> dom.style.left = '10px'
> dom.style.top = '10px'
> ```
>
> <img src="http://mdrs.yuanjin.tech/img/20211222145016.png" alt="image-20211222145016258" style="zoom:50%;" />
>
> ```js
> dom.style.width = '100px'
> dom.style.height = '200px'
> dom.clientHeight; // 读取高度，导致强行reflow
> dom.style.left = '10px'
> dom.style.top = '10px'
> ```
>
> <img src="http://mdrs.yuanjin.tech/img/20211222145207.png" alt="image-20211222145207563" style="zoom:50%;" />

## 重绘 repaint

浏览器一边reflow，一边进行生成对应的图形绘制到页面，绘制的过程称之为repaint

**所有会导致reflow的代码，均会导致repaint**

绘制的过程是靠GPU完成的，速度非常快，因此，**相对于导致reflow的代码，仅会导致repaint的代码效率会高出很多**

凡是不会影响盒子排列，仅影响盒子外观的代码都不会导致reflow，仅导致repaint，例如：

- 改变背景颜色
- 改变字体颜色
- 圆角边框
- 背景图
- ......



# 异常

> 本节课的重点是**异常的分类**
>
> 剩余两部分的知识，绝大部分情况下都用不到，除非你要写一些 *高端* 的代码

![image-20211222175234095](http://mdrs.yuanjin.tech/img/20211222175234.png)

**异常并非坏事，它可以让开发人员及时发现错误、定位错误，甚至在某些时候，我们还需要故意的抛出异常**

## 异常的分类

在JS中，异常表现为一个对象，不同的对象表达了不同的异常类型，不同类型的异常对应到不同的错误

| 异常类型           | 含义                                         |
| ------------------ | -------------------------------------------- |
| **SyntaxError**    | 语法错误                                     |
| **ReferenceError** | 引用错误，往往是使用了未定义的变量或函数     |
| **TypeError**      | 类型错误，往往是使用了一个对象中不存在的成员 |

**每个异常都是一个对象，通过对应的构造函数创建**

> 所有的异常构造器都继承自Error，更多信息参见[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Error)

当代码运行过程中出现错误时，JS会：

1. 自动创建对应的异常对象，抛出错误
2. 程序终止运行
3. 控制台中会显示异常对象

每个异常对象都至少记录了**两个关键信息**：

1. 错误消息描述：描述异常出现的原因
2. 调用堆栈信息：描述异常出现的位置

## 捕获异常

捕获异常就是处理错误，当错误发生后，我们对错误进行相应的处理，让程序不至于终止

```js
try{
  // 代码1
}
catch(err){
  // 代码2：当代码1出现异常后，会执行这里的代码，异常对象会传递给err
}
finally{
  // 代码3：可省略。无论是否有异常，都会执行
}

// 无异常的执行顺序：代码1 --> 代码3
// 有异常的执行顺序：代码1 --> 出现异常，中断代码1的执行 --> 代码2 --> 代码3
```

**在绝大部分时候，我们都无须捕获异常，除非满足以下要求：**

1. 我们能够预知某段代码会出现异常
2. 我们知道出现异常后要做什么

上面的条件任意一个不满足，都不应该处理异常

**永远不能为了不报错而捕获异常！**

下面是一段可能使用异常捕获的伪代码

```js
try {
  var heros = network.getHeros(); // 从网络获取王者荣耀英雄数据，得到英雄数组
  createHTML(heros); // 将数组生成HTML
}
catch(err) {
  // 出现网络故障，给用户显示一个提示框
  showErrorDialog('网络故障，请检查您的网络是否连接正常。故障原因：' + err.message);
}
```

## 手动抛出异常

不仅浏览器会自动给我们抛出异常，我们还可以手动的抛出异常

```js
throw 异常对象; // 当代码运行到这里，会终止执行，抛出异常对象，效果和浏览器抛出的错误完全一样
```

当编写函数时，如果满足下面三个条件，就可以选择抛出异常：

1. 预知执行过程中可能会出现某种错误
2. 浏览器不会抛出这个错误
3. 该函数无法处理这个错误

下面展现了一个需要抛出异常的例子

```js
/**
 * 得到两个数字之和
 * 若传递的不是数字，则会抛出TypeError
 * @param {number} a 数字1
 * @param {number} b 数字2
 * @return {number} 两数之和
 */
function sum(a, b){
  if(typeof a !== 'number' || typeof b !== 'number'){
    throw new TypeError('必须传入两个数字才能求和')
  }
  return a + b;
}
```

**规范：如果某个函数需要抛出异常，一定要在函数的文档注释中阐述清楚**

## 练习

说出下面的错误描述的含义，以及该错误发生的原因

![image-20211223103308973](http://mdrs.yuanjin.tech/img/20211223103309.png)

![image-20211223103332002](http://mdrs.yuanjin.tech/img/20211223103332.png)

<img src="http://mdrs.yuanjin.tech/img/20211223103347.png" alt="image-20211223103347139" style="zoom:50%;" />

<img src="http://mdrs.yuanjin.tech/img/20211223103450.png" alt="image-20211223103450241" style="zoom:50%;" />

