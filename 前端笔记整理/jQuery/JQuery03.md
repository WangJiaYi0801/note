## JQuery第三天

## 1.今日重点

```
视频1没有声音
视频6没有声音
```



## 2.绑定事件

```js
bind() 事件绑定 类似于JS中的addEventListener

普通添加事件：
	$('#btn').click();

添加多个监听事件
$('#btn').bind({"click"：回调函数},{"mouseover"：回调函数});

//可以同时添加多个事件，但是事件执行函数是一样的
$('#btn').bind("mouseover mouseout",function(){});
```



```js
delegate(标签,事件类型，回调函数)  //给某个元素的子元素添加事件
```



```
on()  父元素调用为子元素添加事件
on(事件类型，标签，回调函数);

两种用法：
	1.两个参数： 事件名称 回调函数
	2.三个参数: 事件名称 添加事件元素，回调函数
```

```js
总结：
	bind:
         绑定多个事件
         参数:{"事件的类型":事件处理函数,....}
    delegate
         参数:父级元素.delegate("子级元素","事件类型",事件处理函数)
    on
         参数:父级元素.on("事件类型","子级元素",事件处理函数);

建议：在手机上或者动态添加的事件推荐使用on来添加
```



### 1.添加删除表格数据练习

```js
//点击按钮,显示遮挡层和对话框
//添加数据
$("#j_btnAddData").click(function () {
    $("#j_mask").css("display","block");
    $("#j_formAdd").css("display","block");
});
//关闭
$("#j_hideFormAdd").click(function () {
    $("#j_mask").css("display","none");
    $("#j_formAdd").css("display","none");
});
//真正的添加数据
$("#j_btnAdd").click(function () {
    //获取课程  j_txtLesson
    var lesson=$("#j_txtLesson").val();
    //获取学院  j_txtBelSch
    var belSch=$("#j_txtBelSch").val();
    //创建行--拼接字符串,添加到tbody中
    $("<tr><td>"+lesson+"</td><td>"+belSch+"</td><td><a href='javascrip:;' class='get'>GET</a></td></tr>").appendTo($("#j_tb"));
    //隐藏遮挡层和对话框
    $("#j_mask").css("display","none");
    $("#j_formAdd").css("display","none");
    $("#j_txtLesson").val("");//情况课程的文本框
});
//获取tbody中应用.get类样式的元素,绑定点击事件
//如果元素是动态添加的,那么非常推荐用on的方式为动态添加的元素绑定事件
$("#j_tb").on("click",".get",function () {
    $(this).parent().parent().remove();//删除tr
});
```



## 3.解绑事件

```js
on()  off()
bind()  unbind()
delegate()  undelegate()

//建议： 事件绑定和解绑，不要混着使用，普通的click方法可以使用off解绑
```

注意： 如果是通过父级元素添加事件，那么父级元素解绑事件，子级元素事件也会消失。

```js
 //第一个按钮通过on的方式绑定点击事件
$("#btn1").on("click",function () {
    alert("我被点了");
});
//第二个按钮把第一个按钮的点击事件解绑
$("#btn2").on("click",function () {
    //off()参数:要解绑的事件的名字
    $("#btn1").off("click");//解绑事件
});
```



```js
 //第一个按钮bind绑定事件
$("#btn1").bind("click",function () {
    alert("我又被点了");
});
//第二个按钮unbind解绑事件
$("#btn2").bind("click",function () {
    $("#btn1").unbind("click");//解绑事件的方法
});
```



```js
//点击第一个按钮为div中p绑定点击事件
$("#btn1").click(function () {
    $("#dv").delegate("p","click",function () {
        alert("我被点了");
    });
});
//点击第二个按钮为div中p解除绑定事件
$("#btn2").click(function () {
    $("#dv").undelegate("p","click");//解绑
});
```



## 4.事件触发

