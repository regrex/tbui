title: "基础设置"
date: 2015-04-21 16:28:07
order: 1 
tags:
---
##重置设置##

###[normalize.css/reset.css](https://svn.baidu.com/app/search/forum/trunk/fe/common/static/style/tbUtility)###

统一浏览器一致性，其中 Normalize.css，这是由 Nicolas Gallagher 和 Jonathan Neal 维护的一个CSS 重置样式库。
reset.css是符合贴吧业务具体需求的重置样式

###[entry](https://svn.baidu.com/app/search/forum/trunk/fe/common/static/style/tbUtility)###

*   在body上设置了**字体大小**12px, **字体**采用非衬线字体，**字体色值**为#333，**行高**22px
*   设置了基本颜色 @link-color ，并且当链接处于 :hover 状态时才添加下划线
*   `<ins>`hover状态不添加下划线

##font##

### font-size ### 

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.font-size-12(); // => font-size: 12px;
.font-size-14(); // => font-size: 14px;
.font-size-16(); // => font-size: 16px;
.font-size-20(); // => font-size: 20px;
```

### font-family ###

*   非衬线字体

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.font-family-sans-serif(); // => font-family: "Helvetica Neue", Helvetica, Arial, sans-serif; 
```

*   非衬线字体

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.font-family-serif(); // => font-family: Georgia, "Times New Roman", Times, serif;
```

*   等宽字体

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.font-family-mono(); // => font-family: Menlo, Monaco, Consolas, "Courier New", monospace;  
```

*   微软雅黑

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.font-family-yahei(); // => font-family: "microsoft yahei" simhei sans-serif;
```

### line-height ###

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.line-height-22(); // => line-height: 22px;
.line-height-26(); // => line-height: 26px;
```

### font-weight ###

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.font-weight-normal(); // => font-weight: normal; 
.font-weight-bold(); // => font-weight: bold;
```

### 链接色值设置 ###

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.a-color(@link: @link-color; @hover: @link-color; @visited: @visited-color);
```

### 链接下划线设置 ###

``` less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/font.less source 
.a-decoration(@link: none; @hover: underline);
```

##utility##

可以使用以下两种方式调用: `.class-name` 和 `.mixins(...)`

###文本色值块###

方法：添加`.class-name`类名的方式

> **注意： **为了避免被覆盖，使用！important优先级
> vip-red是超级用户经常会使用的类, 已经设置!important，不会被覆盖，请放心使用, 并且三态已经做处理

```html 示例 https://svn.baidu.com/app/search/forum/trunk/fe/common/static/style/tbUtility/utility.less source
   <p class="red-text">I am a demo ! </p>
   <p class="orange-text">I am a demo ! </p>
   <a class="vip-red" href="#">I am a demo ! </a>
```
<iframe height='141' scrolling='no' src='//codepen.io/yuanzhen/embed/waKMQo/?height=141&theme-id=13754' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/yuanzhen/pen/waKMQo/'>waKMQo</a> by yuanzhen (<a href='http://codepen.io/yuanzhen'>@yuanzhen</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

###浮动###

将元素向左或者向右浮动, **注意：**使用了!important，避免被覆盖

*   添加`.pull-left`或者`.pull-right`类 

```html 示例 https://svn.baidu.com/app/search/forum/trunk/fe/common/static/style/tbUtility/utility.less source
<span class="pull-left">float left...</span> 
<span class="pull-right">float right...</span> 
```

*   使用`.pull-left()`或者`.pull-right()`方式 

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/utility_compile.less source
.pull-left(); // => float: left
.pull-right(); // => float: right 
```

###清除浮动###

<p>通过为`父元素`添加 .clearfix 类可以很容易地清除浮动（float）。此类还可以作为 mixin 使用。</p>

*   添加`.clearfix`类

```html 示例 https://svn.baidu.com/app/search/forum/trunk/fe/common/static/style/tbUtility/utility.less source
    <div class="clearfix"></div>
