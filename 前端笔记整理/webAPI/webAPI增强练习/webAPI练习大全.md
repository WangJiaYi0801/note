# WebAPI练习

## 1.练习说明

```
这一阶段我们主要是用JS写页面动效的，所以我们要学DOM和BOM操作API，也就是js操作页面元素等功能。
```

## 2.DOM语法知识

### 1.找标签

```js
var div = document.getElementById('main');  //根据id找标签
var divs = document.getElementsByTagName('div'); //根据标签名找标签,返回数组
var inputs = document.getElementsByName('hobby'); //根据name获取标签，返回数组
var mains = document.getElementsByClassName('main'); //根据类名获取标签，返回数组
综合写法：
	var text = document.querySelector('#text');  ---通过id获取元素
	var boxes = document.querySelectorAll('.box'); ---通过类名获取元素
```

### 2.事件操作

```js
//点击按钮,弹出框,这样就是一个完整的事件操作.
//单击  按钮  弹框
var box = document.getElementById('box');
box.onclick = function() {
    console.log('代码会在box被点击后执行');  
};	
其他事件：
	onclick       单击
    onmouseover   鼠标移入
    onmouseout    鼠标移除
    ondblclick    双击
    onfocus       获得焦点
    onblur        失去焦点
```

### 3.属性操作

```js
//找到标签，并直接点属性名，就可以获取值和设置值
var link = document.getElementById('link');
link.href
link.title
link.id
link.class
link.src

//表单元素
    - value 用于大部分表单元素的内容获取(option除外)
    - type 可以获取input标签的类型(输入框或复选框等)
    - disabled 禁用属性
    - checked 复选框选中属性
    - selected 下拉菜单选中属性
var txt = document.getElementById('txt');
txt.value
txt.type
txt.disabled
txt.checked
txt.selected

```

### 4.内容操作

```js
var box = document.getElementById('box');
box.innerHTML = '我是文本<p>我会生成为标签</p>';   //标签会翻译
box.innerText = '我是文本<p>我不会生成为标签</p>'; //标签直接输出
```

### 5.修改样式

```js
使用style方式设置的样式显示在标签行内
var box = document.getElementById('box');
box.style.width = '100px';
box.style.height = '100px';
box.style.backgroundColor = 'red';
box.style.height = '100px';
```

注意: 通过样式属性设置宽高、位置的属性类型是字符串，需要加上px

### 6.类名的操作

```js
修改标签的className属性相当于直接修改标签的类名
var box = document.getElementById('box');
box.className = 'show';
```

### 7.节点操作

```
appendChild()   添加子节点
insertBefore()  插入节点
removeChild()  移除节点
replaceChild() 替换节点

节点属性：
	parentNode   父节点
	childNodes   子节点
	children     子元素
	nextSibling/previousSibling 上一个兄弟节点和下一个兄弟节点
	firstChild/lastChild   第一个或最后一个子元素
```



### 8.事件监听

```js
box.addEventListener('click', eventCode, false);    //添加事件
box.removeEventListener('click', eventCode, false);  //移除事件
```



### 9.事件对象属性

```
- event.type 获取事件类型
- clientX/clientY     所有浏览器都支持，窗口位置
- pageX/pageY       IE8以前不支持，页面位置
- event.target || event.srcElement 用于获取触发事件的元素
- event.preventDefault() 取消默认行为
```

### 10.鼠标键盘事件

```
- onmouseup 鼠标按键放开时触发
- onmousedown 鼠标按键按下触发
- onmousemove 鼠标移动触发
- onkeyup 键盘按键按下触发
- onkeydown 键盘按键抬起触发
```



## 3.BOM语法知识

### 1.弹框效果

```
	- alert()
	- prompt()
	- confirm()
```

### 2.页面加载和卸载

```js
onload事件:
    window.onload = function () {
      // 当页面加载完成执行
      // 当页面完全加载所有内容（包括图像、脚本文件、CSS 文件等）执行
    }
onunload事件:
	window.onunload = function () {
  		// 当用户退出页面时执行
	}
```

### 3.定时器

```
单次定时: setTimeout()和clearTimeout()  只执行一次
// 创建一个定时器，1000毫秒后执行，返回定时器的标示
var timerId = setTimeout(function () {
  console.log('Hello World');
}, 1000);

// 取消定时器的执行
clearTimeout(timerId);
```

```
多次定时:setInterval()和clearInterval()
// 创建一个定时器，每隔1秒调用一次
var timerId = setInterval(function () {
  var date = new Date();
  console.log(date.toLocaleTimeString());
}, 1000);

// 取消定时器的执行
clearInterval(timerId);
```

### 4.页面偏移量

```
offsetWidth  边框+内容
offsetHeight 边框+内容

clientWidth  内容
clientHeight 内容

scrollWidth  滚动宽度
scrollHeight 滚动高度

```



```js
- offsetParent用于获取定位的父级元素
- offsetParent和parentNode的区别

var box = document.getElementById('box');
console.log(box.offsetParent);
console.log(box.offsetLeft);
console.log(box.offsetTop);
console.log(box.offsetWidth);
console.log(box.offsetHeight);
```

![](media/1498743216279.png)

客户区大小：

​	

```
var box = document.getElementById('box');
console.log(box.clientLeft);
console.log(box.clientTop);
console.log(box.clientWidth);
console.log(box.clientHeight);
```

![](1498743269100-1538132387818.png)



滚动偏移量：

```
var box = document.getElementById('box');
console.log(box.scrollLeft)
console.log(box.scrollTop)
console.log(box.scrollWidth)
console.log(box.scrollHeight)
```

![1498743288621](media/1498743288621.png)



## 4.页面动效

### 1.检测用户名和密码

```

```



### 2.设置下拉框选中项

```

```



### 3.搜索文本框

```

```



### 4.全选反选

```

```



### 5.开关灯效果

```

```



### 6.显示隐藏二维码

```

```



### 7.高亮显示正在输入的文本框

```

```



### 8.隔行变色和高亮显示

```

```



### 9.Tab栏切换

```

```



### 10.鼠标跟随练习

```

```



### 11.倒计时练习

```

```



### 12.拖拽动画

```

```



### 13.弹出层动画

```

```



### 14.放大镜动画

```

```



### 15.模拟滚动条动画

```

```



### 16.无缝滚动轮播图

```

```



### 17.回到顶部

```

```

