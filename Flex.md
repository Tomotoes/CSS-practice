# 浅谈Flex布局的属性及使用

网页布局是CSS的一个重点

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943af11f3a5?imageslim)

> normal flow（文档流）
> float + clear
> position relative + absolute
> display
> 负margin

这些属性在进行页面布局时，组合使用以实现所需要的页面，但对于一些特殊的布局，实现就有些麻烦了

## 1 Flex布局介绍

Flex 是 Flexible Box 的缩写，意思为“弹性布局”

### 1.1 Flex布局的特点

1. 块级布局侧重垂直方向、行内布局侧重水平方向，而Flex布局是与方向无关的
1. Flex布局可以实现空间自动分配、自动对齐（弹性、灵活）
1. Flex布局适用于简单的线性布局，更复杂的布局使用Grid布局

### 1.2 开启Flex布局

开启Flex布局时，只需要在父级元素上写上`display: flex;`，具体如下所示：

```css
.box{
  display: flex;
}
//行内元素也可以
.box{
  display: inline-flex;
}
//Webkit内核的浏览器，需加上前缀
.box{
  display: -webkit-flex;
}
```



### 1.3 Flex容器基本概念

采用Flex布局的元素，可以看做一个Flex容器，其属性表示如下图所示：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943acf1f859?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)



## 2 父元素的属性

Flex布局的父元素共有6中属性可以设置，分别为：

> flex-direction
> flex-wrap
> flex-flow
> justify-content
> align-items
> align-content

### 2.1 flex-direction

`flex-direction`属性决定主轴的方向（前面说过，不能说水平是主轴，垂直是侧轴，就是因为这个属性），它一共有4个值：

> row: 默认值，主轴为水平方向从左到右；
> row-reverse: 主轴为水平方向从右到左；
> column: 主轴为垂直方向从上到下；
> column-reverse: 主轴为垂直方向从下到上

示意图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943ace6104c?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

代码实现效果如下：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943acd4ac6a?imageslim)

### 2.2 flex-wrap

默认的情况下，Flex容器中的子元素都排在一行，如果子元素的总宽度大于父元素的宽度，子元素就会被压缩。`flex-wrap`属性可以设置子元素换行，它一共有3个值：

> nowrap: 默认值，不换行
> wrap: 换行，第一行在上方
> wrap: 换行，第一行在下方

示意图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943af279d28?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

代码实现效果图为：

![img](data:image/svg+xml;utf8,)

### 2.3 flex-flow

`flex-flow`属性是`flex-direction`和`flex-wrap`的组合，它是将这两个属性写到一起，先写`flex-direction`，后写`flex-wrap`，默认值为`row nowrap`

代码实现效果图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943e25760aa?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

### 2.4 justify-content

`justify-content`属性定义子元素在主轴上的对齐方式，它主要有5种取值：

> flex-start: 默认值，从起点开始
> flex-end: 从终点对齐
> cneter: 居中对齐
> space-between: 两端对齐，子元素之间的间隔相等
> space-around: 每个子元素的左右间隔相等

示意图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943f0601b02?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

代码实现效果图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943ee20cdf5?imageslim)

### 2.5 align-items

`align-items`属性定义子元素在侧轴上的对齐方式，主要由5种取值：

> strech: 默认值，子元素的高度铺满父元素
> flex-start: 子元素从侧轴起点对齐
> flex-end: 子元素从侧轴终点对齐
> center: 子元素根据侧轴居中对齐
> baseline: 根据子元素第一行文字的基线对齐(当字体大小不一致时，突出效果)

**注意：** 应用此属性时，子元素的高度不能写死，应该由其内容撑起来

示意图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab943f15401f7?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

代码实现效果图为：

![img](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="697" height="419"></svg>)

### 2.6 align-content

`align-content`属性定义子元素多根轴线在侧轴上的对齐方式，只在多行显示下有效。主要取以下5个值：

> stretch: 默认值，轴线铺满侧轴
> flex-start: 与侧轴起点对齐
> flex-end: 与侧轴终点对齐
> center: 与侧轴中点对齐
> space-between: 与侧轴两端对齐，轴线之间的间隔相等
> space-around: 每根轴线两侧的间隔相等

示意图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab94410ab2e33?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