```

*   通过调用`.clearfix()` mixins

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/utility_compile.less source
.clearfix(); 
```

###图片替换###

可以用来将元素的文本内容替换为一张背景图

*   添加`.hide-text`类

```html 示例 https://svn.baidu.com/app/search/forum/trunk/fe/common/static/style/tbUtility/utility.less source
    <span class="hide-text"></span>
```

*   调用`.hide-text()` mixins

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/utility_compile.less source
   .element{
       .hide-text();
   }
```

###文字省略###

设置在`dispaly: block`或者`dispaly: inline-block`且设置宽度

*   添加`.text-overflow`, 用于**单行**文字省略。 

```html 使用类名 https://svn.baidu.com/app/search/forum/trunk/fe/common/static/style/tbUtility/utility.less source
<div class="text-overflow"></div>
```

*   调用mixins `.text-overflow(...)`

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/utility_compile.less source
    .element{
        .text-overflow(); 
    }
    .element{
        .text-overflow(2); // 传入参数，仅支持webkit，表示第几行省略
    }
```

###合并icon

*   合并icon尺寸不一致，需要提供宽高信息

<!---注意：---> @my-list: demo1 20px 30px; 会生成有问题

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/utility_compile.less source
//使用如下
@my-list: demo1 20px 20px,
          demo2 20px 30px; //三个参数分别是value, width, height
.icon-sprite-multi(@my-list);

```
生成css文件

```
.icon-demo1 {
  display: inline-block;
  width: 20px;
  height: 20px;
  background: url("hfj/icon_demo1.png?__sprite");
}
.icon-demo2 {
  display: inline-block;
  width: 20px;
  height: 30px;
  background: url("hfj/icon_demo2.png?__sprite");
}
```

*   合并icon仅提供图片信息

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/utility_compile.less source
//使用如下
@my-list: "demo1", "demo2", "demo3";
.icon-sprite-single(@my-list);

```
生成css文件 
```
// .icon-demo1{background: url('images/icon_demo1.png?__sprite')}
// .icon-demo2{background: url('images/icon_demo2.png?__sprite')}
// .icon-demo3{background: url('images/icon_demo3.png?__sprite')}
```

