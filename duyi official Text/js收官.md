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

## 知识回顾-数据的表达1



和HTML、CSS不同，JS是一门 _命令式编程语言_，和其他命令式编程语言一样，它的本质是**处理数据**

JS 提供了三种方式来表达一个数据：

- 变量
- 字面量
- 表达式

程序中任何需要数据的地方，都可以使用上面任意一种数据表达。

### 注意点

#### 标识符

程序中有些可以自行命名的地方，称之为**标识符**

> 常见的标识符有：变量名、函数名、参数名

_js_ 的标识符必须符合以下规则：

- 允许数字、字母、下划线、\$符号
- 不得以数字开头
- 不能和关键字冲突
- 建议使用驼峰命名法

一个完整的程序中，会涉及成百上千的标识符，好的名称不仅可以减少名称冲突，更有利于程序的阅读和维护。

名称要做到**望文知意**

#### 转义符

| 转义符 | 含义           |
| ------ | -------------- |
| `\'`   | 普通英文单引号 |
| `\"`   | 普通英文双引号 |
| `\r`   | 回车           |
| `\n`   | 换行           |

> 小技巧：常用`\r\n`表示换行



## 知识回顾-数据的表达2



本节课主要回顾对象的表达

### 注意点

#### 数据类型

原始类型：number、string、boolean、null、undefined

引用类型：对象（包含普通对象、数组、函数）

#### 对象的原始写法

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

## 知识回顾-数据的表达3

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

## 知识回顾-数据的运算



### 运算符

#### 算术（数学）运算

支持：加(+)、减(-)、乘(*)、除(/)、求余(%)

值得注意的是，+和-可以放到单个数据的前面，表示正负。

