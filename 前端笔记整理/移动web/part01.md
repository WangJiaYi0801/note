- 1. 1.二倍图

  2. 1. 原始图片尺寸的二倍
     2. 二倍图一般为640,三倍为750

-  

- 1. 2.远程调试

  2. 1. 模拟调试

     2. 真机调试

     3. 1. 上传服务器
        2. 模拟本地服务器,ghostlab,weinre,debuggap

-  

- 1. 3.视口

  2. 1. viewport:视口,显示内容

     2. PC端 : viewport的大小等于浏览器窗口的大小

     3. 1. 父容器设具体宽高,如果超过viewport,出现滚动条
        2. 父元素设宽100%,子元素具体宽高,子元素超过viewport,自动换行
        3. 父元素设弹性盒子,子元素缩小

     4. 移动端

     5. 1. 有默认的viewport,980/1024,导致页面缩放或者出现横向滚动条

        2. 元素没有直接显示在设备上,而是显示在视口viewport中

        3. pc端的页面在移动端显示会被缩放

        4. layout viewport(布局视口-默认大小)

        5. 1. 获取viewport的大小

           2. 1. document.documentElement.clientWidth ; 
              2. document.documentElement.clientHeight ;

        6. ideal viewport(理想视口-设备屏幕大小)

        7. 1. 新设备获取大小

           2. 1. window.screen.width          ;
              2. window.screen.height          ;

           3. 老设备

           4. 1. window.screen.width          / window.devicePixelRatio ;
              2. window.screen.height          / window.devicePlxelRatio ;

-  

- 1. 4.屏幕适配

  2. 1. <meta  name="viewport"        content="width="device-width">

     2. 1.  建议写在原有的meta的后面
        2. name用于说明当前meta是来设置viewport属性的
        3. width:是viewport的宽度,device-width是设备的宽度

     3. <meta name="viewport"        content="initial-scale=1">

     4. 1. initital-scale设置页面的初始缩放值,为一个数字,可以带小数 
        2. 效果与width=device-width相同,考虑兼容性,都写上

     5. 其他属性

     6. 1. user-scalable: 是否允许用户进行缩放,yes/no
        2. minimum-scale: 允许用户的最小缩放值
        3. maximum-scale: 允许用户的最大缩放值

-  

- 1. 5.京东首页--html+css

  2. 1. 公共样式--base.css

     2. 1. 样式重置
        2. 添加新的样式

     3. 整体结构

     4. 1. 外层最大的盒子jd-layout

        2. 1. 有最大宽度640px,最小宽度320px
           2. 居中显示

        3. 搜索块jd-search

        4. 1. 左右固定,中间自适应

           2. 1. flex方法:兼容性问题
              2. 中间盒子margin:0 100px;左右盒子定位

           3. 设置背景图片大小一半

           4. 使用伪元素添加放大镜

        5. 轮播图jd-banner

        6. 导航块jd-nav

        7. 1. 解决基线对齐,用display:block;

        8. 产品块

        9. 1. 秒杀块,添加特殊标记,与后面的产品块区别

-  