###opacity###

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/opacity.less source
.opacity(.5)  // => opacity: .5
.background-opacity(#fff, .5) => rgba(255, 255, 255, .5)
```

###渐变###

*   从左到右横向linear渐变

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/gradient.less source
#gradient .horizontal(@star-color, @end-color, @start-percent, @end-persent);
```

*   从上到下纵向linear渐变

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/gradient.less source
#gradient .vertical(@star-color, @end-color, @start-percent, @end-persent);
```

*   径向渐变

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/gradient.less source
#gradient .directional(@deg, @start-color, @end-color);
```

###背景大小###

.background-size(@image-url, @rest...);

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/utility_compile.less source
.background-size('test.png', 50% 50%); 
```
生成css文件
```
background-image: url('test.png');
background-size: 50% 50%;
filter: progid:DXImageTransform.Microsoft.AlphaImageLoader(src='test.png', sizingMethod='scale');
```

##三角形##

常用于一些小边角

```less 示例 http://gitlab.baidu.com/tbfe/build/blob/master/fis2/less/triangle.less source
/*
* @param @direction 方向，提供 up, down, left, right四个方向
* @param @width  横向长度 
* @param @height  纵向长度 
* @param @color 色值 
*/
.triangle(@direction, @width, @height, @color);
```
<iframe height='147' scrolling='no' src='//codepen.io/yuanzhen/embed/rVOdyO/?height=147&theme-id=13754' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/yuanzhen/pen/rVOdyO/'>rVOdyO</a> by yuanzhen (<a href='http://codepen.io/yuanzhen'>@yuanzhen</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

##按钮##

###跨浏览器展现###

据bootstrap的介绍，**强烈建议尽可能使用 `<button>`元素**来获得在各个浏览器上获得相匹配的绘制效果。

同时，如果并排按钮，建议使用同类型的标签，禁止lineheight的设置，因为在不同类型的按钮中，高度获取不一致

###作为按钮的元素###

为 `<a>`、`<button>`、`<input type="submit">`、`<input type="button">`或 `<input type="reset">`元素添加按钮类（button class）即可使用 基础库 提供的样式。

###预定义样式###
在预定义样式中，
提供了**四种样式**类: `.btn-default`、`.btn-attention`、`.btn-sub`、`.btn-disable`
提供了**三种尺寸**类: `.btn-small`、`.btn-middle`、`.btn-larger`
这四种样式和尺寸可以随意搭配使用。

<iframe height='268' scrolling='no' src='//codepen.io/yuanzhen/embed/YPMaar/?height=268&theme-id=13754' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/yuanzhen/pen/YPMaar/'>YPMaar</a> by yuanzhen (<a href='http://codepen.io/yuanzhen'>@yuanzhen</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

样式默认设置
```
<button class="btn-default btn-small" >常用蓝色(.btn-default)</button>
<button class="btn-attention btn-small" >关注(.btn-attention)</button>
<button class="btn-sub btn-small" >副按钮(.btn-sub)</button>
<button class="btn-disable btn-small" >不可用按钮(.btn-disable)</button>
```

尺寸默认设置
```
<button class="btn-default btn-small" >常用尺寸(.btn-small)</button> 
<button class="btn-default btn-middle" >中按钮(.btn-middle)</button> 
<button class="btn-default btn-larger" >大按钮(.btn-larger)</button> 
```

### 自定义按钮 ###

自定义按钮提供了以下两种样式mixins

```
//纯色背景
.btn-variant(@color, @bg-color, @border-color, @hover-color, @hover-bg-color, @hover-border-color){
}

//渐变背景
.btn-styles(@color: #fff, @btn-color: #555) {
}

//@padding-vertical: btn上下间距 
//@padding-horizontal: btn横向间距 
//@line-height: btn字体大小
//@font-size: btn字体大小
//@border-radius: btn圆角
.btn-size(@padding-vertical, @padding-horizontal, @line-height, @font-size, @border-radius) {
}

```

<iframe height='239' scrolling='no' src='//codepen.io/yuanzhen/embed/RNmjyZ/?height=239&theme-id=13754' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/yuanzhen/pen/RNmjyZ/'>RNmjyZ</a> by yuanzhen (<a href='http://codepen.io/yuanzhen'>@yuanzhen</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>


自定义按钮是以btn为基础，

*   如果和预定义样式中的4类样式不一致，建议使用.btn-variant(...)或者.btn-styles(...)进行设置;
> 如果使用自定义样式，请不要再添加.btn_default, .btn_sub等预定义样式

*   如果和预定义样式中的3类尺寸不一致，建议使用.btn-size(...)进行设置;
> 如果使用自定义尺寸，请不要再添加.btn_small, .btn_middle等预定义尺寸

```
    <element class="btn element"></element>
    .element{
        .btn-variant(...); //or btn-styles(); 设置背景颜色，文字颜色或者border色值，参数请看下面的mixins 
        .btn-size(...); //设置盒模型大小和字体大小, 参数请看下面的mixins
    }

```

### 带icon的按钮 ###

使用`<i class="icon-*"></i>`表示icon, 样式由用户自己定义，可以使用sprite图片，同时可以使用iconfont(暂时没有)

> **注意：** 
> 尽量使icon的尺寸和文字的尺寸保持一致，例如文字是14px，那么icon也设置为14px; 
> 使用vertical-align: middle 和 [margin-top: -.1em](http://snook.ca/archives/html_and_css/icons-and-type); 使icon居中对齐

```
<button class="btn-sub btn-small"><i class="icon-attention"></i>关注</button>
<button class="btn-attention btn-small"><i class="icon-attention"></i>关注</button>

.icon-attention{
    display: inline-block;
    width: 12px;
    height: 12px;
    vertical-align: middle;
    margin-top: -.1em;
}

```
