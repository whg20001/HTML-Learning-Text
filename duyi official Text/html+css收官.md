# 腾讯课堂

# 初识别HTML，CSS

## 权重

![](https://github.com/whg20001/blog-image/blob/main/img/quanzhong.png?raw=true)

权重之间的进制是255

在写css时同一行的标签直接相加得出总的权重值。

## 选择器

| 选择器名称     | 选择器语法              |
| -------------- | ----------------------- |
| 标签选择器     | 直接使用标签            |
| 类选择器       | 直接使用类名            |
| id选择器       | 直接使用id名            |
| 父类选择器     | 父类标签+空格+子类标签  |
| 父类直接选择器 | 父类标签+>+子类标签     |
| 联合选择器     | 第一个标识+第二个标识   |
| 并列选择器     | 第一个标识+，+第二个+…… |

```html
    <div>
        <em>this is four</em>

        <ul>
            <li>this is second</li>
            <em class="em_class">first</em>
        </ul>

    </div>

    <div class="test_class">this is third</div>
```

```css
/* 选择器 */
/* 直接选择器 */
div {
    width: 200px;
    height: 200px;
    border: solid 1px silver;
}

/* 类别选择器 */
.em_class {
    color: red;
}

/* 父类选择器 */
div li {
    color: aquamarine;
}


div .em_class {
    border: solid 1px red;
}

/* 联合选择器 */
div.test_class {
    color: blanchedalmond;
}

/* 并列选择器 */
div.test_class,
.em_class {
    border-radius: 10px;
}

/* 直接子代选择器 */
div>em {
    color: cadetblue;
}
```



## 定位

relative定位

使用该定位的对象原始位置的空间依旧占着,即保留原来空间

定位参考的是自己原来的位置进行定位

存在的问题：定位为relative时，使用top：50%不起作用



absolute定位

使用该对象的原始位置不会占有

定位的参考对象优先查看父级及以上是否含有定位，若是没有则相对于文档定位



==一般使用relative使元素成为定位参照对象，再使用absolute对元素进行定位==



fixed定位

使得元素固定位

fixed的定位对象和absolute一样



## 两栏布局

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        * {
            padding: 0;
            margin: 0;
        }

        .right {
            background-color: aqua;
            height: 100px;
            width: 100px;
            position: absolute;
            right: 0;
            opacity: 0.5;
        }

        .left {
            background-color: red;
            height: 100px;
            margin-right: 100px;

        }
    </style>
</head>

<body>
    <div class="right"></div>
    <div class="left"></div>
</body>

</html>
```

结果图：

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-21_22-51-28.png?raw=true)



## margin塌陷

使用margin-top时，父级随子元素一起移动

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-22_16-37-21.png?raw=true)

解决方法：触发BFC

如何触发BFC？

> 1. position:absolute
> 2. display:inline-block
> 3. float:left/right
> 4. overflow:hidden

## margin合并BUG

对于行级元素，两个元素不共用margin区域

对于块级元素，两个元素之间共用margin区域

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-22_16-56-19.png?raw=true)

解决方法：

​	触发BFC解决

​	![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-22_17-01-25.png?raw=true)

==但是这个方法可以不解决，不影响开发==

 

## 浮动

1. 浮动元素产生浮动流，所有产生了浮动流的元素，块级元素看不到他们，产生了BFC的元素和文本属性的元素（即inline属性）以及文本都能看到浮动元素

2. 浮动的解决需要使用伪元素来解决。通过伪元素调用clear属性。值得注意的是clear只适用于块级样式。

   ![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-22_20-52-13.png?raw=true)

3. 伪元素必须使用content。



> 要想在浮动时让外部包裹主其中的内容，使用伪元素以及clear属性，注意该属性==只对block元素生效==。



> 使用position：absolute和float：left/right会从内部将元素换成line-block



## line-height

行高表示文本所占的高度多少。

em



## 文本溢出处理

文本溢出处理分为两种，第一种是对单行文本的溢出处理通过打点的手法，对于多行文本的处理是使用截断手法，不做打点处理

### 单行文本(三件套)

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_09-35-29.png?raw=true)



### 多行文本

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_09-43-13.png?raw=true)



## 对于背景图片的处理

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_10-22-24.png?raw=true)



## 对于默认加载策略处理(网速不好情况，屏蔽了CSS和js，只展示HTML)

> 对于默认加载策略下，只展示HTML的情况下，保证基本功能可以使用

### 方法一（推荐）

将背景图片设置在padding中

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_10-43-245.png?raw=true)

### 方法二

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_10-48-40.png?raw=true)

第二种将文字通过缩进和不换行属性移动到框外然后使用隐藏特性



## 提醒：

​	行级元素只能套行级元素

​	块级元素可以套任何元素

​	p标签不能套块级元素

​	a标签不能套a标签



## margin的一个重要应用

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_11-30-18.png?raw=true)

通过margin来对元素居中同时根据页面大小来变化左右margin值



## inline-block的一个小问题

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_11-38-31.png?raw=true)

在span中没有内容时，字体与span底对齐



![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_11-40-34.png?raw=true)

当标签内有内容时，与内容对齐



## vertical-align调整对齐线

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_13-40-10.png?raw=true)

vertical-align可以调整对齐线。





## 小案例

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            height: 50px;
            width: 250px;
            border: solid 1px silver;
            line-height: 50px;
            padding: 0 15px;
            background-color: yellow;
            border-radius: 5px;
            /* cursor: pointer; */
        }

        div:hover {
            color: green;
        }

        div::before {
            content: '';
            display: inline-block;
            background-image: url("../BG/icon.png");
            height: 25px;
            width: 25px;
            background-size: 100% 100%;
            vertical-align: -6px;
            margin-right: 5px;
        }

        div::after {
            content: "";
            /* display: inline-block; */
            background-image: url('../BG/icon_out.png');
            height: 25px;
            width: 25px;
            background-size: 80% 80%;
            background-repeat: no-repeat;
            float: right;
            margin-top: 15px;
            transition: 0.5s;
            cursor: pointer;
        }
    </style>
</head>

<body>
    <div>姬吧</div>
</body>

</html>
```

效果图：

​	![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_14-34-23.png?raw=true)





## 写出常见的行级元素和块级元素

### 行级标签(inline)

**a，span，strong，u（下划线），em(强调)，i(斜体)，sub(下标),sup(上标)**

### 块级标签(block)

**div，p，h1-h6，ul，li，dl（定义列表，跟ul…li类似），dt（定义了定义列表中的项目），dd（定义描述项目的内容，跟dt一起搭配）**

### 行内标签（inline-block）

**textarea，input，img，button**



## 作业：淘宝页面仿写

![](https://github.com/whg20001/blog-image/blob/main/img/Snipaste_2022-10-23_14-53-10.png?raw=true)







# CSS收官

# 布局

![image-20210511102549096](http://mdrs.yuanjin.tech/img/20210511102802.png)

**浮动**：做文字环绕效果

**弹性盒**：单行或单列布局

**网格**：多行多列布局

## 弹性盒

> 详细文档见[MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout)
>
> [弹性盒小游戏](https://flexboxfroggy.com/)

### 生成弹性容器和弹性项目

![image-20210511112624876](http://mdrs.yuanjin.tech/img/20210511112624.png)

**默认情况下，**弹性项目沿着主轴依次排列，侧轴拉伸

### 更改方向

通过`flex-direction`可更改主轴方向

![image-20210511112510632](http://mdrs.yuanjin.tech/img/20210511112510.png)

### 主轴排列

通过`justify-content`属性，可以影响主轴的排列方式

![image-20210511113617325](http://mdrs.yuanjin.tech/img/20210511113617.png)

### 侧轴排列

通过`align-items`属性，可以影响侧轴的排列方式

![image-20210511114016304](http://mdrs.yuanjin.tech/img/20210511114016.png)

### 弹性项目伸缩

所谓伸缩，是指在**主轴方向**上，当**弹性容器**有**额外空间**时，是否需要拉伸，当**空间不足**时，是否需要**压缩**

在**弹性项目**上使用`flex`属性，可设置拉伸和压缩比例：`flex: 拉伸比例 压缩比例 初始尺寸`

拉伸示例：

![image-20210511120916571](http://mdrs.yuanjin.tech/img/20210511120916.png)

压缩示例：

![image-20210511121459341](http://mdrs.yuanjin.tech/img/20210511121459.png)

默认情况下，`flex: 0 1 auto`

### 主轴换行

默认情况，当主轴剩余空间不足时，按照压缩比例进行压缩，但如果设置了主轴换行，则不会压缩，直接换行显示

给**弹性容器**设置`flex-wrap: wrap`，即可主轴换行

<img src="http://mdrs.yuanjin.tech/img/20210511123310.png" alt="image-20210511123310673" style="zoom:50%;" />

> 尽管如此，多行多列仍然推荐使用网格布局

## 网格

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Grid_Layout)
>
> [阮一峰网格布局教程](http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html)
>
> [网格布局小游戏](https://cssgridgarden.com/)

**网格布局是多行多列布局的终极解决方案**

### 生成网格布局

<img src="http://mdrs.yuanjin.tech/img/20210511165317.png" alt="image-20210511165317363" style="zoom:50%;" />

容器生成网格布局后，其所有子元素为**网格项目**

### 定义行和列

`grid-template-rows`：定义行

`grid-template-columns`：定义列

**它们的语法是相同的**

![image-20210511172305100](http://mdrs.yuanjin.tech/img/20210511172305.png)

### 改变排列方向

使用属性`grid-auto-flow: column`，可使子元素按列排放

<img src="http://mdrs.yuanjin.tech/img/20210511173447.png" alt="image-20210511173447321" style="zoom:50%;" />

### 单元格之间的间隙

```css
row-gap: 10px; /* 行间隙为10px */
column-gap: 20px; /* 列间隙为20px */
gap: 10px 20px; /* 行间隙为10px，列间隙为20px */
```

![image-20210512132025687](http://mdrs.yuanjin.tech/img/20210512132025.png)

### 单元格内部的对齐

默认情况下，网格项目在单元格内部水平和垂直拉伸，以撑满单元格

可以使用属性`justify-items`设置**水平方向**的排列方式

可以使用属性`align-items`设置**垂直方向**的排列方式

它们的可取值是相同的：

```css
justify-items: start 左 | end 右 | center 中 | stretch 拉伸;
align-items: start 上 | end 下 | center 中 | stretch 拉伸;
```

<img src="http://mdrs.yuanjin.tech/img/20210511174450.png" alt="image-20210511174450356" style="zoom:50%;" />

可以使用速写属性`place-items: 垂直对齐方式 水平对齐方式`同时设置这两个值

```css
place-items: start center; /* 垂直靠上，水平居中 */
```

### 网格项目定位

默认情况下，网格项目依次排列到单元格中，每个网格占据一个单元格

但可以对网格项目设置`grid-area`属性来改变这一行为

使用方式为：

```css
grid-area: 起始行线编号/起始列线编号/结束行线编号/结束列线编号;
```

<img src="http://mdrs.yuanjin.tech/img/20210511180028.png" alt="image-20210511180027983" style="zoom:50%;" />

# 视觉

> 所谓视觉类样式，是指不影响盒子位置、尺寸的样式，例如文字颜色、背景颜色、背景图片等

## 阴影

### 盒子阴影

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow)

通过`box-shadow`属性可以设置整个盒子的阴影

下面是一些示例

<iframe src="http://mdrs.yuanjin.tech/html/css-manual/box-shadow.html?v=2" style="height:900px;">


### 文字阴影

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow)

通过`text-shadow`可以设置文字阴影

下面是一些示例

<iframe src="http://mdrs.yuanjin.tech/html/css-manual/text-shadow.html?v=3" style="height:500px;">


## 圆角

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius)

通过设置`border-radius`，可以设置盒子的圆角

![image-20210512131026084](http://mdrs.yuanjin.tech/img/20210512131026.png)

`border-radius`可以有很多灵活的用法，将下面的代码依次粘贴到页面中测试一下

```css
border-radius: 10px; /* 同时设置4个角的圆角，半径为10px */
border-radius: 50%; /* 同时设置4个角的圆角，圆的横向半径为宽度一半，纵向半径为高度一半 */
border-radius: 10px 20px 30px 40px; /* 分别设置左上、右上、右下、左下的圆角 */
```

<iframe src="http://mdrs.yuanjin.tech/html/css-manual/border-raduis.html?v=5" style="height:550px;">


## 背景渐变

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/linear-gradient())

在设置**背景图片**时，除了可以使用`url()`加载一张背景图，还可以使用`linear-gradient()`函数设置背景渐变

`linear-gradient()`用于创建一张渐变的图片，语法为：

```css
/* 设置渐变背景，方向：从上到下，颜色：从#e66465渐变到#9198e5 */
background: linear-gradient(to bottom, #e66465, #9198e5);
```

![image-20210512135024676](http://mdrs.yuanjin.tech/img/20210512135028.png)

## 变形

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform)

通过`transform`属性，可以使盒子的形态发生变化

该属性支持多种变形方案，常见的有:

- translate，平移
- scale，缩放
- rotate，旋转

**无论是哪一种transform，都只是视觉效果的变化，不会影响盒子的布局**

**transform不会导致浏览器reflow和rerender，因此效率极高**

### translate 平移

使用`translate`可以让盒子在原来位置上产生位移，类似于相对定位

![image-20210512140622630](http://mdrs.yuanjin.tech/img/20210512140643.png)

### scale 缩放

使用`translate`可以让盒子在基于原来的尺寸发生缩放

![image-20210512141500499](http://mdrs.yuanjin.tech/img/20210512141500.png)

### rotate 旋转

使用`rotate`属性可以在原图基础上进行旋转

```css
/* 在原图的基础上，顺时针旋转45度角 */
transform: rotate(45deg); 
/* 在原图的基础上，顺时针旋转半圈 */
transform: rotate(0.5turn); 
```

可以点击下面的按钮试一下旋转效果

<iframe src="http://mdrs.yuanjin.tech/html/css-manual/rotate.html" style="height:400px;">




### 改变变形原点

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform-origin)

变形原点的位置，会影响到具体的变形行为

默认情况下，变形的原点在盒子中心，你可以通过`transform-origin`来改变它

```css
transform-origin: center; /* 设置原点在盒子中心 */
transform-origin: left top; /* 设置原点在盒子左上角 */
transform-origin: right bottom; /* 设置原点在盒子右下角 */
transform-origin: 30px 60px; /* 设置原点在盒子坐标 (30, 60) 位置 */
```

试一试，先点击设置原点的按钮来设置原点(已在图片中使用红色小点标记)，然后点击变形按钮进行变形

<iframe src="http://mdrs.yuanjin.tech/html/css-manual/transform-origin.html?v2" style="height:600px;">


### 多种变形叠加

可以一次性设置多种变形效果

```css
/* 先旋转45度，再平移(100,100) */
transform: rotate(45deg) translate(100px, 100px);
/* 先平移(100, 100)，再旋转45度 */
transform: translate(100px, 100px) rotate(45deg);
```

注意：旋转会导致坐标系也跟着旋转，从而可能影响到后续的变形效果

下面的例子可以很好的说明这一点

http://mdrs.yuanjin.tech/html/css-manual/multi-transform.html

> 本来打算把这个效果嵌入到markdown，但由于嵌入后出现一些未知的bug，因此只能粘贴效果地址了

# 过渡和动画

使用过渡和动画，可以让css属性变化更加丝滑

**过渡和动画无法对所有的CSS属性产生影响，能够产生影响的只有数值类属性**，例如：颜色、宽高、字体大小等等

## 过渡

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transition)

```css
transition: 过渡属性 持续时间 过渡函数 过渡延迟
```

- **过渡属性**

  针对哪个css属性应用过渡。例如填写`transform`，则表示仅针对**transform**属性应用过渡。

  若填写`all`或不填写，则表示针对所有css属性都应用过渡

- **持续时间**

  css属性变化所持续的时间，需要带上单位。例如`3s`表示3秒，`0.5s`或`500ms`均表示500毫秒

- **过渡函数**

  本质是css属性变化的贝塞尔曲线函数，通常直接使用预设值：

  `ease-in-out`：平滑开始，平滑结束

  `linear`：线性变化

  `ease-in`：仅平滑开始

  `ease-out`：仅平滑结束

- **过渡延迟**

  书写规则和持续时间一样，表示过渡效果延迟多久后触发，不填则无延迟

**在JS中，可以监听元素的`transitionstart`和`transitionend`事件，从而在过渡开始和过渡结束时做一些别的事情**

## 动画

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Animations)

**动画的本质是预先定义的一套css变化规则，然后给该规则取个名字**

![image-20210513172902413](http://mdrs.yuanjin.tech/img/20210513172902.png)

然后，其他元素即可使用这样的规则：

```css
animation: 规则名 持续时间;
```

在应用规则时，还可以指定更多的信息

```css
animation: 规则名 持续时间 重复次数 时间函数 动画方向 延迟时间
```

一些细节：

- 定义规则时，`0%`可以书写为`from`
- 定义规则时，`100%`可以书写为`to`
- 重复次数为`infinite`时，表示无限重复
- 动画方向为`alternate`时，表示交替反向，第1次正向，第2次反向，第3次正向，第4次方向，以此类推

**在JS中，可以监听元素的`animationstart`和`animationnend`事件，从而在过渡开始和过渡结束时做一些别的事情**

# 其他

## box-sizing

一图胜千言

![image-20210514150015660](http://mdrs.yuanjin.tech/img/20210514150015.png)

使用`border-box`控制尺寸更加直观，因此，很多网站都会加入下面的代码

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

## 字体图标

> [MDN font-face 指令](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@font-face)

css3新增了`font-face`指令，该指令可以让我们加载网络字体

其最常见的应用就是字体图标

**字体图标本质上是文字，即通过`color`设置颜色，通过`font-size`设置尺寸**

国内使用最多的字体图标平台是[阿里巴巴矢量图标库](https://www.iconfont.cn/)

登录平台后即可免费使用其所有字体图标

## 图像内容适应

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/object-fit)

css3属性`object-fit`可以控制**多媒体内容和与元素**的适应方式，通常应用在`img`或`video`元素中

一图胜千言

下图中的所有`img`元素均被固定了宽高，溢出img的部分实际上均不会显示

![image-20210514134908778](http://mdrs.yuanjin.tech/img/20210514134908.png)

## 视口单位

css3支持使用`vw`和`vh`作为单位，分别表示`视口宽度`和`视口高度`

例如`1vh`表示视口高度的`1%`，`100vw`表示视口宽度的`100%`

## 伪元素选择器

通过`::before`和`::after`选择器，可以通过css给元素生成两个子元素

<img src="http://mdrs.yuanjin.tech/img/20210514140049.png" alt="image-20210514140049244" style="zoom:50%;" />

使用伪元素可以避免在HTML中使用过多的空元素

**伪元素必须要有`content`属性，否则不能生效，如果不需要有元素内容，设置`content:''`**

## 平滑滚动

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/scroll-behavior)

使用`scroll-behavior: smooth`，可以让滚动更加丝滑

参见MDN效果即可



# HTML收官



<img src="http://mdrs.yuanjin.tech/img/20210518112557.png" alt="image-20210518112556986" style="zoom:50%;" />

HTML5包含两个部分的更新，分别是`文档`和`web api`

# 文档

[HTML5元素表](http://www.html5star.com/manual/html5label-meaning/)

## 元素语义化

元素语义化是指**每个HTML元素都代表着某种含义，在开发中应该根据元素含义选择元素**

元素语义化的好处：

1. 利于SEO（搜索引擎优化）
2. 利于无障碍访问
3. 利于浏览器的插件分析网页

## 新增元素

### 多媒体

可以使用`audio`元素表达一个音频

可以使用`video`元素表达一个视频

它们均具有以下属性

| 属性名   | 含义             | 类型     |
| -------- | ---------------- | -------- |
| src      | 多媒体的文件路径 | 普通属性 |
| controls | 是否显示播放控件 | 布尔属性 |
| autoplay | 是否自动播放     | 布尔属性 |
| loop     | 是否循环播放     | 布尔属性 |
| muted    | 静音播放         | 布尔属性 |

> 新版浏览器不允许「带声音的自动播放」，可能将来甚至不允许自动播放
>
> 浏览器希望播放行为由用户决定

### 文章结构

为了让搜索引擎和浏览器更好的理解文档内容，HTML5新增了多个元素来表达内容的含义。

下面的示例中，使用了HTML5的新增元素来表达一篇文章

```html
<!-- article：一篇文章 -->
<article>
  <!-- header：文章头部信息 -->
  <header>
    <h1>文章标题</h1>
    <!-- blockquote：引用信息 -->
    <blockquote>此文章引用的文献：xxxx</blockquote>
  </header>
  <!-- aside: 文章的其他附加信息 -->
  <aside>
    <span>作者：xxxx</span>
    <span>发布日期：xxx</span>
    <span>浏览量：xxx</span>
  </aside>
  <!-- section：章节 -->
  <section>
    <h2>章节1</h2>
    <p>段落1</p>
    <p>段落2</p>
    <p>段落3</p>
    <p>段落4</p>
  </section>
  <!-- section：章节 -->
  <section>
    <h2>章节2</h2>
    <p>段落1</p>
    <p>段落2</p>
    <p>段落3</p>
    <p>段落4</p>
  </section>
  <!-- section：章节 -->
  <section>
    <h2>章节3</h2>
    <p>段落1</p>
    <p>段落2</p>
    <p>段落3</p>
    <p>段落4</p>
  </section>
  <!-- 页脚 -->
  <footer>
    <p>参考资料</p>
    <!-- cite表示外部站点的引用 -->
    <cite>xxxxxxx</cite>
    <cite>xxxxxxx</cite>
    <cite>xxxxxxx</cite>
    <cite>xxxxxxx</cite>
    <cite>xxxxxxx</cite>
    <cite>xxxxxxx</cite>
  </footer>
</article>
```

## 新增属性

### 自定义数据属性

<img src="http://mdrs.yuanjin.tech/img/20210518123117.png" alt="image-20210518123117393" style="zoom:50%;" />

### input的新增属性

> [MDN input详细文档](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input)

进入下面的地址查看各种属性及其效果

http://mdrs.yuanjin.tech/html/html-manual/input-property.html

# web api

## 使用css选择器选中元素

```js
// 使用css选择器选中匹配的第一个元素
document.querySelector('css选择器');
// 使用css选择器选中匹配的所有元素，返回伪数组
document.querySelectorAll('css选择器');
```

## 控制类样式

```js
// 添加类样式
dom.classList.add('a');  // <div class="a"></div>
dom.classList.add('b');  // <div class="a b"></div>
dom.classList.add('c');  // <div class="a b c"></div>

// 是否包含某个类样式
dom.classList.contains('a');  // true 

// 移除类样式
dom.classList.remove('a');  // <div class="b c"></div>

// 切换类样式
dom.classList.toggle('a'); // <div class="a b c"></div>
dom.classList.toggle('a'); // <div class="b c"></div>
dom.classList.toggle('a'); // <div class="a b c"></div>
```

## 本地存储

`localStorage`，永久保存到本地

`sessionStorage`，临时保存到本地，关闭浏览器后消失

```js
// 保存一个键值对到本地，值必须是字符串
localStorage.setItem('key', 'value');
// 根据键，读取本地保存的值
localStorage.getItem('key');
// 清除所有保存的内容
localStorage.clear();
// 根据键，清除指定的内容
localStorage.removeItem('key');

// 保存一个键值对到本地，值必须是字符串
sessionStorage.setItem('key', 'value');
// 根据键，读取本地保存的值
sessionStorage.getItem('key');
// 清除所有保存的内容
sessionStorage.clear();
// 根据键，清除指定的内容
sessionStorage.removeItem('key');
```

无论是`localStorage`还是`sessionStorage`，它们都只能保存字符串，如果需要保存对象或数组，可以先将对象和数组转换为`JSON`字符串再进行保存

```js
JSON.stringify(obj); // 将对象或数组转换为JSON搁置
JSON.parse(jsonString); // 将JSON格式的字符串转换为对象或数组
```



## 渲染帧

浏览器会不断的对网页进行渲染，通常情况下的速度为每秒渲染60次，每一次渲染称之为**一帧**，因此又可以说：浏览器的渲染速率是60帧

但这不是一定的，它会受到各种因素的影响，因此，帧率往往会有浮动

浮动的帧率就导致一个问题，我们在使用`setInterval`等计时器实现某些动画效果时，如何才能保证每一帧只执行一次动画效果呢？

![image-20210518133821647](http://mdrs.yuanjin.tech/img/20210518133821.png)

为了解决该问题，HTML5新增API`requestAnimationFrame`，用于在每一帧渲染**之前**做某些事

```js
requestAnimationFrame(function(){
  // 传入一个回调函数，该函数在下一帧渲染之前自动运行
  // 通常，可以利用该回调函数，在下一帧渲染前改动元素的状态
})
```

`raq`的回调函数仅执行一次，因此，要实现连贯的动画，通常使用下面的代码结构

```js
// 该函数负责在下一帧渲染前，执行一次元素状态变化
function changeOnce(){
  requestAnimationFrame(function(){
    if(动画是否应该停止){
      return;
    }
    改变元素状态
    changeOnce(); // 改变完成后，继续注册下一针的变化
  })
}
changeOnce();
```

## 音视频API

> [MDN详细文档](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLMediaElement)

针对`video`和`audio`元素，HTML5新增了音视频的API，让开发者可以使用JS控制它们

**音视频属性**

| 属性名       | 含义                                                         |
| ------------ | ------------------------------------------------------------ |
| currentTime  | 当前播放时间，单位为秒。为其赋值将会使媒体跳到一个新的时间。 |
| loop         | 对应HTML标签`loop`属性，决定该媒体是否循环播放.              |
| controls     | 对应HTML标签`controls`属性，控制是否显示用户播放界面的控制 HTML |
| src          | 对应HTML标签`src`属性，获取和设置播放地址                    |
| volume       | 表示音频的音量。值从0.0（静音）到1.0（最大音量）。           |
| playbackRate | 播放倍速。1为正常。                                          |
| duration     | 总时长，单位为秒。                                           |
| paused       | 当前是否是暂停状态                                           |
| muted        | 是否静音                                                     |

**音视频方法**

| 方法名  | 含义     |
| ------- | -------- |
| play()  | 开始播放 |
| pause() | 暂停播放 |

**事件**

| 事件名     | 含义                                                      |
| ---------- | --------------------------------------------------------- |
| pause      | 暂停时触发                                                |
| ended      | 结束时触发                                                |
| play       | 开始播放时触发                                            |
| timeupdate | 属性`currentTime`变化时触发。会随着播放进度的变化不断触发 |
| loadeddata | 事件在第一帧数据加载完成后触发                            |