代码实现效果图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab9441ed27f3d?imageslim)

## 3 子元素属性

Flex布局的子元素共有6种属性可以设置，分别为：

> flex-grow
> flex-shrink
> flex-basis
> flex
> order
> align-self

### 3.1 flex-grow

`flex-grow`属性表示当父元素空间有剩余时，将剩余空间分配给各子元素的比例，默认为`0`，表示不分配；当为数值时，表示父元素剩余空间分配给各子元素的比例，不是扩张后子元素的尺寸比例

代码实现效果图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab9441570e9a0?imageslim)

### 3.2 flex-shrink

`flex-shrink`属性与`flex-grow`属性的作用相反，表示当子元素宽度总和大于父元素宽度，且未换行显示时，各子元素压缩大小，默认为`1`，表示各子元素等比压缩；当数值不一时，表示各子元素因为压缩空间而减小的尺寸的比例，不是压缩后子元素尺寸的比例

代码实现效果图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab94432170a04?imageslim)

### 3.3 flex-basis

`flex-basis`属性可以用来设置子元素的空间，默认值为`auto`，表示为原本大小。当父元素有剩余空间时，可通过此属性扩充子元素的空间；各子元素通过扩孔之后的空间总和超过了父元素的空间大小时，按`flex-basis`值比例来设置子元素的大小，没有`flex-basis`属性时，默认`flex-basis`值为子元素原本大小，使子元素大小总和不得超过父元素空间大小

代码实现效果图为：

![img](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="573" height="298"></svg>)

### 3.4 flex

`flex`属性是`flex-grow`、`flex-shrink`和`flex-basis`的合集，默认值为`0 1 auto`，后两个属性可不写

### 3.5 order

`order`属性定义子元素在排列顺序，默认值为`0`，值越小越靠前

代码实现效果图为：

![img](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="573" height="437"></svg>)

### 3.6 align-self

`align-self`属性允许子元素单独设置对齐方式，优先级比父元素的`align-items`高。默认值为`auto`，表示继承父元素的`align-items`，如果没有父元素，则等同于`stretch`。其可设置以下属性：

> auto: 继承父元素的`align-items`
> stretch
> flex-start
> flex-end
> center
> baseline

除了`auto`值，其他值与父元素的`align-items`属性效果一样

## 4 几个flex布局

### 4.1 上中下布局

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
  <style>
    body{
      display: flex;
      flex-direction: column;
      height: 100vh;
    }
    header{
      height: 100px;
      background: #ddd;
    }
    main{
      flex-grow: 1;
    }
    footer{
      height: 100px;
      background: #ddd;
    }
  </style>
</head>
<body>
<header>heafer</header>
<main>main</main>
<footer>footer</footer>
</body>
</html>
```

代码效果图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab94455a18520?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

### 4.2 九宫格

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
  <style>
    *{padding:0;}
    ul{
      list-style: none;
      border: 1px solid black;
      width: 170px;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
    }
    li{
      width: 50px;
      height: 50px;
      border: 1px solid red;
      margin: 5px 0;
    }
  </style>
</head>
<body>
<ul>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul>
</body>
</html>
```

代码效果图为：

![img](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="195" height="210"></svg>)

### 4.3 一般PC布局

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
  <style>
    body{
      display: flex;
      flex-direction: column;
      height: 100vh;
    }
    header{
      height: 50px;
      background: #ddd;
    }
    main{
      flex-grow: 1;
      display: flex;
    }
    .aside1{
      width: 100px;
      background: #aaa;
    }
    .aside2{
      flex-grow: 1;
    }
    .aside3{
      width: 100px;
      background: #aaa;
    }
    footer{
      height: 50px;
      background: #ddd;
    }
  </style>
</head>
<body>
<header>header</header>
<main>
  <aside class="aside1">aside1</aside>
  <aside class="aside2">aside2</aside>
  <aside class="aside3">aside3</aside>
</main>
<footer>footer</footer>
</body>
</html>
```

代码效果图为：

![img](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="528" height="686"></svg>)

### 4.4 自适应绝对居中

```

```

代码效果图为：

![img](https://user-gold-cdn.xitu.io/2018/5/29/163ab944630bd9a0?imageslim)