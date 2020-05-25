- 1. 1.ES5中数组操作方法------数组.方法名(function(item,index){ })

  2. 1. forEach 等价于 for ,循环数组

     2. map 映射

     3. 1. var arrMap        = arr.map(function(item,index){return item*2})

     4. filter 过滤 返回符合条件的项

     5. 1. var        arrFilter=arr.fliter(function(item,index){return item > 50})

     6. every 每一个 返回true/false 每一项都满足条件为真,有一项不满足为假

     7. 1. var        flagEvery=arr.every(function(item,index){return item >50})

     8. some 一些 返回true/false        只要有一项满足条件就为真,全部满足为假

-  

- 1. 2.绘制形状

  2. 1. 矩形: 

     2. 1. ctx.rect(x,y,width,height);  
        2. ctx.strokeRect(x,y,width,height);
        3. ctx.fillRect(x,y,width,height);
        4. ctx.clearRect(x,y,width,height);

     3. 清除整个画布

     4. 1. ctx.clearRect(0,0,cas.width,cas.height)
        2. cas.width=cas.width;当改变cas的属性时,内容会刷新

     5. 圆弧

     6. 1. ctx.arc(x,y,r,startAngle,endAngle,clockwise)

        2. 1. x,y-----圆心坐标
           2. r--------圆的半径
           3. startAngle,endAngle开始弧度,结束弧度
           4. 弧度制:将360度记为2*Math.PI

        3. ctx.arcTo( )

        4. 绘制圆弧与起始点的位置问题:

        5. 1. 使用开启新路径:         beginPath
           2. 设置起点,ctx.moveTo(x +         100 + r * Math.cos(angle),y+r * Math.sin(angle))

     7. 扇形

-  

-  