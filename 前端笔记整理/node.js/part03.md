- 1. 1.nodemon工具自动重启服务器

  2. 2.express框架

  3. 1. 构建基本的express服务器

     2. - 导入express第三方模块
        - 创建服务器的实例: const app =        express( )
        - 通过app.get( )监听客户端的请求,并指定要坚挺的URL地址和处理函数        app.get('/',(req,res)=>{res.end( )}
        - 调用app.listen( )方法启动express服务器

     3. 快捷方法:

     4. 1. res.send( ) 可发送文本,中文,数组,对象
        2. res.sendFile( ) 发送文件,静态页面

     5. 使用express.static( )静态资源托管

     6. 1. app.use( )的作用,就是注册中间件

     7. 为express框架配置模板引擎渲染动态页面

     8. 1. 使用app.set('view        engine','ejs')
        2. 设置模板页面的默认存放路径app.set('views','模板页面的具体存放路径')
        3. 注意:调用res.render函数来渲染页面,必须先配置模板引擎

-  

- 1. 使用express框架中提供的路由来分发请求

-  

-  