# JQuery快速入门

## 1.JQuery简介

```
JQuery是一个JS库，别人使用JS写了很多功能给我们用，主要集中在以下几点：
	1.简化找标签，改样式等操作语法
	2.增加了动画的操作方法
	3.解决了相关属性的兼容性写法
```



## 2.JQuery语法

### 1.找标签

```js
$('#box')  id选择器
$('.box')  类选择器
$('div')   标签选择器
$('.box li) 后代选择器
$('.box > a')  子代选择器
$('.box, .one') 并集选择器

选择器筛选
$('.box li:first')  第一个li
$('.box li:last')   最后一个li
$('.box li:eq(2)')  第3个li(索引从0开始)
$('.box li:gt(3)')  索引大于3的li
$('.box li:lt(3)')  索引小于3的li
$('.box li:even')   偶数li  (因为索引从0开始，所以显示相反)
$('.box li:odd')   奇数li
//表单筛选
$('.box input:text')   input中是text的标签
$('.box input:radio')   input中是radio的标签
$('.box input:checkbox')   input中被选中的标签

//方法找标签
$('.box li').eq(0)   第一个li
$('.box li').first() 第一个li
$('.box li').last()  最后一个li

$('.box').parent()      父元素
$('.box').children(条件) 所有子元素
$('.box').siblings(条件) 所有兄弟元素
$('.box').find(条件)     在box中查找某个元素
$('.box').next()        下一个元素
$('.box').nextAll()     下面所有的元素
$('.box').prev()        上一个元素
$('.box').prevAll()     上面所有元素
```



### 2.加事件

```
标签.click(function(){});
标签.mouseover()
标签.mouseout()
标签.hover()
其他类似

标签.on(事件类型，回调函数);
$('.box').on('click',function(){});
```



### 3.改样式和内容属性

```js
//内容操作
标签.html()   修改内容
标签.val()    修改表单的value值
标签.text()   修改文字内容

//样式操作
标签.css('属性名','属性值');
标签.css({属性名:属性值,属性名:属性值});

//类的操作
标签.addClass('current') 
标签.removeClass('current')  
标签.toggleClass('current')
标签.hasClass('current')  


//自定义属性操作
标签.attr('属性名'，'属性值');
标签.removeAttr('属性名');
标签.prop('属性名'，'属性值');  

注意： prop方法用于获取类似于checked这种标签独有的属性，Jquery未封装
```



### 4.加动画

```js
//显示隐藏
show()
hide()
toggle()

//上拉下拉
slideDown()
slideUp()
slideToggle()

//淡入淡出
fadeIn()
fadeOut()
fadeTo()
fadeToggle()

//自定义动画
animate({},时间)  //注意参数写法很多，都带引号总没错  
stop()      停止动画
delay()     延迟动画
```



### 5.节点操作

```js
empty()  清空
remove()  移除
clone()   克隆
replace() 替换

after()  标签之后插入
before() 标签之前插入

append()  标签内最后追加内容
appendTo() 将某个标签添加到父标签中
```

### 7.位置大小获取

```js
//获取left值和top值
标签.offset().left
标签.offset().top

//获取滚动距离
标签.scrollTop()
标签.scrollLeft()

//获取宽高
标签.width()
标签.height()



```



### 6.其他

```js
//阻止冒泡
e.stopPropagation()

//获取坐标
e.pageX
e.pageY

//获取标签索引
标签.index();  

//遍历
each()

//入口函数
$(function(){});


//当前元素
$(this)

```



### 7.插件的使用

```

```



## 3.JQuery练习



### 1.开关灯效果





### 2.列表排它高亮显示颜色



### 3.QQ好友面板



### 4.二级下拉菜单



### 5.精品突出展示案例



### 6.手风琴案例



### 7.滚动固定导航



### 8.全选反选



### 9.轮播图





