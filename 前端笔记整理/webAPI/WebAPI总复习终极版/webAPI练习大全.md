# WebAPI练习()

## 1.练习说明

```text
这一阶段我们主要是用JS写页面动效的，所以我们要学DOM和BOM操作API，也就是js操作页面元素等功能。
一念成佛，一念成魔。会与不会就在一念之间。
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
    ondblclick    双击
    onmouseover   鼠标移入
    onmouseout    鼠标移除
   
    onmouseup     鼠标按键放开时触发
    onmousedown   鼠标按键按下触发
    onmousemove   鼠标移动触发
    
    onmouseenter  鼠标进入(区别在于不会冒泡)
    onmouseleave  鼠标离开
    
    onkeyup       键盘按下事件
    onkeydown     键盘抬起事件
    
    onfocus       获得焦点
    onblur        失去焦点
    
    onscroll      滚动事件
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

### 5.自定义属性操作

```
- getAttribute() 获取标签行内属性
- setAttribute() 设置标签行内属性
- removeAttribute() 移除标签行内属性
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
	parentNode  父节点
    childNodes  所有子节点（2*i+1）
    firstChild  第一个子节点
    lastChild   最后一个字节点
    nextSibling 下一个兄弟节点
    previousSibling  上一个兄弟节点
    hasChildNodes() 是否有子节点
```



### 8.元素操作

```

children 所有子元素
firstElementChild  第一个子元素
lastElementChild   最后一个字元素
nextElementSibling 下一个兄弟元素
previousElementSibling 上一个兄弟元素

createElement()  //创建元素，需要在document中创建
```



### 8.事件监听

```js
box.addEventListener('click', eventCode, false);    //添加事件
box.removeEventListener('click', eventCode, false);  //移除事件
//注意： 移除事件的前提是添加事件的执行函数是有名的，不能是匿名函数

IE老版兼容性写法：
attachEvent('onclick',function(){})
detachEvent('onclick',function(){})

//移除事件的第三种写法
	box.onclick=null;
```

注意：监听事件和onclick的区别，1.监听事件可以添加多个，onclick只能1个， 2.监听事件有捕获冒泡，onclick只有冒泡

### 9.事件j阶段和对象属性

```js
事件捕获(从外到内)
目标阶段(当前点击事件)
事件冒泡（从内到外)

--------------------------------------------------
e 事件对象
e.eventPhase 事件冒泡所处的阶段: 1捕获  2目标执行 3.冒泡阶段
e.target    触发事件的对象
this        事件加载的对象
e.type      获取事件名称

e.pageX    鼠标点击相对于页面的距离
e.pageY    鼠标点击相对于页面的距离 
e.clientX  鼠标点击，相对于可视区(浏览器窗口左端)的距离
e.clientY  鼠标点击，相对于可视区(浏览器窗口顶端)的距离

e.keyCode  获得键盘数字编码

//取消事件冒泡
e.stopPropagation();

//取消冒泡非标准方法
e.cancelBubble = true;
```

### 10.鼠标键盘事件

```
- onmouseup 鼠标按键放开时触发
- onmousedown 鼠标按键按下触发
- onmousemove 鼠标移动触发
- onkeyup 键盘按键弹起触发
- onkeydown 键盘按键按下触发
```

### 11.其他

#### 1.取消a标签默认跳转

```js
1.在href属性中填写： javascript:void(0)
2.在事件最后添加return false;
3.e.preventDefault(); //DOM标准方法
4.e.returnValue = false; //IE老版本
```

#### 2.节点和元素相关的概念

```
一个节点有三个属性： nodeType  nodeName  nodeValue
nodeType  节点的类型
 1 元素节点
 2 属性节点
 3 文本节点 
nodeName 节点名称
nodeValue 节点值:元素节点的nodeValue始终是null
--------------------------------------------------------
节点： 包括 空格 + 标签
元素： 就是标签
```

#### 3.打印输出

```js
console.log('123');
//可以打印一个对象，方便查看对象中的属性
console.dir(box);  
```

#### 4.动态创建元素三种方式

```js
//向页面中添加内容 ,问题： 在事件中添加内容，会导致页面之前的内容被清空
document.write()  认识标签

//向页面中添加内容，可以在事件中添加, 如果频繁的拼上接标签.innerHTML会导致页面卡顿（dom树频繁更新）
element.innerHTML 认识标签 

//如果用字符串拼接，会导致内存泄漏，如果要拼接字符，使用数组拼接。
 document.createElement()
```

#### 5.三元运算符的使用方法

```
表达式1 ? 表达式2 : 表达式3；

表达式1 || 表达式2
```

#### 6.获取页面滚动距离

```js
document.body.scrollTop   获取页面滚动距离
document.body.scrollLeft
//前提是得有滚动条
兼容性写法：
document.documentElement.scrollTop
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

- 一般我们写写代码都会带上window.onload方法，因为将来大部分代码都是外链式。
- 函数需要放在window.onload的外部，才能被标签上调用到，因为会改变作用域。

