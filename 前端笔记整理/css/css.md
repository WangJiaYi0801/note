css

[toc]
## 常用样式

字体设置
font: font-style  font-weight  font-size/line-height  font-family;

color:文本颜色

line-height:行间距

text-align:水平对齐方式 left / right / center

text-indent:首行缩进

letter-spacing:字间距

word-spacing:单词间距

color: rgba(r,g,b,a)颜色半透明 a取0-1

text-shadow:水平位置 垂直位置 模糊距离 阴影颜色 (文字阴影)

**标签显示模式（display）**

块级元素 block `<h1>~<h6>、<p>、<div>、<ul>、<li>`

行内元素 inline `<a>、、<em>、<i>、<del>、<span>`

行内块元素 inline-block `<img />、<input />、<td>`

标签显示模式转换 display:block

背景(background)
background:背景颜色 背景图片地址 背景平铺 背景滚动

背景位置
`background: transparent url(image.jpg) repeat-y  scroll 50% 0 ;`

背景透明
`background: rgba(0,0,0,0.3);`

背景缩放
`background-size:百分比/cover/contain`

文本的装饰`text-decoration:underline`下划线

盒子模型

盒子边框`border : border-width || border-style || border-color`border-style:solid：边框为单实线

上边框	border-top-style:样式;
border-top-width:宽度;border-top-color:颜色;border-top:宽度 样式 颜色;

圆角边框`border-radius: 左上角  右上角  右下角  左下角;`

内边距（padding）padding-top

外边距（margin）

```
text-align: center; /*  文字居中水平 */
margin: 10px auto;  /* 盒子水平居中  左右margin 改为 auto */
```

外边距合并问题:

上下垂直外边距合并,塌陷

嵌套垂直外边距合并,父元素添加overflow:hidden

css3盒模型

box-sizing: content-box/border-box(padding和border算进width里)

盒子阴影`box-shadow:水平阴影 垂直阴影 模糊距离 阴影尺寸 阴影颜色  内/外阴影`


## **选择器**

标签选择器  p{}

类选择器    .classname{}

id选择器    #id{}

通配符      *{}  (用于开头清除样式)

交集选择器  p.one{}

并集选择器  .one,p,#id{}

后代选择器  ul li {}

子元素选择器 .demo > li {}

属性选择器 


## 伪类选择器

链接伪类选择器

:link / 未访问的链接 /

:visited / 已访问的链接 /

:hover / 鼠标移动到链接上 /

:active / 选定的链接 /

结构(位置)伪类选择器

:first-child :选取属于其父元素的首个子元素的指定选择器

:last-child :选取属于其父元素的最后一个子元素的指定选择器

:nth-child(n) ： 匹配属于其父元素的第 N 个子元素，不论元素的类型

:nth-last-child(n) ：选择器匹配属于其元素的第 N 个子元素的每个元素，不论元素的类型，从最后一个子元素开始计数。 n 可以是数字、关键词或公式

目标伪类选择器

:target目标伪类选择器 :选择器可用于选取当前活动的目标元素

**伪元素选择器**

E::first-letter文本的第一个单词或字（如中文、日文、韩文等）

E::first-line 文本第一行；

E::selection 可改变选中文本的样式；

E::before和E::after

在E元素内部的开始位置和结束位创建一个元素，该元素为行内元素，且必须要结合content属性使用。







