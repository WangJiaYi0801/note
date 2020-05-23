## **ajax**

- 定义：Ajax(Asynchronous Java and XML的缩写)是一种异步请求数据的web开发技术，在不需要重新刷新页面的情况下，Ajax 通过异步请求加载后台数据，并在网页上呈现出来。

- 作用：提高用户体验，减少网络数据的传输量

https://www.cnblogs.com/qing-5/p/11368009.html

原生JS实现ajax请求

```js
<script>
    function ajax(options){
        options = options ||{};  //调用函数时如果options没有指定，就给它赋值{},一个空的Object
        options.type=(options.type || "GET").    ();/// 请求格式GET、POST，默认为GET
        options.dataType=options.dataType || "json";    //响应数据格式，默认json

        var params=formatParams(options.data);//options.data请求的数据

        var xhr;

        //考虑兼容性
        if(window.XMLHttpRequest){
            xhr=new XMLHttpRequest();
        }else if(window.ActiveObject){//兼容IE6以下版本
            xhr=new ActiveXobject('Microsoft.XMLHTTP');
        }

        //启动并发送一个请求
        if(options.type=="GET"){
            xhr.open("GET",options.url+"?"+params,true);
            xhr.send(null);
        }else if(options.type=="POST"){
            xhr.open("post",options.url,true);

            //设置表单提交时的内容类型
            //Content-type数据请求的格式
            xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
            xhr.send(params);
        }

    //    设置有效时间
        setTimeout(function(){
            if(xhr.readySate!=4){
                xhr.abort();
            }
        },options.timeout)

    //    接收
    //     options.success成功之后的回调函数  options.error失败后的回调函数
    //xhr.responseText,xhr.responseXML  获得字符串形式的响应数据或者XML形式的响应数据
        xhr.onreadystatechange=function(){
            if(xhr.readyState==4){
                var status=xhr.status;
                if(status>=200&& status<300 || status==304){
                  options.success&&options.success(xhr.responseText,xhr.responseXML);
                }else{
                    options.error&&options.error(status);
                }
            }
        }
    }

    //格式化请求参数
    function formatParams(data){
        var arr=[];
        for(var name in data){
            arr.push(encodeURIComponent(name)+"="+encodeURIComponent(data[name]));
        }
        arr.push(("v="+Math.random()).replace(".",""));
        return arr.join("&");

    }
    //基本的使用实例
    ajax({
        url:"http://server-name/login",
        type:'post',
        data:{
            username:'username',
            password:'password'
        },
        dataType:'json',
        timeout:10000,
        contentType:"application/json",
        success:function(data){
　　　　　　。。。。。。//服务器返回响应，根据响应结果，分析是否登录成功
        },
        //异常处理
        error:function(e){
            console.log(e);
        }
    })
</script>
```



## **promise**

```jsx
Promise对象可以理解为一次执行的异步操作，使用promise对象之后可以使用一种链式调用的方式来组织代码；让代码更加的直观。
```



https://www.jianshu.com/p/1ec8d1c4e287



比如我们在工作中经常会碰到这么一个需求，比如我使用ajax发一个A请求后，成功后拿到数据，我们需要把数据传给B请求；那么我们需要如下编写代码：

```js
$.ajax({
      url: '',
      dataType:'json',
      success: function(data) { // 获取data数据 传给下一个请求
          var id = data.id;
          $.ajax({
              url:'',
              data:{"id":id},
              success:function(){ // .....
 }
          });
      }
});
```

缺点：

1. 后一个请求需要依赖于前一个请求成功后，将数据往下传递，会导致多个ajax请求嵌套的情况，代码不够直观。

 2. 如果前后两个请求不需要传递参数的情况下，那么后一个请求也需要前一个请求成功后再执行下一步操作，这种情况下，那么也需要如上编写代码，导致代码不够直观。



为了防止请求一层一层嵌套,就可以使用promise使其呈一种链式结构.



### 如何使用promise



创建promise对象

第一种方式:new一个promise

```jsx
var promise = new Promise(function(resolve,reject){
    // 异步处理
    // 成功调用resolve 往下传递参数 且只接受一个参数
    // 失败调用reject  往下传递参数 且只接受一个参数
});
```



