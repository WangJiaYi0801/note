- 1. 1.触屏事件

  2. 1. 触发条件:必须在移动端+ 必须有自己的宽高

  3. 1. touchstart:手指触摸屏幕时触发

     2. touchmove:手指在屏幕上滑动时触发

     3. 1. 是持续触发的

     4. touchend:手指离开屏幕时触发

     5. touchcancel:意外中断时触发

     6.  ![图片1](/Users/jiayiwang/Downloads/图片1.png)

     7. Touch对象

     8. 1. clientX / clientY 手指相对于layout viewport 的水平/垂直像素距离

        2. pageX / pageY 手指相对于layout viewport 的水平/垂直像素距离(含滚动)

        3. screenX / screenY 手指相对于layout viewport 的水平/垂直像素距离(含滚动)

        4. 1. 未设置viewport时,screenX         / Y 在Webview中不正确

     9. 手指对象:

     10. 1. touches(屏幕上的所有的触摸对象) 
         2. targetTouches(屏幕上所有的目标触摸手指对象)
         3. changedTouches(最后手指松开的那个手指对象)

-  

- 1. 2.京东页面--js部分

  2. 1. 注意--在页面加载事件外封装事件函数,使浏览器先解析,在页面加载完成后再调用,加快调用速度,提高用户体验

- window.onload = **function**() {

- searchEffect();

- timeBack();

- lunBoTu();

- }

- 1. 顶部固定搜索框底色随页面滑动而改变

  2. 1. 封装函数
     2. 获取banner高度即滚动范围,及搜索框对象
     3. 添加事件,在页面滚动时,获取滚动距离,在banner高度之内,透明度随高度比例变化

- **function** searchEffect() {

- **var** banner = document.querySelector('.jd_banner');

- **var** bannerHeight = banner.offsetHeight;

- **var** searchbox = document.querySelector('.jd_search');

-  

- window.onscroll = **function**() {

- **var** offsetHeight = document.body.scrollTop || document.documentElement.scrollTop;

- **var** opacity = 0;

- if (offsetHeight < bannerHeight) {

- opacity = offsetHeight / bannerHeight;

- searchbox.style.backgroundColor = "rgba(233,35,34," + opacity + ")";

- }

- }

- }

- 1. 秒杀区域,倒计时效果

  2. 1. 封装函数
     2. 获取对象,设定总时间
     3. 启动定时器,每秒执行一次
     4. 计算时分秒的值,写入对应位置
     5. 当时间减到0时,停止定时器

- **function** timeBack() {

- **var** spans = document.querySelector('.jd_sk_time').querySelectorAll('span');

- **var** total = 3600;

-  

- **var** timeId = setInterval(**function**() {

- total--;

- **var** hour = Math.floor(total / 60 / 60);

- **var** mintue = Math.floor(total / 60 % 60);

- **var** second = Math.floor(total % 60);

- spans[0].innerText = Math.floor(hour / 10);

- spans[1].innerText = Math.floor(hour % 10);

- spans[3].innerText = Math.floor(mintue / 10);

- spans[4].innerText = Math.floor(mintue % 10);

- spans[6].innerText = Math.floor(second / 10);

- spans[7].innerText = Math.floor(second % 10);

-  

- if (total == 0) {

- clearInterval(timeId);

- return;

- }

- }, 1000);

- }

-  

- 1. 轮播图

  2. 1. 前期准备

     2. 1. 封装函数
        2. 在图片列表前添加最后一张图的克隆,在最后添加第一张图的克隆
        3. 修改ul和li 的宽度
        4. 修改ul的位置,使其显示第一张图
        5. 封装函数,使点标记随着index的值改变而改变,注意第一张和最后一张的特殊性
        6. 一开始,使点标记标在第一个点
        7. 当屏幕宽度变化时,重新计算宽度

     3. 添加定时器,自动轮播

     4. 1. 给定时器封装函数,方便开始和停止
        2. 时间增加,index值加一,ul位置随之移动
        3. 注意最后一张图,需跳转到前面,if判断,修改index和ul位置
        4. 跳转需要等渐变,即移动的过程结束后,才能执行,添加延时
        5. 修改点标记
        6. 注意渐变属性,在正常移动时要添加渐变,最后一张跳转时,需要关闭渐变,使其瞬间移动

     5. 手指滑动,手动轮播

     6. 1. 给ul添加监听事件

        2. 当手指触碰屏幕时:

        3. 1. 清除定时器
           2. 记录此时的点击位置的x值,记录此时ul的左移的距离

        4. 当手指滑动时:

        5. 1. 需要将渐变属性清除,避免画面延时移动
           2. 记录移动位置的x值
           3. 计算前后移动距离
           4. 计算ul需要移动距离,使其随着手指的位置移动

        6. 当手指松开时:

        7. 1. 判断移动距离是否大于100px,大于则移动图片,小于则回到原来的图片位置
           2. 大于100px时,再判断正负,即向左还是向右
           3. 向左移动,则使ul移动到后一张图的位置,向右移动,则移动到前一张图

        8. 当渐变的动画结束后

        9. 1. 判断是否是第一张或最后一张图,取消渐变效果,瞬间移动图片
           2. 修改点标记
           3. 设置短暂的计时器,在瞬移之后,重启定时器

        10. 代码优化--添加节流阀

        11. 1. 声明标志变量isEnd,值为true
            2. 在手指松开的事件中使isEnd的值改为false
            3. 在动画结束的事件中使isEnd的值回到true
            4. 在手指移动的事件中判断isEnd是否为true
            5. 这样设置后,在动画结束之前,无法进行下一次的移动,避免连续触发事件,导致错乱
            6. 注意,在手指移动事件中,需要清除distanceX的值,否则会继承上一次的值,导致连续触发手指松开的事件

