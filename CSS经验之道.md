伪元素的默认display属性是inline 



基于文件格式使用不同的样式



```css
a[href^="http://"]{
    padding-right: 20px;
    background: url(external.gif) no-repeat center right;
}
/* emails */
a[href^="mailto:"]{
    padding-right: 20px;
    background: url(email.png) no-repeat center right;
}

/* pdfs */
a[href$=".pdf"]{
    padding-right: 20px;
    background: url(pdf.png) no-repeat center right;
}

```



#### content属性

这是一个非常非常容易被忽视的属性，很多小伙伴在使用伪元素的时候都容易犯错：“为啥我的伪元素没有显示出来？”，最后一查才发现，是自己的content属性没有设置，导致伪元素不显示，那么content元素究竟可以填哪些东西呢？

#### string

最简单的不过如此，上面例子1中给书名添加书名号的就是string类型

#### attr()

嗯哼，这是什么值，难不成还能设置元素的attr？我们来一串代码解释一下：

```html
<style>
    .test1::after {
        content: attr(class)
    }
    .test2::after {
        content: attr(href)
    }
</style>

<body>
    <span class="test1">this el's class is :</span>
    <br>
    <a class="test2" href="baidu.com">百度:</a>
</body>
```

如图：

![image](http://oyxdyxgq8.bkt.gdipper.com/2E2D24BD-801F-4131-8D76-B8681FC587DD.png)

非常好理解，就是在元素后面加上该元素的属性值。

#### url()

这个属性是用来索引媒体文件，比如一个放一个图片，经过测试，对mp4、pdf、mp3格式的文件并不能显示出来：

```html
<style>
    .test1::before {
        content: url("https://sfault-avatar.b0.upaiyun.com/124/827/1248273836-57c7f5f15344a_big64");
    }
</style>

<body>
    <span class="test1">there is a pic before the el</span>
</body>
```

如图：![image](http://oyxdyxgq8.bkt.gdipper.com/AEAAD9CE-1E59-42E3-B731-10ED8AB44AF5.png)

### counter()

CSS中有个计数器属性，就能能够像一个树状图一样列出1.1 1.2这样的目录结构，对于这个属性，后续我也会专门出一篇博文来总结它的使用方式。对于伪元素来说，能定制计数器的分隔符号，说的有点抽象，我们来个demo：

```html
<style>
    body{
    counter-reset: section;
    }
    h1{
        counter-reset: subsection;
    }
    h1:before{
        counter-increment:section;
        content:counter(section) "、";
    }
    h2:before{
        counter-increment:subsection;
        content: counter(section) "-" counter(subsection) "、";
    }
</style>

<body>
    <h1>CSS的世界</h1>
    <h2>color</h2>
    <h2>fonst-size</h2>
    <h2>backgroung</h2>

    <h1>HTML的世界</h1>
    <h2>div</h2>
    <h2>ul</h2>

    <h1>Javascript的世界</h1>
    <h2>原型</h2>
    <h2>闭包</h2>
</body>
```

如图：

![image](http://oyxdyxgq8.bkt.gdipper.com/59993A8B-9142-4938-B5D5-AE12E1B9A6DF.png)

也就是说能够定制每个分隔的符号，计数器属性非常好用，就像之前之前给书名加上书名号的那个例子一样，以防后端不给你序列号～



### 单位

  px: 像素
  in: 英寸
  mm: 毫米
  q: 1/4毫米
  cm: 厘米
  pt: 磅
  pc: 派卡
  %: 百分比
  em: 根据文档字体计算尺寸
  rem: root em根据根文档字体计算尺寸
  ex: 文档字符”的高度
  ch: 文档数字0的的宽度
  vh: 视口高度的 1/100
  vw: 视口宽度的 1/100
  vmin: 视口高度和宽度之间的最小值的 1/100
  vmax: 视口高度和宽度之间的最大值的 1/100

backface-visibility 属性定义当元素不面向屏幕时是否可见。
如果在旋转元素不希望看到其背面时，该属性很有用。


img {
  transition: .4s ease-in-out;
  &:hover{
    transition: all .2s .1s;
    transform: scale(1.8);
  }
}
有的时候 mouseout不会触发过渡效果 
是因为 你把 过渡写在了 hover里面


利用hover触发 will-change
&:hover {
  will-change: left, top, width, height;
}


inline-block 布局
你可以使用 inline-block 来布局。有一些事情需要你牢记：

vertical-align 属性会影响到 inline-block 元素，你可能会把它的值设置为 top 。
你需要设置每一列的宽度
如果HTML源代码中元素之间有空格，那么列与列之间会产生空隙



使用 max-width 替代 width 可以使浏览器更好地处理小窗口的情况。这点在移动设备上显得尤为重要

常见的例子是：把 li 元素修改成 inline，制作成水平菜单。

rem是根据根的font-size变化，em是根据父级的font-size变化

background-clip: border-box（默认值）
背景延伸到边框外沿（但是在边框之下）。

background-clip: padding-box
边框下面没有背景，即背景延伸到内边距外沿。

background-clip: content-box
背景裁剪到内容区 (content-box) 外沿。

background-clip: text
背景被裁剪为文字的前景色。

background-clip: inherit


~ 兄弟选择器，同一个父级的兄弟元素


display:inline-block将对象呈递为内联对象，但是对象的内容作为块对象呈递。旁边的内联对象会被呈递在同一行内，允许空格。

inline:
	使元素变成行内元素，拥有行内元素的特性，即可以与其他行内元素共享一行，不会独占一行. 
	不能更改元素的height，width的值，大小由内容撑开. 
	可以使用padding，margin的left和right产生边距效果，但是top和bottom就不行.

block:
	使元素变成块级元素，独占一行，在不设置自己的宽度的情况下，块级元素会默认填满父级元素的宽度. 
	能够改变元素的height，width的值. 
	可以设置padding，margin的各个属性值，top，left，bottom，right都能够产生边距效果.

inline-block:
结合了inline与block的一些特点，结合了上述inline的第1个特点和block的第2,3个特点.
用通俗的话讲，就是不独占一行的块级元素。

如果设置 padding margin，会改变所处一行的位置，并非牵连到一行的 inline元素




padding

对于block元素
1. padding值暴走，一定会影响尺寸
2. width非auto，padding影响尺寸 （平时可见）
3. width为auto，或 box-sizing为border-box，同时padding值没有暴走，不影响尺寸

对于inline元素
水平padding影响尺寸，垂直padding不影响尺寸
垂直padding影响背景尺寸，垂直的背景尺寸 会脱离文档流，很奇怪

padding 不支持任何形式的负值

padding的百分比均是相对于宽度计算的


css正方形背景图
{
	padding:50%
	background:url(exp.jpg);
	background-size:100%;
	position:relative;
}

inline水平元素的padding百分比值（有三个特点）：
 1）同样相对于宽度计算；
 2）默认的高度宽度细节有差异；//会让规范中“strut”出现，让高比宽更大
 3）padding会断行



设计 button 可以通过 设计label，来实现 样式百分百兼容


1.border-width不支持百分比，原因不同设备的border-width设置一样 
2.还有outline  box-shadow  text-shadow也有此特性
3.属性关键字：thin（1px） medium（默认3px ）thick（5px）
因为border-style:double 只有3px 才能显示出来

border-style:
solid 实线

dashed 虚线
	Chrome/FireFox：宽高 3:1
	IE：宽高 2:1

dotted 点线
	Chrome/FireFox：方形
	IE：圆形

double 双线 
1px：0+1+0
2px: 1+0+1
3px: 1+1+1

三道杠
border-top:60px double;
border-bottom:20px solid;

inset 内凹 兼容性差


border-color box-shadow text-shadow 默认使用就是当前的 color

background-position 默认是相对左上方定位


position: relative;left：10px;top:10px;
relative 的第一个作用：起到定位的作用；left和top是指相对于它原来位置的定位。
relative 是不脱离文档流的（意思就是它原有的位置是保留的，其他元素无法占据）。所以相对定位通常只是用作限制绝对定位的。
如截图所示，relative 对absolute的限制有三方面
1、限制定位
2、限制z-index层级（就是说，如果relative设置了z-index层级并且为具体的数字，而不是auto，那么内部的absolute设置的层级就不管用了）
3、限制在overflow下的嚣张气焰（只有加上relative，overflow：hidden、auto，滚动条，才会对absolute定位的元素起作用）
relative 对 fixed 的限制只有z-index


relative 相对于自身定位，不会影响其他元素的布局
无侵入：即他不会影响其他元素的布局，比如说：如果是margin-top：-100px；移走后，紧接着这个div的div也会向上移动；如果是top:-100px，则不会，后面的元素会保持不动.应用：自定义拖拽

当top和bottom，或者left和right同时存在时，如果是relative定位，这只有一方存在，即top和left；
但如果是absolute定位，这两者可以同时存在，起到拉伸的效果

z-index 值越大，越靠近用户
relative 在层级方面的表现：
1. 提高层叠上下文（鬼畜级别）
页面有两张图片出现层叠情况，默认后一张图片层叠前一张，如果设置前一张图片position：relative，则前一张会层叠在前
2.新建层叠上下文与层级控制
relative 的z-index 为一个具体的数值，那么就会新建一个层叠上下文，从而限制内部absolute元素的层叠。而为auto（可以dayue 理解为z-index 为0）的话，就不会新建一个层叠上下文（ie6、7除外，是个bug）


relative 的最小化影响原则，指的是尽量降低relative属性对齐他元素或布局的潜在影响。
relative要遵循避免原则和最小化原则，即能不用relative则不用，relative作用的div范围越小越好


overflow基本属性值：visible(默认)、hidden、scroll、auto、inherit

visible:大于框框的部分或超出框框，IE6浏览器则会把框框撑大
hidden：会剪辑超出框框的部分
scroll:会在容器的下边和右边出现滚动条
auto:只能判断是否超出容器，超出之后则会出现滚动条
inherit:不常用，只有IE8+的浏览器才支持

body/html与滚动条
无论什么浏览器，默认滚动条均来自<html>！而不是<body>标签
整体部分：-webkit-scrollbar
两端按钮：-webkit-scrollbar-button
外层轨道：-webkit-scrollbar-track
内层轨道：-webkit-scrollbar-track-piece
滚动滑块：-webkit-scrollbar-thumb
边角：    -webkit-scrollbar-corner


BFC (Block formatting context) 块级格式化上下文 自成小世界
overflow:auto scroll hidden 的这几个属性可以触发BFC

使用BFC可以应用以下:
1.清除浮动影响
2.避免margin穿透问题
3.两栏自适应布局

BFC（Block formatting context）-"块级格式化上下文"
页面之结界，内部元素再怎么翻云覆雨都不会影响外部。

overflow与BFC
overflow：auto/scroll/hidden都可以
overflow:visible不可以
三种常见应用：
1.清除浮动影响（IE7+等）
  overflow:hidden（元素不能全部显示），所以：
  IE7 ：.clearfix{ *zoom:1; }
  IE8+：.clearfix:after{ content:'';display:table;clear:both; }
2.避免margin穿透问题（重叠问题类似）
  overflow只是万千方法中的一个，还可以
  边框、padding、margin自适应元素BFC化。
3.两栏自适应布局
  流体自适应布局/BFC布局

absolute 会让overflow设置失效!

包含块的定义:
如果其自身没有设置relative 则会默认body为relative,有relative的为包含块

避免失效的设置
1.overflow元素自身为包含块
2.overflow元素的子元素为包含块
3.任意合法transform声明当做包含块

resize属性可以拉伸元素尺寸，不过必须要满足元素的overflow属性值不能是visible,
resize:both 水平垂直两边拉，
horizontal 只有水平方向拉
vertical   只有垂直方向拉
text-overflow:ellipsis  文本溢出用省略号表示。

a[href="#address"] 点击后 页面将滚动到 #address元素可视位置 或者 url锚链



行高的由来:

content area + vertical spacing  =  line-height
内容区域高度 + 行间距 = 行高
总结:行高决定内联盒子高度; 行间距是墙头草,可大可小(甚至负值),保证高度正好等同于行高

line-heigth: normal;
默认，不同浏览器有所差异，不同字体也有所差异。

line-heigth: <number>
根据当前元素的字体大小计算，line-height = 1.5 * 20px = 30px。

line-height: <length>
**em;**rem;**px;**pt。

line-heigth: <percent>
相对于设置该属性元素的字体大小计算，line-height = 150% * 20px = 30px。

line-height: <inherit>
行高继承，ie8+。



行高不会影响图片实际占据的高度。
为了实现基线对齐（内联元素，内联块状元素才有），是后面的文字的line-height的影响。
隐匿文本节点。好像有一个文本节点在里面。

如何消除底部间隙，
1.图片块状化（块状元素没有基线了）。没有基线对齐。
2.vertical-align:bottom；底线对齐。
3.行高足够小，line-height:0;


z-index
支持负值
支持 CSS3 animation 动画
只对定位元素 起作用 ，不支持 position:static;

如果定位元素发生嵌套，处理原则：
祖先优先原则


position:sticky是一个新的css3属性，它的表现类似position:relative和position:fixed的合体，在目标区域在屏幕中可见时，它的行为就像position:relative; 而当页面滚动超出目标区域时，它的表现就像position:fixed，它会固定在目标位置。

层叠水平是对所有的元素都有作用，而z-index仅仅对于定位元素有作用

层叠的7种等级图