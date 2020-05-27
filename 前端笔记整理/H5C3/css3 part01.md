- 1. 1.选择器

  2. 1. 属性选择器:根据指定名称的属性的值来查找元素

     2. 1. E[attr] 查找指定的拥有attr属性的E标签
        2. E[attr=value]   查找拥有attr属性,并且值只为value的E标签, = 是严格匹配
        3. E[attr*=value]  查找拥有attr属性,并且值中包含value的E标签
        4. E[attr^=value]  查找拥有attr属性,并且值以value开头的E标签
        5. E[attr$=value]  查找拥有attr属性,并且值以value结尾的E标签

-  

- 1. 伪类选择器

  2. 1. a:hover   a:link   a:

     2. 结构伪类

     3. 1. 兄弟伪类: + :获取当前元素的相邻的相同标签的元素

- ~ :获取当前元素的所有有相同标签的元素

- 1. 相对于父元素的结构伪类

  2. 1. E:first-child 查找E元素的父级元素中的第一个元素,如果是E元素,则找到
     2. E:last-child 最后一个元素
     3. E:first-of-type       限制类型,只查找E元素
     4. E:last-of-type
     5. E:nth-child(从1开始的索引/关键字/表达式):

- li:nth-child(4) / li:nth-child(even/odd) /

- li:nth-child(-n+5) n小于等于0时就无效 nth-last-child 从后往前数

- 1. E:nth-of-type      限制类型

- 1. 空值:没有任何内容,连空格都没有 E:empty
  2. E:target 可以为锚点目标元素添加样式,当目标元素被触发时,调用样式

- 1. 伪元素选择器

  2. 1. E:before /       E:after 或者 E::before / E::after

     2. 1. 是行内元素 
        2. 必须添加content : "        " ,没有内容也要添加
        3. 功能完全等价于一个dom元素,但是不在dom树中
        4.  ![001](/Users/jiayiwang/Downloads/001.png)

     3. E::first-letter 取第一个字母或者第一个文字

     4. 1. E::first-line 取第一行
        2. E::selection 设置当前选中内容的样式,不能设置大小

-  

- 1. 2.颜色设置

  2. 1. RGBA

     2. 1. rgb(0,255,0) 红黄绿青蓝紫 6位十六进制数
        2. opacity:0.2 将整个盒子变透明,包括里面的内容
        3. rgba(0,255,0,0.2) 将盒子变透明,内容不变,即不具有继承性
        4. transparent 不可调节透明度,完全透明

     3. HSL

-  

- 1. 3.阴影shadow

  2. 1. text-shadow : offsetX offsetY blur        color

     2. 1. length 长度值,指向阴影的延伸距离 offsetX offsetY
        2. blur 羽化/模糊值,不能为负,用来指定模糊效果的作用距离
        3. color  指定阴影颜色,可以使用rgba透明色
        4. 多层阴影:text-shadow : offsetX offsetY blur         color , text-shadow : offsetX offsetY blur         color

- 逗号分割,可加多层阴影 

- 1. box-shadow :       h v blur       spread color inset

  2. 1. h 水平方向的偏移值
     2. v 垂直方向的偏移值
     3. blur 模糊--可选
     4. spread 阴影尺寸,扩展和收缩阴影的大小--可选
     5. color 颜色--可选--默认黑色
     6. inset 内阴影--可选

-  

- 1. 4.盒模型

  2. 1. box-sizing       指定盒模型的计算大小的方式
     2. content-box 内容的大小为盒子大小
     3. border-box  表框border+内间距padding+内容content=盒子大小

-  

- 1. 5.边框圆角

  2. 1. border-radius 先上下后左右
     2. 左上角:       border-top-left-radius

-  

- 1. 6.渐变

  2. 1. linear-gradient 线性渐变:指沿着某条直线朝一个方向产生渐变效果

     2. 1. 语法:

- linear-gradient(方向 , 开始颜色 , 结束颜色)

- linear-gradient(方向 , 颜色1 位置 , 颜色2 位置...)

- 1. 方向: 可用方向词或角度

- to top : 0deg

- to right : 90deg

- to bottom : 180deg--默认

- to left : 270deg

- 1. 位置 : 可用百分比

- 1. radial-gradient 径向渐变: 

  2. 1. 语法:radial-gradient(形状 大小 at坐标 , 颜色1 位置 , 颜色2 位置...)
     2. 形状:shape

- circle : 产生正方形的渐变色

- ellipse : 适配当前的形状,如果是正方形,效果相同--默认

- 1. 坐标:position

- 可以赋值坐标,也可以赋值px

- at left top / at 50px 50px

- 1. 大小:size

- closest-side: 最近边

- farthest-side: 最远边

- closest-corner: 最近角

- farthest-corner: 最远角--默认

- 1. repeating-radial-gradient       重复渐变:

- repeating-linear-gradient(circle closest-side at center center,#fff 0%,#fff 10%,#000 10%,#000 20%);