-  

-  

- *//**轮播图*

- **function** lunBoTu() {

- *// 1.**修改图片**,**前后分别添加图片*

- **var** bannerUl = document.querySelector('.jb_bannerImg');

- **var** lis = document.querySelectorAll('.jb_bannerImg>li');

- **var** liFirst = lis[0];

- **var** liLast = lis[lis.length - 1];

- bannerUl.appendChild(liFirst.cloneNode(true));

- bannerUl.insertBefore(liLast.cloneNode(true), bannerUl.firstChild);

-  

- *// 2.**修改**ul**的宽度**,**和**li**的宽度*

- lis = document.querySelectorAll('.jb_bannerImg>li');

- **var** liWidth = lis[0].offsetWidth;

- bannerUl.style.width = liWidth * lis.length + 'px';

- for (**var** i = 0; i < lis.length; i++) {

- lis[i].style.width = parseInt(liWidth) + 'px';

- }

- **var** index = 1;

- bannerUl.style.left = -liWidth * index + 'px';

-  

- *//**封装函数**,**点标记的变化*

- **var** indicator = document.querySelectorAll('.jd_bannerIndicator>li');

- **function** indicaterChange(index) {

- for (**var** i = 0; i < indicator.length; i++) {

- indicator[i].classList.remove('active');

- }

- if (index == 1) {

- indicator[0].classList.add('active');

- } else {

- indicator[index - 1].classList.add('active');

- }

- }

- *//**使点标记中的第一个选中*

- indicaterChange(index);

-  

- *//* *屏幕宽度变化时**,**重新计算宽度*

- window.onresize = **function**() {

- liWidth = document.querySelector('.jd_banner').offsetWidth;

- bannerUl.style.width = liWidth * lis.length + 'px';

- for (**var** i = 0; i < lis.length; i++) {

- lis[i].style.width = parseInt(liWidth) + 'px';

- }

- }

-  

- *// 3.**定时器**,**自动轮播*

- **var** timeId;

- startTimeId();

- **function** startTimeId() {

- timeId = setInterval(**function**() {

- index++;

- bannerUl.style.transition = 'left 0.5s';

- bannerUl.style.left = -liWidth * index + 'px';

- setTimeout(**function**() {

- if (index > 8) {

- bannerUl.style.transition = 'none';

- index = 1;

- bannerUl.style.left = -liWidth * index + 'px';

- }

- indicaterChange(index);

- }, 500)

- }, 2000);

- }

-  

- *// 4.**手指滑动**,**手动轮播*

- **var** startX, currentX, moveX, distanceX;

- **var** isEnd = true;

-  

- bannerUl.addEventListener('touchstart', **function**(e) {

- clearInterval(timeId);

- startX = e.touches[0].clientX;

- })

-  

- bannerUl.addEventListener('touchmove', **function**(e) {

- if (isEnd) {

- bannerUl.style.transition = 'none';

- moveX = e.touches[0].clientX;

- distanceX = moveX - startX;

- } else {

- distanceX = 0;

- }

- bannerUl.style.left = -index * liWidth + distanceX + 'px';

- })

-  

- bannerUl.addEventListener('touchend', **function**() {

- isEnd = false;

- console.log(distanceX);

- if (Math.abs(distanceX) > 100) {

- if (distanceX > 0) {

- index--;

- } else {

- index++;

- }

- }

- bannerUl.style.transition = 'left 0.5s';

- bannerUl.style.left = -liWidth * index + 'px';

- })

-  

- *//**添加监听事件**,**当动画结束后**,**实现无缝滚动的衔接*

- bannerUl.addEventListener('webkitTransitionEnd', **function**() {

- console.log('end');

- if (index < 1) {

- index = 8;

- }

- if (index > 8) {

- index = 1;

- }

- bannerUl.style.transition = 'none';

- bannerUl.style.left = -liWidth * index + 'px';

-  

- indicaterChange(index);

-  

- setTimeout(**function**() {

- isEnd = true;

- clearInterval(timeId);

- startTimeId();

- }, 100);

- })

-  

- }

-  

-  ![2018-12-07_204538](/Users/jiayiwang/Downloads/2018-12-07_204538.png)

-  

-  

-  

-  