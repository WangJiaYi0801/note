- 1. 1.立方体:

  2. 1. transform-style       : preserve-3d ; 使元素保留3d转换的效果(需要设置在父元素中)
     2. 景深效果

-  

- 1. 2.动画 -- 关键帧动画

  2. 1. 添加动画的步骤:

     2. 1. 创建动画:

        2. 1. @keyframes: moveName {

- 0%{ }               from

- 50%{ }      或   

- 100%{ }             to

- }

- 1. 考虑兼容性,加前缀

- 1. 将动画添加到指定元素上

  2. 1. animation-name:       moveName ; 动画名:
     2. animation-duration       : 2s ; 总耗时 
     3. animation-iteration-count:       infinete ; 设置动画播放次数,可为数字次数以及infinete无限次
     4. animation-direction:       alternate ;设置交替动画
     5. animation-delay: 2s       ; 设置动画延迟时间
     6. animation-fill-mode:       forwards(保留动画结束时的状态) / backwards(不保留状态,有延迟时,直接进行初始状态)  /both(两者兼有) ; 设置动画结束时的状态,默认结束后回到原来的状态
     7. animation-timing-function       : ease / linear ; 时间函数
     8. animation-play-state:       paused / running ; 设置动画播放状态
     9. animation       : 动画名 动画时间 延迟时间 动画速度 次数(infinite) forwards ;

-  

- 1. 3.多列布局

  2. 1. 常用属性:

     2. 1. column-count: 3 ; 设置列数
        2. column-width:        500px ; 设置列宽(列数和列宽计算取更大列宽)
        3. column-gap:50px ; 设置列间隙大小
        4. column-rule:        dashed 3px red ; 设置列间隙样式,与边框样式的添加一样
        5. column-span: all ;        设置跨列显示(取 1 或者 all )

-  

- 1. 4.伸缩布局

  2. 1. display:       flex ; 设置父容器为伸缩盒子,会使每个子元素自动变成伸缩项(flex item)

     2. justify-content:设置或检索弹性盒子元素在主轴(横轴)方向上的对齐方式

     3. 1. flex-start--第一个元素左对齐,后续元素向他对齐

        2. 1.  ![1](/Users/jiayiwang/Downloads/1.png)

        3. flex-end--第一个元素右对齐,后续元素向他对齐

        4. 1.  ![2](/Users/jiayiwang/Downloads/2.png)

        5. center--子元素相互对齐在行内居中对齐,最左,最右边距相等

        6. 1.  ![3](/Users/jiayiwang/Downloads/3.png)

        7. space-between--左右两边对齐边线,中间均匀分布

        8. 1.  ![4](/Users/jiayiwang/Downloads/4.png)

        9. space-around--左右保留子元素间距的一半,中间均匀分布

        10. 1.  ![5](/Users/jiayiwang/Downloads/5.png)

     4. flex-flow: 是flex-wrap和flex-direction的综合

     5. 1. flex-wrap: 控制子元素是否换行显示,默认不换行

        2. 1. nowrap:         不换行
           2. wrap: 换行
           3. wrap-reverse:翻转,从上到下,翻转后就是从下到上来排序

        3. flex-direction:设置主轴方向,默认为水平row

        4. 1. row: 水平是主轴
           2. row-reverse: 水平主轴,从右到左
           3. column: 垂直是主轴
           4. column-reverse: 垂直是主轴,从下到上

     6. flex: 是flex-grow,flex-shrink和flex-basis的综合,默认 0 1 auto

     7. 1. flex-grow: 1 ;可以扩展子元素的宽度,占据空白的空间的比例值,写在子元素中

        2. 1. 比例值计算: (当前元素的值/所有子元素的值) *          空白空间的大小

        3. flex-shrink: 定义收缩比例,通过设置的值来计算收缩的空间

        4. flex: [number];给子元素设置比例 

     8. align-items: 设置子元素在侧轴上的对齐方式

     9. 1. center /         flex-start / flex-end  / space-between /space-around

- align-self: center /  flex-start / flex-end  ; 给子元素设置侧轴位置,作用于自己一个

