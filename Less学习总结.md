# Less入门总结

因为Indigo主题使用的是 Less，所以自己有必要学习一下

## 1. 安装

```bash
npm install -g less（安装node之后）
```

**将 .less 文件编译成纯 CSS 文件，像下面这样：**
```bash
lessc styles.less > styles.css
```

***

## 2. 变量
> 支持运算
```css
@background-color: #ffffff;

p{
  background-color: @background-color;
}
span{
  background-color: @background-color -100 ;
}
```
***

## 3. Mixins

```css

#circle{
  background-color: #4CAF50;
  border-radius: 100%;
}

#small-circle{
  height: 50px;
  #circle
}
```
*最后将被解析为：*
```css
#circle {
    background-color: #4CAF50;
    border-radius: 100%;
}

#small-circle {
    height: 50px;
    background-color: #4CAF50;
    border-radius: 100%;
}
```

**如果不想出现circle规则 即写成 \#circle() 即可**

***

## 4. 默认传入参数
```css
#circle(@size: 25px){
    background-color: #4CAF50;
    border-radius: 100%;

    width: @size;
    height: @size;
}

#small-circle{
    #circle
}

#big-circle{
    #circle(100px)
}
```
转换成 CSS :

```css
#small-circle {
    background-color: #4CAF50;
    border-radius: 100%;
    width: 25px;
    height: 25px;
}
#big-circle {
    background-color: #4CAF50;
    border-radius: 100%;
    width: 100px;
    height: 100px;
}
```

***

## 5. 嵌套
```css
ul{
    background-color: #03A9F4;
    padding: 10px;
    list-style: none;

    li{
        background-color: #fff;
        border-radius: 3px;
        margin: 10px 0;
    }
}
```
*编译成css*
```css
ul {
    background-color: #03A9F4;
    padding: 10px;
    list-style: none;
}
ul li {
    background-color: #fff;
    border-radius: 3px;
    margin: 10px 0;
}
```

**作用域**
```css

@text-color: #000000;

ul{
    @text-color: #fff;
    background-color: #03A9F4;
    padding: 10px;
    list-style: none;

    li{
        color: @text-color;
        border-radius: 3px;
        margin: 10px 0;
    }
}
```
*编译生成的 CSS 代码如下：*
```css

ul {
    background-color: #03A9F4;
    padding: 10px;
    list-style: none;
}
ul li {
    color: #ffffff;
    border-radius: 3px;
    margin: 10px 0;
}
```

***

## 6. &的运用
```css
@var: #004590;

div{
  height: 50px;
  width: 50px;
  background-color: @var;

  &:hover{
    background-color: fadeout(@var, 50%)
  }
}
```

*编译成 CSS 如下所示：*
```css
div {
    height: 50px;
    width: 50px;
    background-color: #004590;
}
div:hover {
    background-color: rgba(0, 69, 144, 0.5);
}
```

***

## 7.other


.hiddenMixin() {
  color: black;
}
p {
  .hiddenMixin()
}
将会输出这样的结果：

p {
  color: black;
}


守卫

另外一种制约多个 mixin 同时使用的方法是使用 guards。
它是一个特殊的表达式，和 mixin 的申明联合起来使用。
他必须在 mixin 使用之前是真实的。 
当你想匹配表达式的时候，使用 gurads 往往是有用的。

在开始使用 guards 的时候， 我们是从 when 这个关键词开始的:

.mixin (@a) when (lightness(@a) >= 50%) {   
  background-color: black;
}

.mixin (@a) when (lightness(@a) < 50%) {
  background-color: white;
}

.mixin (@a) { // this is always included
  color: @a;
}

.class1 {
  .mixin(#ddd);
} // this matches the first mixin

.class2 {
  .mixin(#555);
} // this matches the second mixin
我们将会得到这样的结果:

.class1 {
  background-color: black;
  color: #ddd;
}

.class2 {
  background-color: white;
  color: #555;
}
在 guards 中支持的操作符有 >, >=, =, 等