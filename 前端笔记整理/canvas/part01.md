- 1. 1.基本使用:

  2. 1. 提供canvas标签即可,默认会占据300*150的区域
     2. 利用html属性为他设置宽高,不要使用css来设置,使用属性设置canvas标签的宽高,实际上相当于增加了canvas画布的像素,但是如果使用css来设置画布的大小,那么不会增加像素点,只是将像素扩大了
     3. canvas只能展示绘图的内容,但是不能进行绘图.利用canvas找到绘图工具,每个canvas都有一套工具,利用工具可以在当前canvas上进行绘图.使用语法: canvas.getContext('2d')就返回一套在当前画布上绘图的工具集.这个工具集专门绘制 平面图形,如果要绘制立体的图形需要传入 'webgl'.
     4. 开始绘图:首先需要绘制点,然后需要将这些点描边,才可以看到东西

-  

- 1. 绘图常用方法:

  2. 1. ctx.moveTo(x,y)       将绘图的起始点设置为x,y
     2. ctx.lineTo(x,y)   从当前位置,绘制直线到x,y
     3. ctx.stroke(       )     将刚刚绘制的所有的点联系起来,就可以看到图形了

-  

- 1. 绘制方法

  2. 1. ctx.stroke( )
     2. ctx.fill(       )---------调用fill方法会将所有的点连接起来,并构成一个封闭的图形结构,如果所有的描点没有构成封闭结构,也会将开始的起点,与最后的点连接起来,构成闭合图形,填充颜色

-  

- 1. 非零环绕原则:

  2. 1. 如果需要判断某个区域是否需要填充颜色,就从该区域中随机的选取一个点,从这个点拉一条直线出来,一定要拉到图形的外面,辞职以该点为原型,看穿过拉出的直线的线段,如果是顺时针方向就记为 +1,逆时针 -1,最终看求和的结果,如果是0就填充,不是0 ,则填充

-  

- 1. 闭合路径

  2. 1. closePath(       )方法
     2. lineWidth       设置绘制线宽

-  

- 1. canvas中绘图是有状态的

  2. 1. 在需要改变颜色,绘制方法,改变一些属性....就会改变绘画状态,使用beginPath(       )方法

-  

- 1. 绘制虚线

  2. 1. ctx.setLineDash([5,5])

     2. 1. 数组中的数字,表示实线部分和空白部分长度

     3. ctx.getLineDash( )

     4. ctx.lineDashOffset       = 值

-  

- 1. 设置描边和填充的颜色

  2. 1. ctx.strokeStyle 设置描边的颜色
     2. ctx.fillStyle     设置填充的颜色

-  