- 1. 1.绘制文本(参考点在文字左下角)

  2. 1. ctx.fillText('hello       canvas',100,100);

     2. ctx.strokeText('hello       canvas',100,100);

     3. 常见属性:

     4. 1. ctx.font =        '30px Consolas'
        2. ctx.textAlign ---         left/right/center         start/end 水平对齐
        3. ctx.textBaseline ---top,middle,bottom hanging,ideographics,alphabetic 垂直对齐方式
        4. ctx.measureText('文本'),获取文本对象,ctx.measureText('        ').width 获取宽度

-  

- 1. 绘制图片

  2. 1. ctx.drawImage( )有三种调用形式

     2. 1. ctx.drawImage(img,x,y)
        2. ctx.drawImage(img,x,y,width,height)
        3. ctx.drawImage(img,sx,sy,swidth,sheight,x,y,width,height)

     3. 步骤:

     4. 1. 创建图片对象,其实就是img标签 : new Image( )

        2. 1. var img = new Image( );
           2. img.src = ' ';

        3. 确定要绘制的位置

        4. 1. var x          = 100, y =          100;

        5. 开始绘制:(需要等待图片加载完毕后再执行)

        6. 1. 使用onload事件
           2. ctx.drawImage(img,x,y);

-  

- 1. 变换

  2. 1. ctx.trandform(x,y) 平移变换

     2. ctx.scale(x,y) 缩放变换

     3. ctx.translate()

     4. ctx.rotate(radian) 旋转变换--弧度

     5. setTransForm()

     6. 环境

     7. 1. 使用ctx.save( )方式保存当前状态
        2. 如果需要恢复到已经保存的状态,只需要调用ctx.restore( )
        3. 状态保存的机制是基于状态栈实现的,也就是说save()一次就存储一个状态,restore一次就将刚刚存入的恢复,如果save两次,就需要restore两次,才可以恢复到最先的状态
        4. 一般在封装绘图的时候都会采用开始绘制之前, save 一次, 然后 开启一个新路径, 然后绘制结束后 restore, 然后再开启一个新路径. 这样保持当前状态不会对其他绘图代码构成影响

     8. 优化

     9. 1. canvas 在绘制图片的时候, drawImage 方法还支持将一个 canvas 绘制到另一个 canvas 中. 因此使用该功能, 可以在内存中完成复杂的绘图, 将绘制好的半成品再绘制到 canvas 中合成需要的效果

     10. 画布保存

     11. 1. ctx.ToDataURL(        type,encoderOptions)

     12. 1. 该方法可以将画布转换成 base64 格式的数据
         2. type 表示输出类型. 例如: image/png 或 image/jpeg 等
         3. encoderOptions 表示图片输出质量, 其取值在 0 到 1 之间. 如果是 1, 表示无损压缩, 必须使用 image/jpeg 或 image/webp 才起作用

     13. 渐变和图案

     14. 1. ctx.createLinearGradient(x0,y0,x1,y1)        线性渐变

         2. 1. 参数表示线型渐变的方向与位置
            2. 使用时先创建对象,然后利用addColorStop(rate,color)设置颜色
            3. 然后将给对象赋值给*Style属性即可

- var canvasGradient = ctx.createLinearGradient( 0, 25, 200, 25 );
      canvasGradient.addColorStop( 0, 'blue' );
      canvasGradient.addColorStop( 1, 'red' );
      ctx.fillStyle = canvasGradient;

- ctx.fillRect( 0, 100, 200, 50 );

-  

- 1. ctx.createRadialGradient(x0,y0,r0,x1,y1,r1)  放射渐变
  2. ctx.createPattern(img,repetition) 重复填充
  3. 阴影(少用,性能不高)

-  

-  

-  