- 1. 背景样式

  2. 1. 添加背景颜色       background-color:skyblue;

     2. 添加背景图片 background-image

     3. 1. 图片大于容器,默认左上角放置
        2. 图片小于容器,图片默认平铺

     4. 设置图片平铺 no-repeat /       repeat-x background-repeat

     5. 1. round : 会将图片进行缩放之后再平铺
        2. space : 会在图片之间产生间距进行平铺

     6. 设置在滚动容器的背景的行为: background-attachment

     7. 1. fixed : 滚动窗口的滚动条,图片固定不动

        2. scroll : 滚动窗口的滚动条,图片会随着滚动条滚动

        3. local:滚动内容的滚动条: 背景图片会跟随内容一起滚动

        4. scroll: 滚动内容的滚动条: 背景图片不会跟随内容一起滚动

        5. 应用:

        6. 1. 视差滚动: 必须有一个背景图,设置fixed,图片不会动,图片后面的图片会把随进度条滚动把背景图覆盖

     8. 设置背景图片大小 background-size

     9. 1. 宽度/高度 宽度/auto(保持比例自动缩放) 

        2. 百分比 , 是参照父容器可放置内容区域的百分比

        3. 设置contain : 按比例调整图片大小,使图片宽高自适应整个元素的背景区域,使图片全部包含在容器内,维持宽高比例

        4. 1. 图片大于容器: 等比缩小,可能造成空白区域
           2. 图片小于容器: 等比放大,可能造成空白区域

        5. cover: 背景图片等比缩放,自适应整个背景区域,多余部分溢出

        6. 1. 图片大于容器: 等比缩小,完全填满容器,多余部分溢出
           2. 图片小于容器: 等比放大,完全填满容器,多余部分溢出

     10. 设置背景坐标的原点 background-origin

     11. 1. border-box: 从border的位置开始填充,会与border重叠
         2. padding-box: 从padding的位置开始填充,会与padding重叠
         3. content-box: 从content的位置开始填充,会与content重叠

     12. 设置内容的裁切 background-clip

     13. 1. border-box: 显示border及以内的内容
         2. padding-box: 显示padding及以内的内容
         3. content-box: 显示content及以内的内容

-  

- 1. 综合写法:

  2. 1. background:       url(../images/a.jpg) no-repeat center center / 20px 30px;

-  

- 1. 2.过渡

  2. 1. 添加过渡效果:过渡效果执行完毕之后,默认会还原到原始状态

     2. 1. transition-property:        添加过渡效果的样式属性名称
        2. transition-duration:        过渡效果的耗时,秒数
        3. transition-timing-function:设置时间函数--控制运动的速度
        4. transition-delay: 过渡效果的延迟
        5. 简写: transition: 属性名称 过渡时间 时间函数 延迟时间

     3. 为多个样式同时添加过渡效果 , 逗号分隔

     4. 1. transition:        left 2s linear 0s , background-color 5s         linear 0s;

     5. 所有样式添加过渡效果(效率低下)

     6. 1. transition:        all 2s linear 0s;

     7. steps(4): 让过渡效果分为指定的几次来完成

     8. 1. 例: 时钟效果
        2. 兼容性: IE10 以上支持,其他加前缀
        3. 速度与步伐不能共存,有冲突

     9. 要求: 过渡的属性必须要有具体的值,如display就不能添加过渡效果

-  

- 1. 3.2D 转换

  2. 1. 2D移动 : transform : translate(20px);

     2. 1. 移动参照元素本身; 执行完毕后会恢复原始位置
        2. 一个参数表示x方向,两个参数表示xy方向
        3. 单一方向移动:translateY;

     3. 2D缩放 : transform : scale(2)        取值为倍数,0-1缩小,大于1放大

     4. 1. 一个参数,x和y方向都进行等比例缩放 ; 两个参数 即 x 和 y
        2. 缩放时不影响其他元素,参照自己的中心点
        3. 单方向缩放: scaleX ; scaleY

     5. 2D旋转 : transform : rotate(30deg) 正值顺时针;负值逆时针

     6. 2D斜切 : transform :       skew(30deg) 正值往当前轴负方向斜切

     7. 1. 一个参数延X轴切,两个参数X 和Y
        2. 单方向斜切 : skewY

     8. 轴心点: transform-origin : 0 0 ;

     9. 1. 设置值 x,y
        2. 还可以是关键字,top bottom left        right

     10. 添加多个属性 transform :       translate(20px) rotate(30deg)

     11. 1. 要先移动,再旋转 --旋转会旋转坐标系,效果不同

     12. 清除transform值 : transform : none;

     13. transform       经典应用---实现任意元素居中

     14. 1. 先定位top : 50% ;  left : 50% ;
         2. 然后使用transform : translate(-50%,-50%) ;        -->参数为百分比时,以自身为参照

-  

- 1. 4.3D转换---参数必须为三个: x轴偏移,y轴偏移,z轴偏移

  2. 1. 3D移动 : transform :       translate3d ( x , y , z );
     2. 3D缩放 : transform :       scale3d ( x , y , z );
     3. 3D旋转 : transform :       rotate3d ( x , y , z ,angle);