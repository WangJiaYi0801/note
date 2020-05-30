# JQuery第二天

## 1.今日重点

```
第15个视频没有声音
第19个视频没有声音
第26个视频没有声音


```



## 2.类操作

```
addClass('current')     //添加类
removeClass('current')  //移除类
toggleClass('current)    //开关类 
hasClass('current')     //是否有某个类，返回true和false

//可以添加多个类
addClass('current').addClass('bd');
addClass('current bd');
//注意添加类名前面没有点。
```



### 1.开关灯案例

```js
//方法1
$("#btn").click(function () {             
    if($("body").hasClass("cls")){                   
        $("body").removeClass("cls");
        $(this).val("关灯");

    }else{                   
        $("body").addClass("cls");
        $(this).val("开灯");
    }
});

//方法2
$("#btn").click(function () {
    $("body").toggleClass("cls");//切换类样式
});
```

### 2.Tab菜单案例

```js
 //获取ul中的所有的li,调用鼠标进入的事件
$(".tab>li").mouseover(function () {
    //移除当前的li的所有兄弟元素li的类样式
    $(this).siblings("li").removeClass("active");
    //让当前li添加类样式
    $(this).addClass("active");

    //获取当前的li的索引
    var index=$(this).index();                
    $(".products>div:eq("+index+")").siblings("div").removeClass("selected");
    $(".products>div:eq("+index+")").addClass("selected");
});
```

### 3.css和类样式操作总结

```js
 css()
     css("属性","属性值");
     css("属性","属性值").css("属性","属性值");
     css({"属性":"属性值","属性":"属性值"});
 addClass()
     addClass("类样式名字");添加一个类样式
     addClass("类样式名字1 类样式名字2");
 removeClass()
     removeClass("类样式名字");移除类样式
     removeClass();移除的是当前元素中所有的类样式
 hasClass();判断当前元素是否应用了某个类样式
 toggleClass();切换元素的类样式的
```



## 3.链式编程

```
如果多行代码操作的是同一个对象的样式属性，那么可以连接起来写，简化代码。
```

```js
 $("#dv").html("<p>这是一个p</p>");
 $("#dv").css("backgroundColor","red");
//简写方式
 $("#dv").html("<p>这是一个p</p>").css("backgroundColor","red");
```

注意：如果获取一个标签的值，那么就不能用链式编程，因为会返回一个字符串。$('#dv').html().css()就是错误的

### 1.列表鼠标移入排它

```js
$("#uu>li").mouseover(function () {
    $(this).css("backgroundColor","red").siblings("li").css("backgroundColor","");
}).click(function () {
    $(this).css("fontSize","50px").css("color","green").css("fontFamily","全新硬笔行书简");
});
```

### 2.按钮连续操作练习

```js
 $("#btn").click(function () {
     $(this).val("改变了");
 }).mouseover(function () {
     $(this).css({"width":"200px","height":"100px"});
 }).mouseout(function () {
     $(this).css("backgroundColor","green");
 });
```



## 4.兄弟元素操作

```
next()  下一个兄弟
nextAll() 后面所有兄弟
prev()   上一个兄弟
prevAll() 上面所有兄弟
siblings() 除自己以外的所有兄弟
```



### 1.啤酒案例练习

```js
$("ul>li").mouseenter(function () {
    $(this).css("backgroundColor","red").siblings().css("backgroundColor","");
}).mouseleave(function () {
    $(this).css("backgroundColor","").siblings().css("backgroundColor","");
}).click(function () {                
    $(this).prevAll().css("backgroundColor","yellow").end().nextAll().css("backgroundColor","blue");
});
```

## 5.常见动画方法

```js
show()  显示
hide()  隐藏   本质上还是display:block和none
slideUp() 上滑
slideDown() 下滑
slideToggle()  上下滑
fadeIn()  淡入
fadeOut() 淡出
fadeToggle() 淡入淡出
fadeTo(事件，透明度)    透明度动画


参数1： 
	1.可以写毫秒，1000毫秒
	2.可以写字符串 slow normal fast
$("#dv").hide(1000);
$("#dv").show("fast");

参数2： 是一个回调函数，可以在动画执行后触发

$('#dv').hide(1000,function(){
    alert('动画结束了')；
})
```

### 1.递归显示隐藏动画

```js
  $("#btn1").click(function () {
      //获取div,最后一个图片,隐藏
      $("div>img").last("img").hide(800,function () {
          //arguments.callee相当于递归
          $(this).prev().hide(800,arguments.callee);
      });
  });
//显示
$("#btn2").click(function () {
    $("div>img").first("img").show(800,function () {
        //arguments.callee相当于递归
        $(this).next().show(800,arguments.callee);
    });
});
```

### 2.点击隐藏删除操作

```js
$("div").click(function () {
    $(this).hide(800,function () {
        $(this).remove();
    });
});
```



## 6.animate动画方法

```js
animate(属性，时间，回调函数);
属性的变化和时间是必须的，回调函数可以没有。

animate({"属性名"："属性值"},1000)
注意： animate属性不能修改非数值效果，例如颜色。

stop()   动画停止函数（内部原理停止上一个定时器）；
建议: 在每次添加动画之前都加上stop(),直接显示隐藏动画除外
```

### 1.二级菜单

```js
$(".wrap>ul>li").mouseover(function () {
    //鼠标进入
    $(this).children("ul").stop().show(500);//显示
});
$(".wrap>ul>li").mouseout(function () {
    //鼠标离开
    $(this).children("ul").stop().hide(500);//显示
});
```



## 7.元素创建

