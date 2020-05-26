1. 1.轮播图的滑动轮播

2. 1. 用touchstart和touchend判断滑动方向
   2. 然后添加监听事件,调用左右切换按钮的方法

3. 信息块

4. 产品块

5. 1. 导航

   2. 1. 引用bootstrap的js组件

      2. 尽量不修改父容器高度,用子元素撑开父盒子,可用行高或者padding

      3. 导航滑动:

      4. 1. 要计算导航项的原始宽度

         2. 1. 获取宽度时,width(         ) 方法不能获取到padding的值
            2. 使用innerWidth( ),他可以取到加上padding的宽度值
            3. outerWidth( ),可以取到加上padding和border的宽度
            4. outerWidth( ture         ),可以取到加上padding和margin和border的宽度

         3. 使用插件实现滑动

   3. 内容面板

   4. 1. 宽屏放三个,缩小一点放两个,小屏放一个,使用栅格系统进行布局

 ![111](/Users/jiayiwang/Downloads/111.png)

 

 