- 1. stretch: 拉伸,让子元素在侧轴方向上进行拉伸,是默认值
  2. baseline: 基线对齐
  3. align-items:      center / flex-start /       flex-end ; 给父元素设置子元素的侧轴位置,作用于所有子元素







- ## ![重要](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAAXNSR0IArs4c6QAAAHhlWElmTU0AKgAAAAgABAEaAAUAAAABAAAAPgEbAAUAAAABAAAARgEoAAMAAAABAAIAAIdpAAQAAAABAAAATgAAAAAAAABgAAAAAQAAAGAAAAABAAOgAQADAAAAAQABAACgAgAEAAAAAQAAABCgAwAEAAAAAQAAABAAAAAA6IepAgAAAAlwSFlzAAAOxAAADsQBlSsOGwAAAUdJREFUOBGNU0tOwzAQnbhIXZYIWFNuECjscwO4AeEG3UZsygLlGs0NygmANb9wA/Z80ixZxOGNZQfbSQOWohnPe29mNOMQDZyP7Cjhb4BCYggElgQUzIc4wSawvD6JpJAvjAspDsPLh6KPu7EDiNvKtu8nCd6z49gP8l1Qs4KZaKySFJxp3zFbICaInDvR7mUC3m03TLmawWc2WwL8K4mvz3fSp0TNgB2guc8YuL+K71rNyNnCPzthcRwuijUXcBJw4CubrRqiU/Z7jiNmvLNGiFXmHjE11KxNZYM7HZSLaFuOR28AzfoMr7WC6oMwLZijjtNBPRa8a19caa4ykkZqeCbmJBDWY0G791wNX4Q2b4wANrH83yHq9kuAFcTz3fR5aRP5xeIxcWwf+IXB2w50+zlWNDWgnWAvfbzDe5licVf4Q2OD/QAk/mtExMcVswAAAABJRU5ErkJggg==) 属性总结:

- | @keyframes      | 创建动画         | @keyframes: moveName{   0%{ }        from{ }   50%{ }   或   100%{ }      to{ }   } |
  | --------------- | ---------------- | ------------------------------------------------------------ |
  | animation       | 添加动画         | animation:  name duration  timing-function  delay   iteration-count       direction          fill-mode      play-state;          动画名    总耗时    时间函数      延迟时间      播放次数          方向             元素样式     运行状态                 2s    linear 匀速         2s       n  次              normal 默认        none 默认      running 运行中                       ease 慢快慢(默认)           infinite 无限次     reverse 反向播放    forwards     paused 暂停                                                                  alternate 奇正偶反  backwards   forwards : 动画结束后,保留最后状态   backwards : 在有延迟时,直接应用from中的开始属性值 |
  |                 |                  | display : flex ; 设置父元素为伸缩盒子,子元素均自动变为伸缩项 ( flex items ) |
  | justify-content | 设置排列方式     | justify-content : flex-start 默认值,项目位于容器的开头                 flex-end  项目位于容器的结尾                 center   项目位于容器的中心                 space-between 左右对齐边线,中间均匀分布,留有空白                 space-around   左右留白为中间留白的一半 |
  | flex-flow       | 设置排列方式     | flex-flow : flex-direction       flex-wrap ;  默认 row nowrap     设置主轴方向                   设置是否换行      row    水平                       nowrap 不换行      row-reverse从右到左            wrap    换行      column    垂直                   wrap-reverse      column-reverse从下到上 |
  | flex            | 设置空间分配方法 | flex : flex-grow          flex-shrink           flex-basis ;  默认 1 1 auto    设置项目扩展的量          设置项目收缩的量     设置项目初始长度    number                 number             auto /    % / px    / em 或其他长度单位的数字    比例值 = n1/(n1+n2+…)    按比例值分配剩余空白区 |
  | align-items     | 设置侧轴对齐方式 | align-items   : flex-start / flex-end / center / baseline / stretch    baseline : 基线对齐   stretch : 不设置高度时,项目延侧轴拉伸至父元素高度,为默认属性 |
  | align-self      | 设置侧轴对齐方式 | 给项目添加的属性,设置自己一个的对齐方式                      |





弹性布局案例:

![6](/Users/jiayiwang/Downloads/6.png)