```js
直接使用$('标签') 就可以创建一个标签对象。
append()  追加元素
prepend() 插入某个元素前面

after()  在后面添加元素
before() 在前面添加元素

appendTo()  把当前标签添加到其他标签中去

```

```js
//创建元素
var aObj=$("<a href='http://www.baidu.com'>百度"+i+"</a>");
//把元素添加到div中
$("#dv").append(aObj);//把超链接追加到div中

//把元素插入到某个元素的前面
$("#dv").prepend(aObj);
//把元素添加到当前元素的后面(兄弟元素来添加)
$("#dv").after(aObj);
//把元素添加到当前元素的前面(兄弟元素来添加)
$("#dv").before(aObj);
```

注意：append追加元素，可以把已经存在的元素移除，类似于剪切效果

### 1.权限选择案例

```js
获取第一个下拉框中被选中的option添加到第二个下拉框
$("#toRight").click(function () {
    $("#se2").append($("#se1>option:selected"));
});

//第二个按钮
$("#toLeft").click(function () {
    $("#se1").append($("#se2>option:selected"));
});
//第三个按钮
$("#toAllRight").click(function () {
    $("#se2").append($("#se1>option"));
});
//第四个按钮
$("#toAllLeft").click(function () {
    $("#se1").append($("#se2>option"));
});
```

### 2.appendTo添加元素

```js
$("#btn").click(function () {
    //创建p标签
    var pObj= $("<p></p>");
    pObj.text("哈哈哈,我又变帅了");
    //$("#dv").append(pObj);
    //把pObj对象主动的加到div中
    pObj.appendTo($("#dv"));
});
```

### 3.html()添加元素

```js
$("#btn").click(function () {
    $("#dv").html("<p>这是一个p标签</p>");
});
```



### 4.动态创建表格

```

```

```js
   $("#btnCreate").click(function () {
       var arr=[];
       //遍历数组
       for(var i=0;i<datas.length;i++){
           var obj=datas[i];//数组中的每一个对象
           //创建行和列,加入到tbody中
           arr.push("<tr><td><a href="+obj.url+">"+obj.name+"</a></td><td>"+obj.type+"</td></tr>");
       }
       $("#tbd").html(arr);
   });
```

```js
//另外一种方法
for(var i=0;i<datas.length;i++){
    var obj=datas[i];//数组中的每一个对象
    //创建行和列,加入到tbody中
    $("<tr><td><a href="+obj.url+">"+obj.name+"</a></td><td>"+obj.type+"</td></tr>").appendTo($("#tbd"));
}
```

## 8.清空内容和克隆节点

```js
html('') //清空内容
empty()  //清空内容
remove()  移除元素

clone()  克隆元素

children() 子元素
```



## 9.表单属性获取和设置

```js
val()  可以获取和设置表单的value值
```

注意; 设置下拉框的value值可以让下拉框某一项选中，前提是option上有value值



## 10.自定义属性

```
attr()  设置和获取自定义属性
设置自定义属性
attr('ss','1');
获取自定义属性
attr('ss')
注意： attr不能获得多选框的选中值checked属性

prop()  //该方法可以获取多选框的checked属性
```

### 1.复选框选中属性操作

```
//复选框选中案例
//获取选中状态
 var flag=$("#ck").prop("checked");
if(flag){
    //选中了
    $("#ck").prop("checked",false);
}else{
    //没有选中
    $("#ck").prop("checked",true);
}
```

### 2.全选全不选，是否全选

```js
 //获取第一个按钮,点击---全选
$("#btnAll").click(function () {
    $("#dv :checkbox").prop("checked",true);
});
//获取第二个按钮,点击---全不选
$("#btnNoAll").click(function () {
    $("#dv :checkbox").prop("checked",false);
});


```

```js
 $("#j_cbAll").click(function () {
     var cked=$(this).prop("checked");//保存当前复选框的选中状态
     //获取tbody中所有的复选框
     $("#j_tb").find(":checkbox").prop("checked",cked);
 });

//获取tbody中所有的复选框
$("#j_tb").find(":checkbox").click(function () {
    //先获取tbody中所有的复选框的个数
    var length1=$("#j_tb").find(":checkbox").length;
    //再获取tbody中所有选中的复选框的个数
    var length2=$("#j_tb").find(":checked").length;
    //二者比较,如果相同,让最上面的复选框选中,否则不选中
    if(length1==length2){
        //都选中了
        $("#j_cbAll").prop("checked",true);
    }else{
        //有没选中
        $("#j_cbAll").prop("checked",false);
    }
});
```



## 11.设置和获取元素宽高

```js
width()   //获取和设置宽度
height()  //获取和设置高度
$("#dv").css("width")   //获取宽度，返回字符串 100px，可以使用parsetInt转换为数字

$('#dv').width(100);    //直接设置元素宽度为100，不需要带px

总结： 通过css设置和获取宽高，需要带px单位，使用width()方法可以不用带px单位。

```



## 12.获取元素的位置操作

```js
offset() 方法可以获得 left和top值，都是数字，不带单位
offset().left  //left值
offset().top


//获取left和top的值--->都是数字类型
console.log($("#dv").offset().left);
console.log($("#dv").offset().top);

//设置left和top值
$("#dv").offset({"left":200,"top":200});
```

## 13.页面滚动距离

```js
scrollLeft()  滚动出去的左边距离
scrollTop()   滚动出去的顶部距离

$(document).click(function () {
    //获取的滚动出去的距离----->数字类型
    console.log($(this).scrollLeft()+"===="+$(this).scrollTop());
});
```



## 14.今日总结