算术运算的表达式一定返回数字，可以利用其特点做类型转换，参考[类型的隐式转换](#类型的隐式转换)

#### 字符串拼接

当`+`的两端有一个是字符串时，不再进行算术运算，而变为字符串拼接

表达式一定返回string，可以利用其特点做类型转换，参考[类型的隐式转换](#类型的隐式转换)

#### 赋值运算

涉及的运算符：`=` `+=` `*=` `/=` `-=` `%=`。

其中，`a += xxx`，等效于`a = a + (xxx)`，其他类似

> 小贴士
> 赋值表达式始终返回赋值结果，我们可以利用该特点完成连续赋值
>
> ```js
> // 将 3 同时赋值给 a、b
> a = b = 3;
> ```

#### 比较运算

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

#### 逻辑运算

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


### 布尔判定

所有需要判断真假的地方都会使用下面的规则

| 数据                                      | 判定  |
| ----------------------------------------- | ----- |
| `false` `null` `undefined` `0` `NaN` `''` | false |
| 剩余所有数据                              | true  |

### 类型的隐式转换

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



## 知识回顾-流程的切割

### 函数的作用

使用函数切割流程，不仅可以减少重复代码、还可以有效的降低整体复杂度

<img src="http://mdrs.yuanjin.tech/img/20211209124426.png" alt="image-20211209124426753" style="zoom:50%;" />

### 函数的常见问题

#### **如何理解函数的参数、返回值、函数体？**

<img src="http://mdrs.yuanjin.tech/img/20211209125120.png" alt="image-20211209125120817" style="zoom:50%;" />

参数：表示完成流程所需的**必要信息**

返回值：表示完成流程后**产生的结果**

函数体：表示具体的流程

**函数的参数、返回值只取决于函数的作用，与函数体无关**

#### 为什么我觉得有了函数之后，程序反而变得更复杂了？

函数的核心作用，是为了让某一段复杂的流程变得简单。

如果在函数的帮助下，反而觉得流程变得复杂了，极有可能的原因是开发思想没有做相应的切割，导致思想负担过重。

**始终记住以下两点**：

1. 定义函数时，只需要考虑这个函数如何实现即可，完全不需要考虑其他无关的东西。
2. 调用函数时，只需要考虑向其传递什么参数，如何使用它的返回结果，完全无需考虑函数的具体实现。

函数具有**三要素**：函数名、参数、返回值

只要具备三要素，就能书写函数体；只要具备三要素，就能完成函数调用。

#### 学习函数时不知道该如何切割流程怎么办？

要完成一个函数声明，分为两步：

1. 设计函数

   设计函数就是如何切割流程，具体来说就是设计出函数的三要素，这一步是最难的，目前无须同学们掌握，老师会帮你把函数设计好。

2. 书写函数体

   根据设计的三要素完成函数体，这一步就是现阶段练习的重点。

## 数据的作用域

1. JS有两种作用域：全局作用域和函数作用域
   - 内部的作用域能访问外部，反之不行。访问时从内向外依次查找。
   - 如果在内部的作用域中访问了外部，则会产生闭包。
   - 内部作用域能访问的外部，取决于函数定义的位置，和调用无关
2. 作用域内定义的变量、函数声明会提升到作用域顶部



## 全局对象

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



## 原型

###  原型要解决的问题

<img src="http://mdrs.yuanjin.tech/img/20211210142340.png" alt="image-20211210142340406" style="zoom:50%;" />

上图中，通过构造函数可以创建一个用户对象

这种做法有一个严重的缺陷，就是每个用户对象中都拥有一个`sayHi`方法，对于每个用户而言，`sayHi`方法是完全一样的，没必要为每个用户单独生成一个。

要解决这个问题，必须学习原型

### 原型是如何解决的

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

## 这是啥？

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




## 原型链

### 什么是原型链

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

### 完整的链条

![image-20210903152359095](http://mdrs.yuanjin.tech/img/20210903152359.png)

### 对开发的影响

#### 在原型上更改会产生多大影响

更改构造函数的原型会对所有原型链上有该构造函数的原型的对象产生影响

#### 学会利用原型链判断类型

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

#### 学会创建空原型的对象

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




## 继承

### 会员系统

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

### 处理构造器内部的重复

可以将VIPUser构造器改写为

```js
function VIPUser(username, password, expires){
  User.call(this, username, password);
  this.expires = expires;
}
```

### 处理原型上的重复

只需要将原型链设置为下面的结构即可

<img src="http://mdrs.yuanjin.tech/img/20211214155347.png" alt="image-20211214155342118" style="zoom:50%;" />

仅需一句代码即可

```js
Object.setPrototypeOf(VIPUser.prototype, User.prototype)
```

至此，完美的解决了之前提到的两处重复代码的问题

### 这和继承有什么关系

继承是面向对象的概念，它描述了两个对象类型（类，构造函数）之间的关系

如果在逻辑上可以描述为：A不一定是B，但B一定是A，则：B继承A、A派生B、A是B的父类、B是A的子类

**子类的实例应该自动拥有父类的所有成员**

继承具有两个特性：

- 单根性：子类最多只有一个父类
- 传递性：间接父类的成员会传递到子类中

### 如何在JS中封装继承

```js
function inherit(Child, Parent){
  // 在原型链上完成继承 
  Object.setPrototypeOf(Child.prototype, Parent.prototype);
}
```

> 过去，由于没有提供更改隐式原型的方法，因此这一过程会比较复杂。那时候，我们使用一种称之为「圣杯模式」的办法来达到相同的目的，这里不做介绍。



## 标准库

### 包装类

如果尝试着把原始类型（number、string、boolean）当做对象使用，JS会自动将其转换为对应包装类的实例

#### Number

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

#### String

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

#### 数学

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

### 日期

#### 时间基础知识

##### 单位

| 单位               | 名称 | 换算                  |
| ------------------ | ---- | --------------------- |
| hour               | 小时 | 1 day = 24 hours      |
| minute             | 分钟 | 1 hour = 60 minutes   |
| second             | 秒   | 1 minute = 60 seconds |
| millisecond （ms） | 毫秒 | 1 second = 1000 ms    |
| nanosecond （ns）  | 纳秒 | 1 ms = 1000 ns        |

##### GMT和UTC

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

##### Unix 时间戳

> Unix 时间戳（Unix Timestamp）是Unix系统最早提出的概念

它将UTC时间1970年1月1日凌晨作为起始时间，到指定时间经过的秒数（毫秒数）

##### 程序中的时间处理

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

### 对象

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object

| API                                                          | 含义                                     | 备注         |
| ------------------------------------------------------------ | ---------------------------------------- | ------------ |
| [Object.assign()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) | 将多个对象的属性混合到一起               | 后面覆盖前面 |
| [Object.getPrototypeOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf) | 获取一个对象的隐式原型                   |              |
| [Object.setPrototypeOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/setPrototypeOf) | 设置一个对象的隐式原型                   |              |
| [Object.create()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create) | 创建一个新对象，同时设置新对象的隐式原型 |              |

### 数组

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



### 函数

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function

| API                                                          | 含义               | 备注                     |
| ------------------------------------------------------------ | ------------------ | ------------------------ |
| [Function.prototype.apply()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) | 执行函数，绑定this | 参数列表以数组的形式传递 |
| [Function.prototype.call()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call) | 执行函数，绑定this | 参数列表依次传递         |



## WebAPI

和标准库不同，WebAPI 是**浏览器**提供的一套 API，用于操作浏览器窗口和界面

WebAPI 中包含两个部分：

- BOM：Browser Object Model，浏览器模型，提供和浏览器相关的操作
- DOM：Document Object Model，文档模型，提供和页面相关的操作

<img src="http://mdrs.yuanjin.tech/img/20211215154644.png" alt="image-20211215154639275" style="zoom:50%;" />

### BOM

BOM 提供了一系列的对象和函数，提供和浏览器本身相关的操作

#### window

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

#### window.location

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

#### window.history

https://developer.mozilla.org/zh-CN/docs/Web/API/History

提供当前窗口历史记录的操作

| API                                                          | 含义                                             | 备注       |
| ------------------------------------------------------------ | ------------------------------------------------ | ---------- |
| [`History.back()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/back) | 后退                                             |            |
| [`History.forward()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/forward) | 前进                                             |            |
| [`History.go()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/go) | 根据相对当前页面的偏移量，<br />进入指定的记录页 |            |
| [`History.pushState()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/pushState) | 在历史记录中添加一条记录                         | 页面不刷新 |
| [`History.replaceState()`](https://developer.mozilla.org/zh-CN/docs/Web/API/History/replaceState) | 替换当前记录                                     | 页面不刷新 |

### DOM

DOM 是一个对象，它对应到 HTML 中的节点

<img src="http://mdrs.yuanjin.tech/img/20211215164209.png" alt="image-20211215164209559" style="zoom:50%;" />

#### 获取 dom

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

#### 创建 dom

| API                          | 含义                | 备注         |
| ---------------------------- | ------------------- | ------------ |
| ==document.createElement()== | 创建一个 dom 并返回 | 传入元素名称 |

#### 更改 dom 结构

这里是指更改文档树（DOM 树）

| API                                                          | 含义                                              | 备注          |
| ------------------------------------------------------------ | ------------------------------------------------- | ------------- |
| ==dom.remove()==                                             | 从文档树中删除 dom                                | 不是删除对象  |
| dom.removeChild()                                            | 删除 dom 的某个子节点                             | 传入 dom 对象 |
| [`dom.insertBefore()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Node/insertBefore) | 在 dom 的子节点中，添加一个新节点到另一个节点之前 |               |
| ==dom.appendChild()==                                        | 添加一个新节点到 dom 的子节点末尾                 | 传入 dom 对象 |

#### dom 属性

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

#### dom 内容

| API               | 含义                       | 备注                           |
| ----------------- | -------------------------- | ------------------------------ |
| ==dom.innerText== | 获取或设置元素文本内容     | 设置时会自动进行 HTML 实体编码 |
| ==dom.innerHTML== | 获取或设置元素的 HTML 内容 |                                |

#### dom 样式

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

#### 监听 dom 事件

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

##### 事件类型

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

##### 注册事件

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

##### 事件处理函数

当事件发生时，会自动调用事件处理函数，并向函数传递一个参数，该参数称之为事件对象，里面包含了事件发生的相关信息，比如鼠标位置、键盘按键等等

```js
dom.addEventListener('click', function (e) {
  console.log(e.clientX); //打印鼠标的横坐标
});
```

常见的事件对象有：[鼠标事件对象](https://developer.mozilla.org/zh-CN/docs/Web/API/MouseEvent)、[键盘事件对象](https://developer.mozilla.org/zh-CN/docs/Web/API/KeyboardEvent/KeyboardEvent)

另外，在事件处理函数中，`this`始终指向注册事件的 dom

#### dom 进阶

##### 事件默认行为

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

##### dom 尺寸和位置

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

##### 事件传播机制

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



## 正则表达式

### 创建正则对象

```js
// 构造函数
new RegExp('规则', '标识')
// 字面量书写
/规则/标识
```

### 正则常用方法

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

### 标识

| 标识字符 | 含义                                     |
| -------- | ---------------------------------------- |
| i        | 不区分大小写                             |
| g        | 全局匹配，如果没有此标识，只会匹配第一个 |
| m        | 多行匹配                                 |

### 规则

详见：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions

#### 字符匹配规则

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

#### 连续的规则

多个规则可以连续书写，用以匹配多个字符，例如：

```js
/\d[a-zA-Z]/  // 匹配以1个数字紧跟一个字母
```

若多个规则是一个或者的关系，使用`|`分割

```js
/\d[a-zA-Z]|[a-zA-Z]\d/ // 匹配以1个数字紧跟一个字母，或者一个字母紧跟一个数字
```

#### 规则的重复（量词）

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

## 浏览器的渲染流程

### 解析HTML

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

### 生成DOM树

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

### 生成渲染树

**浏览器一边生成DOM树，一边计算DOM树中每个节点的样式规则，最终形成渲染树**。

CSS属性的计算过程，发生在这一个步骤

<img src="https://xiejie-typora.oss-cn-chengdu.aliyuncs.com/2021-11-20-091551.png" alt="image-20211120171550663" style="zoom:50%;" />

### 布局 layout / 重排 reflow

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

### 重绘 repaint

浏览器一边reflow，一边进行生成对应的图形绘制到页面，绘制的过程称之为repaint

**所有会导致reflow的代码，均会导致repaint**

绘制的过程是靠GPU完成的，速度非常快，因此，**相对于导致reflow的代码，仅会导致repaint的代码效率会高出很多**

凡是不会影响盒子排列，仅影响盒子外观的代码都不会导致reflow，仅导致repaint，例如：

- 改变背景颜色
- 改变字体颜色
- 圆角边框
- 背景图
- ......



## 异常

> 本节课的重点是**异常的分类**
>
> 剩余两部分的知识，绝大部分情况下都用不到，除非你要写一些 *高端* 的代码

![image-20211222175234095](http://mdrs.yuanjin.tech/img/20211222175234.png)

**异常并非坏事，它可以让开发人员及时发现错误、定位错误，甚至在某些时候，我们还需要故意的抛出异常**

### 异常的分类

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

### 捕获异常

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

### 手动抛出异常

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

### 练习

说出下面的错误描述的含义，以及该错误发生的原因

![image-20211223103308973](http://mdrs.yuanjin.tech/img/20211223103309.png)

![image-20211223103332002](http://mdrs.yuanjin.tech/img/20211223103332.png)

<img src="http://mdrs.yuanjin.tech/img/20211223103347.png" alt="image-20211223103347139" style="zoom:50%;" />

<img src="http://mdrs.yuanjin.tech/img/20211223103450.png" alt="image-20211223103450241" style="zoom:50%;" />



# js提升

## 零碎的改动

### 严格模式

此为ES5新增语法

参考：https://www.runoob.com/js/js-strict.html

参考：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode

### let 和 const

ES6建议不再使用`var`定义变量，而使用`let`定义变量，`const`定义常量

```js
let a = 1; // 使用 let 定义变量
a = 2; // 变量的值是可修改的

const b = 1; // 使用 const 定义常量
b = 2; // ❌ 报错，常量的值不可修改
```

**对于开发的影响：均使用const，实在需要修改变量，再改为let**

无论是let还是const，它们均解决了长久以来变量定义的问题，使用它们定义变量，具有以下特点：

- 全局定义的变量不再作为属性添加到全局对象中

- 在变量定义之前使用它会报错

- 不可重复定义同名变量

- 使用`const`定义变量时，必须初始化

- 变量具有块级作用域，在代码块之外不可使用

  注意，在for循环中使用let定义变量，变量所在的作用域是循环体，因此在循环外不能使用。另外，for循环会对该变量做特殊处理，让每次循环使用的都是一个独立的循环变量，这可以解决JS由来已久的问题。

  ```js
  // 过去的问题
  for(var i = 0; i < 3; i++){
    setTimeout(function(){
      console.log(i)
    }, 1000)
  }
  // 输出：3 3 3
  
  // 过去的解决办法：IIFE
  for(var i = 0; i < 3; i++){
    (function(i){
      setTimeout(function(){
        console.log(i)
      }, 1000)
    })(i)
  }
  // 输出：0 1 2
  
  // 现在的做法
  for(let i = 0; i < 3; i++){
    setTimeout(function(){
      console.log(i)
    }, 1000)
  }
  // 输出：0 1 2
  ```

### 幂运算

```js
2 ** 3  // 8
2 ** 4  // 16
```

### 字符串新增API

| API                                                          | 含义                         |
| ------------------------------------------------------------ | ---------------------------- |
| [String.prototype.includes(s)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/includes) | 字符串中是否包含某个子串     |
| [String.prototype.trim()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim) | 去掉字符串首尾空白字符       |
| [String.prototype.trimStart()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trimstart) | 去掉字符串开始的空白字符     |
| [String.prototype.trimEnd()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trimend) | 去掉字符串末尾的空白字符     |
| [String.prototype.replaceAll(s, t)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replaceall) | 将字符串中**所有**的s替换为t |
| [String.prototype.startsWith(s)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/startswith) | 判断字符串是否以s开头        |
| [String.prototype.endsWith(s)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/endswith) | 判断字符串是否以s结尾        |
|                                                              |                              |

### 模板字符串

ES6提供了一种新的字符串字面量的书写方式，即模板字符串，写法为

```js
`字符串内容`
```

模板字符串可以轻松的实现换行和拼接

```js
const user = { name: 'monica', age: 17 }
const s1 = `姓名：${user.name}，年龄：${user.age}
my name is ${user.name}`;
// 等同于
const s2 = '姓名：' + user.name + '，年龄：' + user.age + '\nmy name is ' + user.name

/* 
 * s1和s2均为：
 * 姓名：monica，年龄：17
 * my name is monica
 */
```

在需要换行或拼接时，模板字符串远胜于普通字符串

通常，我们可以使用模板字符串拼接html

```js
const user = { name: 'monica', age: 17 }
const html = `
<div>
	<p><span class="k">姓名</span><span class="v">${user.name}</span></p>
	<p><span class="k">年龄</span><span class="v">${user.age}</span></p>
</div>
`;
/* 
 * <div>
 *  <p><span class="k">姓名</span><span class="v">monica</span></p>
 *  <p><span class="k">年龄</span><span class="v">17</span></p>
 * </div>
 */
```



## 数组

### for-of 循环

ES6提供了一种爽翻天的方式遍历各种数组和伪数组

示例1：

```js
const arr = ['a', 'b', 'c']
// 过去的方式——垃圾
for(let i = 0; i < arr.length; i++){
  const item = arr[i]
  console.log(item)
}

// for of 的方式，结果一样
for(const item of arr){
  console.log(item)
}
```



示例2:

```js
const elements = document.querySelectorAll('.item');
// for of 的方式
for(const elem of elements){
  // elem 为获取到的每一个元素
}
```



### 新增API

| API                                                          | 作用                                                     | 图示                                                         |
| ------------------------------------------------------------ | -------------------------------------------------------- | ------------------------------------------------------------ |
| [Array.isArray(target)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray) | 判断target是否为一个数组                                 |                                                              |
| [Array.from(source)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/from) | 将某个伪数组source转换为一个真数组返回                   |                                                              |
| [Array.prototype.fill(n)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/fill) | 将数组的某些项设置为n                                    | <img src="http://mdrs.yuanjin.tech/img/20210602165516.png" alt="image-20210602165515908" style="zoom:50%;" /> |
| [Array.prototype.forEach(fn)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) | 遍历数组，传入一个函数，每次遍历会运行该函数             | <img src="http://mdrs.yuanjin.tech/img/20210602165832.png" alt="image-20210602165832725" style="zoom:50%;" /> |
| [Array.prototype.map(fn)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map) | 数组映射，传入一个函数，映射数组中的每一项               | <img src="http://mdrs.yuanjin.tech/img/20210602170025.png" alt="image-20210602170025141" style="zoom:50%;" /> |
| [Array.prototype.filter(fn)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) | 数组筛选，传入一个函数，仅保留满足条件的项               | <img src="http://mdrs.yuanjin.tech/img/20210602170149.png" alt="image-20210602170149489" style="zoom:50%;" /> |
| [Array.prototype.reduce(fn)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) | 数组聚合，传入一个函数，对数组每一项按照该函数的返回聚合 | <img src="http://mdrs.yuanjin.tech/img/20210602170451.png" alt="image-20210602170451299" style="zoom:50%;" /> |
| [Array.prototype.some(fn)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/some) | 传入一个函数，判断数组中是否有至少一个通过该函数测试的项 | <img src="http://mdrs.yuanjin.tech/img/20210602171403.png" alt="image-20210602171403455" style="zoom:50%;" /> |
| [Array.prototype.every(fn)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/every) | 传入一个函数，判断数组中是否所有项都能通过该函数的测试   | <img src="http://mdrs.yuanjin.tech/img/20210602171441.png" alt="image-20210602171441468" style="zoom:50%;" /> |
| [Array.prototype.find(fn)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/find) | 传入一个函数，找到数组中第一个能通过该函数测试的项       | <img src="http://mdrs.yuanjin.tech/img/20210602171510.png" alt="image-20210602171510075" style="zoom:50%;" /> |
| [Array.prototype.includes(item)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) | 判断数组中是否存在item，判定规则使用的是`Object.is`      | <img src="http://mdrs.yuanjin.tech/img/20210602170615.png" alt="image-20210602170615564" style="zoom:50%;" /> |
|                                                              |                                                          |                                                              |

## 对象

### 对象成员速写

在某些场景下，ES6提供了一种更加简洁的方式书写对象成员

示例1：

```js
const name = 'monica', age = 17;
const sayHello = function(){
  console.log(`my name is ${this.name}`);
}
// 过去的方式
const user = {
  name: name,
  age: age,
  sayHello: sayHello
}

// 速写
const user = {
  name,
  age,
  sayHello
}
```

示例2：

```js
// 过去的方式
const MyMath = {
  sum: function(a, b){
    //...
  },
  random: function(min, max){
    //...
  }
}

// 速写
const MyMath = {
  sum(a, b){
    // ...
  },
  random(min, max){
    // ...
  }
}
```

### 解构

ES6提供了一种特殊的语法，通过该语法，可以轻松的从数组或对象中取出想要的部分

示例1：

```js
const user = {
  name: 'monica',
  age: 17,
  addr: {
    province: '黑龙江',
    city: '哈尔滨'
  }
}

// 取出 user 中的 name 和 age
const { name, age } = user;
console.log(name, age); //  monica 17

// 取出 user 中的 city
const { addr: { city } } = user
console.log(city); //  哈尔滨
```

示例2：

```js
const arr = [1, 2, 3, 4]
// 取出数组每一项的值，分别放到变量a、b、c、d中
const [a, b, c, d] = arr;
// 仅取出数组下标1、2的值
const [, a, b] = arr; 
// 仅取出数组下标1、3的值
const [, a, , b] = arr;
// 取出数组前两位的值，放到变量a和b中，剩下的值放到一个新数组arr2中
const [a, b, ...arr2] = arr;
```

示例3：

```js
let a = 1, b = 2;
// 交换两个变量
[b, a] = [a, b]
```

示例4：

```js
// 在参数位置对传入的对象进行解构
function method({a, b}){
  console.log(a, b)
}
const obj = {
  a:1,
  b:2,
  c:3
}
method(obj); // 1 2
```

示例5：

```js
// 箭头函数也可以在参数位置进行解构
const method = ({a, b}) => {
  console.log(a, b)
}
const obj = {
  a:1,
  b:2,
  c:3
}
method(obj); // 1 2
```

示例6：

```js
const users = [
  {name:'monica', age:17},
  {name:'邓哥', age:70}
]
// 在遍历时进行解构
for(const {name, age} of users){
  console.log(name, age)
}
```

### 展开运算符

示例1：

```js
const arr = [3, 6, 1, 7, 2];
// 对数组的展开
Math.max(...arr); // 相当于：Math.max(3, 6, 1, 7, 2)
```

示例2：

```js
const o1 = {
  a: 1, 
  b: 2,
}
const o2 = {
  a: 3, 
  c: 4,
}
// 对对象的展开
const o3 = {
  ...o1,
  ...o2
}
/*
	o3：{
		a: 3,
		b: 2,
		c: 4
	}
*/
```

示例3：

```js
const arr = [2,3,4];
const arr2 = [1, ...arr, 5]; // [1,2,3,4,5]
```

示例4：

```js
const user = {
  name: 'monica',
  age: 17
}
const user2 = {
  ...user,
  name: '邓哥'
}
// user2: { name:'邓哥', age: 17 }
```

### 属性描述符

对于对象中的每个成员，JS使用属性描述符来描述它们

```js
const user = {
  name: 'monica',
  age: 17
}
```

上面的对象，在JS内部被描述为

```js
{
  // 属性 name 的描述符
  name: {
    value: 'monica',
    configurable: true, // 该属性的描述符是否可以被重新定义
    enumerable: true, // 该属性是否允许被遍历，会影响for-in循环
    writable: true // 该属性是否允许被修改
  },
  // 属性 age 的描述符
  age: {
    value: 'monica',
    configurable: true, // 该属性的描述符是否可以被重新定义
    enumerable: true, // 该属性是否允许被遍历，会影响for-in循环
    writable: true // 该属性是否允许被修改
  },
}
```

ES5提供了一系列的API，针对属性描述符进行操作

1. `Object.getOwnPropertyDescriptor(obj, propertyName)`

   该方法用于获取一个属性的描述符

   ```js
   const user = {
     name: 'monica',
     age: 17
   }
   
   Object.getOwnPropertyDescriptor(user, 'name');
   /*
   {
       value: 'monica',
       configurable: true, // 该属性的描述符是否可以被重新定义
       enumerable: true, // 该属性是否允许被遍历，会影响for-in循环
       writable: true // 该属性是否允许被修改
   }
   */
   ```

2. `Object.defineProperty(obj, propertyName, descriptor)`

   该方法用于定义某个属性的描述符

   ```js
   const user = {
     name: 'monica',
     age: 17
   };
   
   Object.defineProperty(obj, 'name', {
     value: '邓哥', // 将其值进行修改
     enumerable: false, // 让该属性不能被遍历
     writable: false // 让该属性无法被重新赋值
   })
   ```

#### getter 和 setter

属性描述符中有两个特殊的配置，分别为`get`和`set`，通过它们，可以把属性的取值和赋值变为方法调用

```js
const obj = {};
Object.defineProperty(obj, 'a', {
  get(){ // 读取属性a时，得到的是该方法的返回值
    return 1;
  },
  set(val){ // 设置属性a时，会把值传入val，调用该方法
    console.log(val)
  }
})

console.log(obj.a); // 输出：1
obj.a = 3; // 输出：3
console.log(obj.a); // 输出：1
```

### 键值对

`Object.keys(obj)`：获取对象的属性名组成的数组

`Object.values(obj)`：获取对象的值组成的数组

`Object.entries(obj)`：获取对象属性名和属性值组成的数组

`Object.fromEntries(entries)`：将属性名和属性值的数组转换为对象

示例：

```js
const user = {
  name: 'monica',
  age: 17
}
Object.keys(user); // ["name", "age"]
Object.values(user); // ["monica", 17]
Object.entries(user); // [ ["name", "monica"], ["age", 17] ]
Object.fromEntries([ ["name", "monica"], ["age", 17] ]); // {name:'monica', age:17}
```

### 冻结

使用`Object.freeze(obj)`可以冻结一个对象，该对象的所有属性均不可更改

```js
const obj = {
  a: 1,
  b: {
    c: 3,
  },
};

Object.freeze(obj); //  冻结对象obj

obj.a = 2; // 不报错，代码无效
obj.k = 4; // 不报错，代码无效
delete obj.a; // 不报错，代码无效
obj.b = 5; // 不报错，代码无效

obj.b.c = 5; // b对象没有被冻结，有效

console.log(obj); // {a:1, b:{ c: 5 } }
```

可以使用`Object.isFrozen`来判断一个对象是否被冻结

### 相同性判定

`Object.is`方法，可以判断两个值是否相同，它和`===`的功能基本一致，区别在于：

- NaN和NaN相等
- +0和-0不相等

```js
Object.is(1, 2); // false
Object.is("1", 1); // false
Object.is(NaN, NaN); // true
Object.is(+0, -0); // false
```

### Set

[Set MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set)

ES6新增了Set结构，用于保存唯一值的序列

### Map

[Map MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map)

ES6新增了Map结构，用于保存键值对的映射，它和对象的最大区别在于：对象的键只能是字符串，而Map的键可以是任何类型

## 函数

### 箭头函数

所有使用**函数表达式**的位置，均可以替换为箭头函数

箭头函数语法：

```js
// 完整语法
(参数列表) => { 函数体 }
// 若有且仅有一个参数
参数 => { 函数体 }
// 若函数体有且仅有一条返回语句
(参数列表) => 返回语句
```

示例1：

```js
const sum = function(a, b) {
  return a + b;
}

// 箭头函数写法
const sum = (a, b) => a + b
```

示例2：

```js
dom.onclick = function(e){
  // ....
}

// 箭头函数写法
dom.onclick = e => {
  // ...
}
```

示例3：

```js
setTimeout(function(){
  // ...
}, 1000)

// 箭头函数写法
setTimeout(() => {
  // ...
}, 1000)
```

箭头函数有以下特点：

1. 不能使用`new`调用

2. 没有原型，即没有`prototype`属性

3. 没有`arugments`

4. 没有`this`

   > 有些教程中会说：箭头函数的`this`永远指向箭头函数定义位置的`this`，因为箭头函数会绑定`this`。
   >
   > 这个说法没错，根本原因是它没有`this`，它里面的`this`使用的是外层的`this`

   ```js
   const counter = {
     count: 0,
     start: function(){
       // 这里的 this 指向 counter
       setInterval(() => {
         // 这里的 this 实际上是 start 函数的 this
         this.count++;
       }, 1000)
     }
   }
   ```

箭头函数的这些特点，都足以说明：**箭头函数特别适用于那些临时需要函数的位置**

> 我们将来会在面试指导阶段对this指向进行总结

### 剩余参数

ES6不建议再使用`arguments`来获取参数列表，它推荐使用剩余参数来收集未知数量的参数

```js
// ...args为剩余参数
function method(a, b, ...args){
  console.log(a, b, args)
}

method(1, 2, 3, 4, 5, 6, 7); // 1 2 [3, 4, 5, 6, 7]
method(1, 2); // 1 2 []
```

**注意，剩余参数只能声明为最后一个参数**

### 参数默认值

ES6提供了参数默认值，当参数没有传递或传递为`undefined`时，会使用默认值

示例1：

```js
// 对参数 b 使用了默认值1
function method(a, b = 1){
  console.log(a, b)
}
method(1, 2); // 1  2
method(1); // 1 1
method(1, undefined); // 1 1
```

示例2：

```js
// 对参数 b 使用了默认值1， 对参数 c 使用默认值2
const method = (a, b = 1, c = 2, d) => {
  console.log(a, b, c, d)
}
method(1, 2); // 1 2 2 undefined
method(1); // 1 1 2 undefined
method(1, undefined, undefined, 4); // 1 1 2 4
```

### 类语法

过去，函数有着两种调用方式：

```js
function A(){}

A(); // 直接调用
new A(); // 作为构造函数调用
```

这种做法无法从定义上明确函数的用途，因此，ES6推出了一种全新的语法来书写构造函数

示例1：

```js
// 旧的写法
function User(firstName, lastName){
  this.firstName = firstName;
  this.lastName = lastName;
  this.fullName = `${firstName} ${lastName}`;
}
User.isUser = function(u){
  return !!u && !!u.fullName
}
User.prototype.sayHello = function(){
  console.log(`Hello, my name is ${this.fullName}`);
}

// 新的等效写法
class User{
  constructor(firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
    this.fullName = `${firstName} ${lastName}`;
  }
  
  static isUser(u){
  	 return !!u && !!u.fullName
  }
  
  sayHello(){
    console.log(`Hello, my name is ${this.fullName}`);
  }
}
```

示例2：

```js
function Animal(type, name){
  this.type = type;
  this.name = name;
}

Animal.prototype.intro = function(){
  console.log(`I am ${this.type}, my name is ${this.name}`)
}

function Dog(name){
  Animal.call(this, '狗', name);
}

Dog.prototype = Object.create(Animal.prototype); // 设置继承关系

// 新的方式

class Animal{
  constructor(type, name){
    this.type = type;
    this.name = name;
  }
  
  intro(){
    console.log(`I am ${this.type}, my name is ${this.name}`)
  }
}

class Dog extends Animal{
 	constructor(name){
    super('狗', name);
  }
}
```



### 函数API

| API                                                          | 含义                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Function.prototype.call(obj, ...args)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call) | 调用函数，绑定this为obj<br />后续以列表的形式提供参数        |
| [Function.prototype.apply(obj, args)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) | 调用函数，绑定this为obj<br />args以数组的形式提供参数        |
| [Function.prototype.bind(obj, ...args)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) | 返回一个函数的拷贝<br />新函数的this被绑定为obj<br />起始参数被绑定为args |
|                                                              |                                                              |



# 事件循环（核心概念）

## 浏览器的进程模型

### 何为进程？

程序运行需要有它自己专属的内存空间，可以把这块内存空间简单的理解为进程

<img src="http://mdrs.yuanjin.tech/img/202208092057573.png" alt="image-20220809205743532" style="zoom:50%;" />

每个应用至少有一个进程，进程之间相互独立，即使要通信，也需要双方同意。

### 何为线程？

有了进程后，就可以运行程序的代码了。

运行代码的「人」称之为「线程」。

一个进程至少有一个线程，所以在进程开启后会自动创建一个线程来运行代码，该线程称之为主线程。

如果程序需要同时执行多块代码，主线程就会启动更多的线程来执行代码，所以一个进程中可以包含多个线程。

![image-20220809210859457](http://mdrs.yuanjin.tech/img/202208092108499.png)

### 浏览器有哪些进程和线程？

**浏览器是一个多进程多线程的应用程序**

浏览器内部工作极其复杂。

为了避免相互影响，为了减少连环崩溃的几率，当启动浏览器后，它会自动启动多个进程。

![image-20220809213152371](http://mdrs.yuanjin.tech/img/202208092131410.png)

> 可以在浏览器的任务管理器中查看当前的所有进程

其中，最主要的进程有：

1. 浏览器进程

   主要负责界面显示、用户交互、子进程管理等。浏览器进程内部会启动多个线程处理不同的任务。

2. 网络进程

   负责加载网络资源。网络进程内部会启动多个线程来处理不同的网络任务。

3. **渲染进程**（本节课重点讲解的进程）

   渲染进程启动后，会开启一个**渲染主线程**，主线程负责执行 HTML、CSS、JS 代码。

   默认情况下，浏览器会为每个标签页开启一个新的渲染进程，以保证不同的标签页之间不相互影响。

   > 将来该默认模式可能会有所改变，有兴趣的同学可参见[chrome官方说明文档](https://chromium.googlesource.com/chromium/src/+/main/docs/process_model_and_site_isolation.md#Modes-and-Availability)

## 渲染主线程是如何工作的？

渲染主线程是浏览器中最繁忙的线程，需要它处理的任务包括但不限于：

- 解析 HTML
- 解析 CSS
- 计算样式
- 布局
- 处理图层
- 每秒把页面画 60 次
- 执行全局 JS 代码
- 执行事件处理函数
- 执行计时器的回调函数
- ......

> 思考题：为什么渲染进程不适用多个线程来处理这些事情？

要处理这么多的任务，主线程遇到了一个前所未有的难题：如何调度任务？

比如：

- 我正在执行一个 JS 函数，执行到一半的时候用户点击了按钮，我该立即去执行点击事件的处理函数吗？
- 我正在执行一个 JS 函数，执行到一半的时候某个计时器到达了时间，我该立即去执行它的回调吗？
- 浏览器进程通知我“用户点击了按钮”，与此同时，某个计时器也到达了时间，我应该处理哪一个呢？
- ......

渲染主线程想出了一个绝妙的主意来处理这个问题：排队

![image-20220809223027806](http://mdrs.yuanjin.tech/img/202208092230847.png)

1. 在最开始的时候，渲染主线程会进入一个无限循环
2. 每一次循环会检查消息队列中是否有任务存在。如果有，就取出第一个任务执行，执行完一个后进入下一次循环；如果没有，则进入休眠状态。
3. 其他所有线程（包括其他进程的线程）可以随时向消息队列添加任务。新任务会加到消息队列的末尾。在添加新任务时，如果主线程是休眠状态，则会将其唤醒以继续循环拿取任务

这样一来，就可以让每个任务有条不紊的、持续的进行下去了。

**整个过程，被称之为事件循环（消息循环）**

## 若干解释

### 何为异步？

代码在执行过程中，会遇到一些无法立即处理的任务，比如：

- 计时完成后需要执行的任务 —— `setTimeout`、`setInterval`
- 网络通信完成后需要执行的任务 -- `XHR`、`Fetch`
- 用户操作后需要执行的任务 -- `addEventListener`

如果让渲染主线程等待这些任务的时机达到，就会导致主线程长期处于「阻塞」的状态，从而导致浏览器「卡死」

![image-20220810104344296](http://mdrs.yuanjin.tech/img/202208101043348.png)

**渲染主线程承担着极其重要的工作，无论如何都不能阻塞！**

因此，浏览器选择**异步**来解决这个问题

![image-20220810104858857](http://mdrs.yuanjin.tech/img/202208101048899.png)

使用异步的方式，**渲染主线程永不阻塞**

> 面试题：如何理解 JS 的异步？
>
> 
>
> 参考答案：
>
> JS是一门单线程的语言，这是因为它运行在浏览器的渲染主线程中，而渲染主线程只有一个。
>
> 而渲染主线程承担着诸多的工作，渲染页面、执行 JS 都在其中运行。
>
> 如果使用同步的方式，就极有可能导致主线程产生阻塞，从而导致消息队列中的很多其他任务无法得到执行。这样一来，一方面会导致繁忙的主线程白白的消耗时间，另一方面导致页面无法及时更新，给用户造成卡死现象。
>
> 所以浏览器采用异步的方式来避免。具体做法是当某些任务发生时，比如计时器、网络、事件监听，主线程将任务交给其他线程去处理，自身立即结束任务的执行，转而执行后续代码。当其他线程完成时，将事先传递的回调函数包装成任务，加入到消息队列的末尾排队，等待主线程调度执行。
>
> 在这种异步模式下，浏览器永不阻塞，从而最大限度的保证了单线程的流畅运行。

### JS为何会阻碍渲染？

先看代码

```html
<h1>Mr.Yuan is awesome!</h1>
<button>change</button>
<script>
  var h1 = document.querySelector('h1');
  var btn = document.querySelector('button');

  // 死循环指定的时间
  function delay(duration) {
    var start = Date.now();
    while (Date.now() - start < duration) {}
  }

  btn.onclick = function () {
    h1.textContent = '袁老师很帅！';
    delay(3000);
  };
</script>
```

点击按钮后，会发生什么呢？

<见具体演示>

### 任务有优先级吗？

任务没有优先级，在消息队列中先进先出

但**消息队列是有优先级的**

根据 W3C 的最新解释:

- 每个任务都有一个任务类型，同一个类型的任务必须在一个队列，不同类型的任务可以分属于不同的队列。
  在一次事件循环中，浏览器可以根据实际情况从不同的队列中取出任务执行。
- 浏览器必须准备好一个微队列，微队列中的任务优先所有其他任务执行
  https://html.spec.whatwg.org/multipage/webappapis.html#perform-a-microtask-checkpoint

> 随着浏览器的复杂度急剧提升，W3C 不再使用宏队列的说法

在目前 chrome 的实现中，至少包含了下面的队列：

- 延时队列：用于存放计时器到达后的回调任务，优先级「中」
- 交互队列：用于存放用户操作后产生的事件处理任务，优先级「高」
- 微队列：用户存放需要最快执行的任务，优先级「最高」

> 添加任务到微队列的主要方式主要是使用 Promise、MutationObserver
>
> 
>
> 例如：
>
> ```js
> // 立即把一个函数添加到微队列
> Promise.resolve().then(函数)
> ```

> 浏览器还有很多其他的队列，由于和我们开发关系不大，不作考虑

> 面试题：阐述一下 JS 的事件循环
>
> 
>
> 参考答案：
>
> 事件循环又叫做消息循环，是浏览器渲染主线程的工作方式。
>
> 在 Chrome 的源码中，它开启一个不会结束的 for 循环，每次循环从消息队列中取出第一个任务执行，而其他线程只需要在合适的时候将任务加入到队列末尾即可。
>
> 过去把消息队列简单分为宏队列和微队列，这种说法目前已无法满足复杂的浏览器环境，取而代之的是一种更加灵活多变的处理方式。
>
> 根据 W3C 官方的解释，每个任务有不同的类型，同类型的任务必须在同一个队列，不同的任务可以属于不同的队列。不同任务队列有不同的优先级，在一次事件循环中，由浏览器自行决定取哪一个队列的任务。但浏览器必须有一个微队列，微队列的任务一定具有最高的优先级，必须优先调度执行。

> 面试题：JS 中的计时器能做到精确计时吗？为什么？
>
> 
>
> 参考答案：
>
> 不行，因为：
>
> 1. 计算机硬件没有原子钟，无法做到精确计时
> 2. 操作系统的计时函数本身就有少量偏差，由于 JS 的计时器最终调用的是操作系统的函数，也就携带了这些偏差
> 3. 按照 W3C 的标准，浏览器实现计时器时，如果嵌套层级超过 5 层，则会带有 4 毫秒的最少时间，这样在计时时间少于 4 毫秒时又带来了偏差
> 4. 受事件循环的影响，计时器的回调函数只能在主线程空闲时运行，因此又带来了偏差



# Promise基础

> 本节课的任务：
>
> 1. 理解Promise A+规范的基本概念
> 2. 学会创建Promise
> 3. 学会针对Promise进行后续处理

## 邓哥的烦恼

邓哥心中有很多女神，他今天下定决心，要向这些女神表白，他认为，只要女神够多，根据概率学原理，总有一个会接收他

稳妥起见，邓哥决定使用**串行**的方式进行表白：先给第1位女神发送短信，然后等待女神的回应，如果成功了，就结束，如果失败了，则再给第2位女神发送短信，依次类推

![image-20210618150543263](http://mdrs.yuanjin.tech/img/20210618150543.png)

邓哥的女神一共有4位，名字分别是：李建国、王富贵、周聚财、刘人勇

发短信是一个重复性的劳动，邓哥是个程序员，因此决定用函数封装这个动作

```js
// 向某位女生发送一则表白短信
// name: 女神的姓名
// onFulffiled: 成功后的回调
// onRejected: 失败后的回调
function sendMessage(name, onFulffiled, onRejected) {
  // 模拟 发送表白短信
  console.log(
    `邓哥 -> ${name}：最近有谣言说我喜欢你，我要澄清一下，那不是谣言😘`
  );
  console.log(`等待${name}回复......`);
  // 模拟 女神回复需要一段时间
  setTimeout(() => {
    // 模拟 有10%的几率成功
    if (Math.random() <= 0.1) {
      // 成功，调用 onFuffiled，并传递女神的回复
      onFulffiled(`${name} -> 邓哥：我是九，你是三，除了你还是你😘`);
    } else {
      // 失败，调用 onRejected，并传递女神的回复
      onRejected(`${name} -> 邓哥：你是个好人😜`);
    }
  }, 1000);
}
```

有了这个函数后，邓哥于是开始编写程序发送短信了

```js
// 首先向 李建国 发送消息
sendMessage(
  '李建国',
  (reply) => {
    // 如果成功了，输出回复的消息后，结束
    console.log(reply);
  },
  (reply) => {
    // 如果失败了，输出回复的消息后，向 王富贵 发送消息
    console.log(reply);
    sendMessage(
      '王富贵',
      (reply) => {
        // 如果成功了，输出回复的消息后，结束
        console.log(reply);
      },
      (reply) => {
        // 如果失败了，输出回复的消息后，向 周聚财 发送消息
        console.log(reply);
        sendMessage(
          '周聚财',
          (reply) => {
            // 如果成功了，输出回复的消息后，结束
            console.log(reply);
          },
          (reply) => {
            // 如果失败了，输出回复的消息后，向 刘人勇 发送消息
            console.log(reply);
            sendMessage(
              '刘人勇',
              (reply) => {
                // 如果成功了，输出回复的消息后，结束
                console.log(reply);
              },
              (reply) => {
                // 如果失败了，就彻底没戏了
                console.log(reply);
                console.log('邓哥命犯天煞孤星，注定孤独终老！！');
              }
            );
          }
        );
      }
    );
  }
);
```

该程序完成后，邓哥内心是崩溃的

这一层一层的回调嵌套，形成了传说中的「**回调地狱 callback hell**」

邓哥是个完美主义者，怎么能忍受这样的代码呢？

要解决这样的问题，需要Promise出马

## Promise规范

Promise是一套专门处理异步场景的规范，它能有效的避免回调地狱的产生，使异步代码更加清晰、简洁、统一

这套规范最早诞生于前端社区，规范名称为[Promise A+](https://promisesaplus.com/)

该规范出现后，立即得到了很多开发者的响应

Promise A+ 规定：

1. 所有的异步场景，都可以看作是一个异步任务，每个异步任务，在JS中应该表现为一个**对象**，该对象称之为**Promise对象**，也叫做任务对象

   <img src="http://mdrs.yuanjin.tech/img/20210618154556.png" alt="image-20210618154556558" style="zoom:50%;" />

2. 每个任务对象，都应该有两个阶段、三个状态

   <img src="http://mdrs.yuanjin.tech/img/20210618155145.png" alt="image-20210618155145355" style="zoom:50%;" />

   根据常理，它们之间存在以下逻辑：

   - 任务总是从未决阶段变到已决阶段，无法逆行
   - 任务总是从挂起状态变到完成或失败状态，无法逆行
   - 时间不能倒流，历史不可改写，任务一旦完成或失败，状态就固定下来，永远无法改变

3. `挂起->完成`，称之为`resolve`；`挂起->失败`称之为`reject`。任务完成时，可能有一个相关数据；任务失败时，可能有一个失败原因。

   ![image-20210618160538875](http://mdrs.yuanjin.tech/img/20210618160538.png)

4. 可以针对任务进行后续处理，针对完成状态的后续处理称之为onFulfilled，针对失败的后续处理称之为onRejected

   ![image-20210618161125894](http://mdrs.yuanjin.tech/img/20210618161125.png)

## Promise API

ES6提供了一套API，实现了Promise A+规范

基本使用如下：

```js
// 创建一个任务对象，该任务立即进入 pending 状态
const pro = new Promise((resolve, reject) => {
  // 任务的具体执行流程，该函数会立即被执行
  // 调用 resolve(data)，可将任务变为 fulfilled 状态， data 为需要传递的相关数据
  // 调用 reject(reason)，可将任务变为 rejected 状态，reason 为需要传递的失败原因
});

pro.then(
  (data) => {
    // onFulfilled 函数，当任务完成后，会自动运行该函数，data为任务完成的相关数据
  },
  (reason) => {
    // onRejected 函数，当任务失败后，会自动运行该函数，reason为任务失败的相关原因
  }
);
```

## 邓哥的解决方案

学习了ES6的Promise后，邓哥决定对`sendMessage`函数进行改造，改造结果如下：

```js
// 向某位女生发送一则表白短信
// name: 女神的姓名
// 该函数返回一个任务对象
function sendMessage(name) {
  return new Promise((resolve, reject) => {
    // 模拟 发送表白短信
    console.log(
      `邓哥 -> ${name}：最近有谣言说我喜欢你，我要澄清一下，那不是谣言😘`
    );
    console.log(`等待${name}回复......`);
    // 模拟 女神回复需要一段时间
    setTimeout(() => {
      // 模拟 有10%的几率成功
      if (Math.random() <= 0.1) {
        // 成功，调用 resolve，并传递女神的回复
        resolve(`${name} -> 邓哥：我是九，你是三，除了你还是你😘`);
      } else {
        // 失败，调用 reject，并传递女神的回复
        reject(`${name} -> 邓哥：你是个好人😜`);
      }
    }, 1000);
  });
}
```

之后，就可以使用该函数来发送消息了

```js
sendMessage('李建国').then(
  (reply) => {
    // 女神答应了，输出女神的回复
    console.log(reply);
  },
  (reason) => {
    // 女神拒绝了，输出女神的回复
    console.log(reason);
  }
);
```

> 至此，回调地狱的问题仍然没能解决
>
> 要解决回调地狱，还需要进一步学习Promise的知识



# Promise链式调用

![image-20210618161125894](http://mdrs.yuanjin.tech/img/20210618161125.png)

## catch方法

`.catch(onRejected)` = `.then(null, onRejected)`

## 链式调用

![image-20210621103501094](http://mdrs.yuanjin.tech/img/20210621103501.png)

1. then方法必定会返回一个新的Promise

   可理解为`后续处理也是一个任务`

2. 新任务的状态取决于后续处理：

   - 若没有相关的后续处理，新任务的状态和前任务一致，数据为前任务的数据

   - 若有后续处理但还未执行，新任务挂起。
   - 若后续处理执行了，则根据后续处理的情况确定新任务的状态
     - 后续处理执行无错，新任务的状态为完成，数据为后续处理的返回值
     - 后续处理执行有错，新任务的状态为失败，数据为异常对象
     - 后续执行后返回的是一个任务对象，新任务的状态和数据与该任务对象一致

由于链式任务的存在，异步代码拥有了更强的表达力

```js
// 常见任务处理代码

/*
 * 任务成功后，执行处理1，失败则执行处理2
 */
pro.then(处理1).catch(处理2)

/*
 * 任务成功后，依次执行处理1、处理2
 */
pro.then(处理1).then(处理2)

/*
 * 任务成功后，依次执行处理1、处理2，若任务失败或前面的处理有错，执行处理3
 */
pro.then(处理1).then(处理2).catch(处理3)
```

## 邓哥的解决方案

```js
// 向某位女生发送一则表白短信
// name: 女神的姓名
// onFulffiled: 成功后的回调
// onRejected: 失败后的回调
function sendMessage(name) {
  return new Promise((resolve, reject) => {
    // 模拟 发送表白短信
    console.log(
      `邓哥 -> ${name}：最近有谣言说我喜欢你，我要澄清一下，那不是谣言😘`
    );
    console.log(`等待${name}回复......`);
    // 模拟 女神回复需要一段时间
    setTimeout(() => {
      // 模拟 有10%的几率成功
      if (Math.random() <= 0.1) {
        // 成功，调用 onFuffiled，并传递女神的回复
        resolve(`${name} -> 邓哥：我是九，你是三，除了你还是你😘`);
      } else {
        // 失败，调用 onRejected，并传递女神的回复
        reject(`${name} -> 邓哥：你是个好人😜`);
      }
    }, 1000);
  });
}

sendMessage('李建国')
  .catch((reply) => {
    // 失败，继续
    console.log(reply);
    return sendMessage('王富贵');
  })
  .catch((reply) => {
    // 失败，继续
    console.log(reply);
    return sendMessage('周聚财');
  })
  .catch((reply) => {
    // 失败，继续
    console.log(reply);
    return sendMessage('刘人勇');
  })
  .then(
    (reply) => {
      // 成功，结束
      console.log(reply);
      console.log('邓哥终于找到了自己的伴侣');
    },
    (reply) => {
      // 最后一个也失败了
      console.log(reply);
      console.log('邓哥命犯天煞孤星，无伴终老，孤独一生');
    }
  );
```



# Promise静态方法

## 邓哥的新问题

邓嫂出门时，给邓哥交待了几个任务：

1. 做饭

   可交给电饭煲完成

2. 洗衣服

   可交给洗衣机完成

3. 打扫卫生

   可交给扫地机器人完成

邓哥需要在所有任务结束后给邓嫂汇报工作，哪些成功了，哪些失败了

为了最大程度的节约时间，邓哥希望这些任务同时进行，最终汇总结果统一处理

<img src="http://mdrs.yuanjin.tech/img/20210621142519.png" alt="image-20210621142519937" style="zoom:50%;" />

每个任务可以看做是一个返回Promise的函数

```js
// 做饭
function cook() {
  return new Promise((resolve, reject) => {
    console.log('邓哥打开了电饭煲');
    setTimeout(() => {
      if (Math.random() < 0.5) {
        resolve('饭已ok');
      } else {
        reject('做饭却忘了加水，米饭变成了爆米花');
      }
    }, 2000);
  });
}

// 洗衣服
function wash() {
  return new Promise((resolve, reject) => {
    console.log('邓哥打开了洗衣机');
    setTimeout(() => {
      if (Math.random() < 0.5) {
        resolve('衣服已经洗好');
      } else {
        reject('洗衣服时停水了，洗了个寂寞');
      }
    }, 2500);
  });
}

// 打扫卫生
function sweep() {
  return new Promise((resolve, reject) => {
    console.log('邓哥打开了扫地机器人');
    setTimeout(() => {
      if (Math.random() < 0.5) {
        resolve('地板扫的非常干净');
      } else {
        reject('扫地机器人被哈士奇一爪掀翻了');
      }
    }, 3000);
  });
}

```

如何利用这三个函数实现邓哥的要求呢？

## Promise的静态方法

| 方法名                       | 含义                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| Promise.resolve(data)        | 直接返回一个完成状态的任务                                   |
| Promise.reject(reason)       | 直接返回一个拒绝状态的任务                                   |
| Promise.all(任务数组)        | 返回一个任务<br />任务数组全部成功则成功<br />任何一个失败则失败 |
| Promise.any(任务数组)        | 返回一个任务<br />任务数组任一成功则成功<br />任务全部失败则失败 |
| Promise.allSettled(任务数组) | 返回一个任务<br />任务数组全部已决则成功<br />该任务不会失败 |
| Promise.race(任务数组)       | 返回一个任务<br />任务数组任一已决则已决，状态和其一致       |
|                              |                                                              |

## 邓哥的解决方案

```js
Promise.allSettled([cook(), wash(), sweep()]).then((result) => {
  // 处理汇总结果
  const report = result
    .map((r) => (r.status === 'fulfilled' ? r.value : r.reason))
    .join(';');
  console.log(report);
});
```



# async和await

![image-20210618161125894](http://mdrs.yuanjin.tech/img/20210618161125.png)

## 消除回调

有了Promise，异步任务就有了一种统一的处理方式

有了统一的处理方式，ES官方就可以对其进一步优化

ES7推出了两个关键字`async`和`await`，用于更加优雅的表达Promise

### async

async关键字用于修饰函数，被它修饰的函数，一定返回Promise

```js
async function method1(){
  return 1; // 该函数的返回值是Promise完成后的数据
}

method1(); // Promise { 1 }

async function method2(){
  return Promise.resolve(1); // 若返回的是Promise，则method得到的Promise状态和其一致
}

method2(); // Promise { 1 }

async function method3(){
  throw new Error(1); // 若执行过程报错，则任务是rejected
}

method3(); // Promise { <rejected> Error(1) }
```

### await

`await`关键字表示等待某个Promise完成，**它必须用于`async`函数中**

```js
async function method(){
  const n = await Promise.resolve(1);
  console.log(n); // 1
}

// 上面的函数等同于
function method(){
  return new Promise((resolve, reject)=>{
    Promise.resolve(1).then(n=>{
      console.log(n);
      resolve(1)
    })
  })
}
```

`await`也可以等待其他数据

```js
async function method(){
  const n = await 1; // 等同于 await Promise.resolve(1)
}
```

如果需要针对失败的任务进行处理，可以使用`try-catch`语法

```js
async function method(){
  try{
    const n = await Promise.reject(123); // 这句代码将抛出异常
    console.log('成功', n)
  }
  catch(err){
    console.log('失败', err)
  }
}

method(); // 输出： 失败 123
```



## 邓哥表白的完美解决方案

邓哥的女神可不是只有4位，而是40位！

为了更加方便的编写表白代码，邓哥决定把这40位女神放到一个数组中，然后利用async和await轻松完成代码

```js
// 女神的名字数组
const beautyGirls = [
  '梁平',
  '邱杰',
  '王超',
  '冯秀兰',
  '赖军',
  '顾强',
  '戴敏',
  '吕涛',
  '冯静',
  '蔡明',
  '廖磊',
  '冯洋',
  '韩杰',
  '江涛',
  '文艳',
  '杜秀英',
  '丁艳',
  '邓静',
  '江刚',
  '乔刚',
  '史平',
  '康娜',
  '袁磊',
  '龙秀英',
  '姚静',
  '潘娜',
  '萧磊',
  '邵勇',
  '李芳',
  '谭芳',
  '夏秀英',
  '程娜',
  '武杰',
  '崔军',
  '廖勇',
  '崔强',
  '康秀英',
  '余磊',
  '邵勇',
  '贺涛',
];

// 向某位女生发送一则表白短信
// name: 女神的姓名
function sendMessage(name) {
  return new Promise((resolve, reject) => {
    // 模拟 发送表白短信
    console.log(
      `邓哥 -> ${name}：最近有谣言说我喜欢你，我要澄清一下，那不是谣言😘`
    );
    console.log(`等待${name}回复......`);
    // 模拟 女神回复需要一段时间
    setTimeout(() => {
      // 模拟 有10%的几率成功
      if (Math.random() <= 0.1) {
        // 成功，调用 onFuffiled，并传递女神的回复
        resolve(`${name} -> 邓哥：我是九，你是三，除了你还是你😘`);
      } else {
        // 失败，调用 onRejected，并传递女神的回复
        reject(`${name} -> 邓哥：你是个好人😜`);
      }
    }, 1000);
  });
}

// 批量表白的程序
async function proposal() {
  let isSuccess = false;
  for (const girl of beautyGirls) {
    try {
      const reply = await sendMessage(girl);
      console.log(reply);
      console.log('表白成功!');
      isSuccess = true;
      break;
    } catch (reply) {
      console.log(reply);
      console.log('表白失败');
    }
  }
  if (!isSuccess) {
    console.log('邓哥注定孤独一生');
  }
}
proposal();
```



# Promise面试题

# 面试题考点

## Promise的基本概念

![image-20210618161125894](http://mdrs.yuanjin.tech/img/20210618161125.png)

## 链式调用规则

![image-20210621103501094](http://mdrs.yuanjin.tech/img/20210621103501.png)

![image-20210621103501094](http://mdrs.yuanjin.tech/img/20210621103501.png)

1. then方法必定会返回一个新的Promise

   可理解为`后续处理也是一个任务`

2. 新任务的状态取决于后续处理：

   - 若没有相关的后续处理，新任务的状态和前任务一致，数据为前任务的数据

   - 若有后续处理但还未执行，新任务挂起。
   - 若后续处理执行了，则根据后续处理的情况确定新任务的状态
     - 后续处理执行无错，新任务的状态为完成，数据为后续处理的返回值
     - 后续处理执行有错，新任务的状态为失败，数据为异常对象
     - 后续执行后返回的是一个任务对象，新任务的状态和数据与该任务对象一致

## Promise的静态方法

| 方法名                       | 含义                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| Promise.resolve(data)        | 直接返回一个完成状态的任务                                   |
| Promise.reject(reason)       | 直接返回一个拒绝状态的任务                                   |
| Promise.all(任务数组)        | 返回一个任务<br />任务数组全部成功则成功<br />任何一个失败则失败 |
| Promise.any(任务数组)        | 返回一个任务<br />任务数组任一成功则成功<br />任务全部失败则失败 |
| Promise.allSettled(任务数组) | 返回一个任务<br />任务数组全部已决则成功<br />该任务不会失败 |
| Promise.race(任务数组)       | 返回一个任务<br />任务数组任一已决则已决，状态和其一致       |
|                              |                                                              |

## async和await

有了Promise，异步任务就有了一种统一的处理方式

有了统一的处理方式，ES官方就可以对其进一步优化

ES7推出了两个关键字`async`和`await`，用于更加优雅的表达Promise

### async

async关键字用于修饰函数，被它修饰的函数，一定返回Promise

```js
async function method1(){
  return 1; // 该函数的返回值是Promise完成后的数据
}

method1(); // Promise { 1 }

async function method2(){
  return Promise.resolve(1); // 若返回的是Promise，则method得到的Promise状态和其一致
}

method2(); // Promise { 1 }

async function method3(){
  throw new Error(1); // 若执行过程报错，则任务是rejected
}

method3(); // Promise { <rejected> Error(1) }
```

### await

`await`关键字表示等待某个Promise完成，**它必须用于`async`函数中**

```js
async function method(){
  const n = await Promise.resolve(1);
  console.log(n); // 1
}

// 上面的函数等同于
function method(){
  return new Promise((resolve, reject)=>{
    Promise.resolve(1).then(n=>{
      console.log(n);
      resolve(1)
    })
  })
}
```

`await`也可以等待其他数据

```js
async function method(){
  const n = await 1; // 等同于 await Promise.resolve(1)
}
```

如果需要针对失败的任务进行处理，可以使用`try-catch`语法

```js
async function method(){
  try{
    const n = await Promise.reject(123); // 这句代码将抛出异常
    console.log('成功', n)
  }
  catch(err){
    console.log('失败', err)
  }
}

method(); // 输出： 失败 123
```

## 事件循环

根据目前所学，进入事件队列的函数有以下几种：

- `setTimeout`的回调，宏任务（macro task）
- `setInterval`的回调，宏任务（macro task）
- Promise的`then`函数回调，**微任务**（micro task）
- `requestAnimationFrame`的回调，宏任务（macro task）
- 事件处理函数，宏任务(macro task)

## 面试题

1. 下面代码的输出结果是什么

   ```js
   const promise = new Promise((resolve, reject) => {
       console.log(1); 
       resolve(); 
       console.log(2);
   })
   
   promise.then(() => {
       console.log(3);
   })
   
   console.log(4);
   ```

2. 下面代码的输出结果是什么

   ```js
   const promise = new Promise((resolve, reject) => {
       console.log(1); 
       setTimeout(()=>{
         console.log(2)
         resolve(); 
       	console.log(3);
       })
   })
   
   promise.then(() => {
       console.log(4);
   })
   
   console.log(5);
   ```

3. 下面代码的输出结果是什么

   ```js
   const promise1 = new Promise((resolve, reject) => {
   	setTimeout(() => {
       resolve()
     }, 1000)
   })
   const promise2 = promise1.catch(() => {
     return 2;
   })
   
   console.log('promise1', promise1) 
   console.log('promise2', promise2) 
   
   setTimeout(() => {
     console.log('promise1', promise1) 
     console.log('promise2', promise2) 
   }, 2000)
   ```

4. 下面代码的输出结果是什么

   ```js
   async function m(){
     const n = await 1;
     console.log(n);
   }
   
   m();
   console.log(2);
   ```

5. 下面代码的输出结果是什么

   ```js
   async function m(){
     const n = await 1;
     console.log(n);
   }
   
   (async ()=>{
     await m();
     console.log(2);
   })();
   
   console.log(3);
   ```

   

6. 下面代码的输出结果是什么

   ```js
   async function m1(){
     return 1;
   }
   
   async function m2(){
     const n = await m1();
     console.log(n)
     return 2;
   }
   
   async function m3(){
     const n = m2();
     console.log(n);
     return 3;
   }
   
   m3().then(n=>{
     console.log(n);
   });
   
   m3();
   
   console.log(4);
   ```

7. 下面代码的输出结果是什么

   ```js
   Promise.resolve(1)	
     .then(2)
     .then(Promise.resolve(3))
     .then(console.log)
   ```

8. 下面代码的输出结果是什么

   ```js
   var a;
   var b = new Promise((resolve, reject) => {
     console.log('promise1');
     setTimeout(()=>{
       resolve();
     }, 1000);
   }).then(() => {
     console.log('promise2');
   }).then(() => {
     console.log('promise3');
   }).then(() => {
     console.log('promise4');
   });
   
   a = new Promise(async (resolve, reject) => {
     console.log(a);
     await b;
     console.log(a);
     console.log('after1');
     await a
     resolve(true);
     console.log('after2');
   });
   
   console.log('end');
   ```

9. 下面代码的输出结果是什么

   ```js
   async function async1() {
       console.log('async1 start');
       await async2();
       console.log('async1 end');
   }
   async function async2() {
   	console.log('async2');
   }
   
   console.log('script start');
   
   setTimeout(function() {
       console.log('setTimeout');
   }, 0)
   
   async1();
   
   new Promise(function(resolve) {
       console.log('promise1');
       resolve();
   }).then(function() {
       console.log('promise2');
   });
   console.log('script end');
   ```

   

















































