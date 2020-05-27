- 1. 1.拖拽接口

  2. 1. 在h5中,如果想拖拽元素,就必须添加**draggable="true"**属性,图片和超链接默认就可以拖拽

     2. 拖拽事件中,分为拖拽元素和目标元素

     3. 1. 拖拽**o****ndrag** 整个拖拽过程中都会调用,持续

        2. 1. **ondragstart**         当拖拽开始时调用
           2. **ondragleave**         当鼠标离开拖拽元素时调用
           3. **ondragend**         当拖拽结束时调用

        3. 目标元素

        4. 1. **ondragenter**         当拖拽元素进入时调用
           2. **ondragover** 当停留在目标元素上时调用

- 如果想触发ondrop事件,那么就必须在ondragover中阻止浏览器的默认行为:e.preventDefault( );

- 1. **ondrop**      当在目标元素上松开鼠标时调用
  2. **ondragleave**      鼠标离开目标元素时调用

- 1. 通用(拖动文档中的任意元素可拖拽到任意位置)

- 时间原参数e: **e.target** 用事件捕获获取当前元素.使用obj存储

- 给document添加事件.

- 1. **dataTransfer**实现数据的存储和获取

  2. 1. **dataTransfer.setData(format,data)**存储数据

     2. 1. **format**:数据类型:text/html        text.uri-list
        2. **Data:**数据:一般为字符串值
        3. 通过他存储的数据,只能在drop事件中获取

  3. 1. **dataTransfer.getData**获取数据

- 在ondragstart中存储e.target.id,在ondrop中获取id找到对应元素

-  

- 1. 2.缓存

  2. 1. **sessionStorage**:容量5mb左右

- 这个数据本质上是存储到当前页的内存中,生命周期为关闭当前页面,同一浏览器不同窗口数据不共享

- 1. **serItem**(key,value):存储数据,以键值对的方式存储,字符串
  2. **getItem**(key):获取数据,通过指定名称的key获取对应的value值

- 找不到对应名称的key,则获取null

- 1. **removeItem**(key):删除指定key对应数据

- 删除时,key值错误,不报错,但也不会删除数据

- 1. **clear**( ):清空所有存储的数据

-  

- 1. **localStorage**:容量20mb

- 同一浏览器不同窗口可共享数据,永久生效,存储在硬盘上

- 方法与sessionStorage相同

- 清除需要

-  

- 1. 存储同一key值的多个数据,使用数组

  2. 1. 转换字符串 **JSON.stringify**(array) 原理加上引号
     2. 转换数组   **JSON.parse**(string)   原理去掉引号

-  

- 1. 3.多媒体接口

  2. 1. 案例效果图:

     2. 通过jq来实现功能

     3. 1. 获取播放器: var        video=$("video")[0];加上[0]获取的是dom对象

        2. 实现播放与暂停

        3. 1. 用paused方法判断播放状态
           2. play( ) / pause( ) 
           3. toggleClass("         fa-play fa-pause")进行样式切换

        4. 实现全屏操作

        5. 1. click(function(         ) { } );
           2. 不同浏览器需要添加不同的前缀>>能力测试

        6. 实现播放的业务逻辑:当视频文件可以播放时触发下面的事件oncanplay

        7. 1. 将视频文件设置为显示,用setTimeOut(         )模拟延时
           2. 获取视频总时长,计算出时分秒 video.duration 以秒做单位,有小数
           3. 计算时分秒 Math.floor( ),补0操作

        8. 实现播放过程中的业务逻辑,播放时触发ontimeupdate事件

        9. 1. 获取播放时间         video.currentTime
           2. 封装计算时分秒的方法
           3. 将结果展示在结构中
           4. 设置当前播放进度条样式,百分比

        10. 实现视频的跳播

        11. 1. 获取当前鼠标相对于父元素的left值--偏移量offsetX
            2. 计算偏移值相对总宽度的比例
            3. 计算这个位置对应的视频进度值
            4. 设置currentTime

        12. 播放完毕之后,重置播放器的状态 onended

- currentTime,播放按钮样式