### 3.定时器

```js
单次定时: 
	setTimeout()    
    clearTimeout()  
    
    // 创建一个定时器，1000毫秒后执行，返回定时器的标示
    var timerId = setTimeout(function () {
      console.log('Hello World');
    }, 1000);

    // 取消定时器的执行
    clearTimeout(timerId);
```

```js
多次定时:
	setInterval()
	clearInterval()
	
    // 创建一个定时器，每隔1秒调用一次
    var timerId = setInterval(function () {
      var date = new Date();
      console.log(date.toLocaleTimeString());
    }, 1000);

    // 取消定时器的执行
    clearInterval(timerId);
```

### 4.页面偏移量

```js
offsetWidth  边框+内容
offsetHeight 边框+内容
offsetTop   定位父元素顶部距离
offsetLeft  定位父元素左边距离

clientWidth  内容
clientHeight 内容
clientTop   上边框
clientLeft  左边框

scrollWidth  宽度+出去的宽度
scrollHeight 高度+出去的高度
scrollTop    上面滚出去的距离
scrollLeft   距离左边滚出去的距离

offsetParent用于获取定位的父级元素
```

### 5.浏览器对象属性

```
location对象
	 herf   跳转地址
     assign() 让页面跳转到指定的网页(可以后退)
     replace()  替换地址栏中的地址（不能后退）
     reload()  重新加载页面(true强制服务器获取，false可以缓存获取)
     
history对象的方法:
	back()
    forward()
    go()	1 前进   -1后退
    
navigator对象的属性：
	userAgent:通过userAgent可以判断用户浏览器的类型
	platform:通过platform可以判断浏览器所在的系统平台类型.
```



## 4.简单案例



### 1.点击按钮，切换图片



### 2.点击按钮盒子显示隐藏



### 3.美女相册



### 4.检测用户名和密码

```

```



### 5.设置下拉框选中项

```

```



### 6.搜索文本框

```

```





### 7.开关灯效果

```

```



### 8.显示隐藏二维码

```

```



### 9.高亮显示正在输入文本框

```

```



### 10.隔行变色和高亮显示

```

```



### 11.放大镜动画

```

```



### 12.鼠标跟随练习

```

```

### 13.定时器动画

```

```



### 14.回到顶部

```

```



## 5.工作中必备案例

### 1.全选反选

```

```

### 2.Tab栏切换

```

```



### 3.倒计时练习

```

```



### 4.拖拽动画

```

```



### 5.模态窗口

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            margin:0;
            padding:0;            
        }
        html,body{
            height: 100%;
        }
        body{
            height: 3000px;
        }
        .bg{
            position: fixed;
            left:0;
            top:0;
            width:100%;
            height: 100%;
            background-color:rgba(0,0,0,0.6);
            display: none;
        }
        .login{
            width: 400px;
            height: 300px;
            background-color: #fff;
            border-radius: 5px;
            position: absolute;
            left: 50%;
            top:50%;
            margin-top: -150px;
            margin-left: -200px;           
        }
        .login span{
            width: 20px;
            height: 20px;
            background-color: red;
            float:right;
            text-align: center;
            line-height: 20px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <button id="btn">点击按钮</button>
    <div class="bg" id="bg">
        <div class="login" id="login">            
            <span id="close">X</span>
        </div>
       
    </div>

    <script>
        var myBtn =document.getElementById('btn');
        var bg = document.getElementById('bg');
        var closeBtn =document.getElementById('close');
        var loginBox = document.getElementById('login');
        myBtn.onclick=function(){
            bg.style.display='block';
        }
        
        closeBtn.onclick=function(){
            bg.style.display='none';
        }

        // 按下login盒子
        loginBox.onmousedown=function(e){
            //计算当前鼠标在盒子中的位置
            var x = e.pageX - loginBox.offsetLeft;
            var y =e.pageY - loginBox.offsetTop;

            // 鼠标在页面上移动
            document.onmousemove=function(e){
                var moveX = e.pageX - x;
                var moveY = e.pageY - y;
                //注意会偏移，因为定位居中
                loginBox.style.left=moveX+200+'px';
                loginBox.style.top=moveY+150+'px';
            }
            document.onmouseup=function(){
                document.onmousemove=null;
            }
        }

        //拓展： 可以做范围判断
    </script>
</body>
</html>
```



### 6.无缝滚动轮播图

```
//总共就两个功能： 让图片移动，让原点切换
//先写有缝轮播图


//再写无缝轮播
1.复制第一张图添加到图片盒子的最后
2.修改ul图片盒子的宽度，让图片放的下
3.切换下一张：可以移动到第六张 如果是第六张再下一张，就让他瞬间移动到第一张,然后索引为0，注意，焦点切换函数中要判断，如果是第六张图，索引要为0，不能用5

4.上一张数值不变，小于0 时，瞬间移动到第六张，索引还是第五张，为4

//点击焦点的时候注意索引同步

```