```js
事件触发： 就是你帮我去点击
$("#btn1").click();    
$("#btn1").trigger("click");//触发事件
$("#btn1").triggerHandler("click");//触发事件


$("#btn1").click(function () {
    $(this).css("backgroundColor","red");
});
//点击第二个按钮调用第一个按钮的点击事件---触发第一个按钮的点击事件
$("#btn2").click(function () {
    //触发事件--3三种方式
    //$("#btn1").click();
    //trigget()方法中需要写上触发事件的名字
    //$("#btn1").trigger("click");//触发事件
    $("#btn1").triggerHandler("click");//触发事件
});

注意： triggerHandler 不会触发浏览器的focus事件。
```



## 5.事件对象

```
e.delegateTarget----->div--->谁在替元素绑定的事件--div
e.currentTarget----->input--->真正是谁绑定的事件
e.target---->input----触发的事件
```



### 1.按键改变颜色

```js
$(document).keydown(function (e) {
    var keyCode=e.keyCode;//键盘按下后的键对应的键值
    switch (keyCode){
        case 65:$("#dv").css("backgroundColor","red");break;
        case 66:$("#dv").css("backgroundColor","green");break;
        case 67:$("#dv").css("backgroundColor","blue");break;
        case 68:$("#dv").css("backgroundColor","yellow");break;
        case 69:$("#dv").css("backgroundColor","black");break;
    }
});
```



## 6.事件冒泡

```
取消事件冒泡：
e.stopPropagation(); 或者return false;

return false;  还可以用来取消默认事件。
```



## 7.链式编程原理

```
链式编程原理： 内部返回了return this当前对象；

注意： 有些方法传入了参数，才能返回对象，如果是直接获取属性的值，返回的是内容，就不是对象了。
```

```js
function Student(name) {
    this.name=name;
    this.sayHi=function (name) {
        if(name){
            console.log("俺是"+name);
            return this;
        }else{
            console.log("我的名字叫"+this.name);
        }
        //console.log("我的名字叫"+this.name);
        // return this;//把当前对象返回
    };
    this.eat=function () {
        console.log("我就是喜欢吃大蒜+榴莲+臭豆腐");
    };
}
var stu=new Student("小明");
stu.sayHi().eat();

```

### 1.评分案例

```js
 $(".comment>li").mouseover(function () {
     $(this).text("★").prevAll("li").text("★").end().nextAll("li").text("☆");
 }).mouseout(function () {
     $(".comment").find("li").text("☆");
     $(".comment>li[index=1]").text("★").prevAll("li").text("★")
 }).click(function () {
     $(this).attr("index","1").siblings("li").removeAttr("index");
 });
```



## 8.each方法

```
each() 方法也叫迭代，简单点就是循环。
注意: Jquery中有隐式迭代，不需要我们再进行遍历某些元素操作，但是不一样的操作需要自己实现。

例如： 批量给标签添加事件，但是每个标签的内容不一样，就可以使用each()方法

总结： 你可以认为each就是一个简单的for循环。

```

```js
$("#uu>li").each(function (index,element) {               
	$(element).css("opacity",(index+1)/10);
});
```



## 9.其他

### 1.多库共存问题

```js
$.noConflict()  //就是JQuery的控制权 默认的控制权变量有： $  和 JQuery
//让jquery对$对象进行释放控制权
var xy=$.noConflict();
//从此以后xy就是曾经的$---一毛一样的
var $=100;//$原本是对象--->变量
xy(function () {
    xy("#btn").click(function () {
        alert("哈哈,我又变帅了");
    });
});
```



### 2.JQuery插件

```
别人使用Jquery写了一个完成的功能效果，共享出来，挺好用的就是插件了。
使用步骤： 
	1.引入js
	2.引入css
	3.复制html
	4.看说明文档
	
注意： 有的插件没有css或者html，但是一定有js，说明书完善的我们推荐使用。
注意： 有的插件中没有带上JQuery.js文件，需要自己提前引入，才行.
```

推荐插件库：

- [JQuery之家](http://www.htmleaf.com/)
- [JQuery插件库](http://www.jq22.com/)



### 3.自己做插件

```js
1.使用：$.fn.方法名=function(){} 封装方法
2.单独将js代码创建一个文件
3.如果有css将css也单独新建一个文件
4.结构放在说明文档中

```



4.JQueryUI

```
JQuery中单独的功能效果演示.
使用方法： 审查元素找内容，然后复制
```

