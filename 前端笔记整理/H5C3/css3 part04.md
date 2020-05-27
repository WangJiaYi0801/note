- 1. 1.携程网页面

  2. 1. 页面结构分析,画图

     2. 代码实现--结构

     3. 1. header >         a > img
        2. main >         section > left         + ( right > a*4 ) /        section > a >img
        3. footer >         ( nav > a*3 ) + ( p        > a*3 ) + p

     4. 代码实现--样式

     5. 1. 使用 flex : 1 ; 设置盒子的占比

     6.  ![a](/Users/jiayiwang/Downloads/a.png)

-  

- 1. 2.切割轮播图

  2. 1. 5个立方体依次旋转,每个立方体4个面
     2. 保留3D效果,需要给父元素设置,transfrom-style
     3. 通过background-position设置图片背景位置,拼接成一张图片
     4. 点击事件：添加图片索引，设置节流阀,each遍历5个立方体,设置延迟转动90度

-  

- 1. 3.全屏滚动插件

  2. 1. 步骤:

     2. 1. 引入文件(js+css)
        2. 写入结构
        3. 调用方法

     3. 在切换屏之后,再给元素添加样式,交集选择器

     4. 图片间距较大是由于基线对齐,解决方法:

     5. 1. font-size:0;
        2. display:block;
        3. 设置底线对齐

     6. 定位参照浏览器中心点,top:50%;left:50%;用transform:translate进行移动自身宽高的50%;

-  