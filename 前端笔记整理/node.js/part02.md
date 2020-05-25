- 1. 1.模块化

  2. 1.  CommonJS规范: 

- require(引入模块) modules(模块标识) exports(暴露成员)

- 1. 模块作用域和全局作用域

  2. 1. 每个js文件,都是独立模块,有独立作用域,外界在require这个文件时,默认无法访问js文件中的私有成员
     2. global.b=b使其变为全局作用域

  3. module.exports 与 exports 的异同

  4. 1. 他们引用同一个空对象
     2. 以module.exports的指向为准

-  

- 1. 2.node.js中的模块和包

  2. 1. 模块成员分类:核心模块,第三方模块,用户自定义模块

-  

- 1. 3.npm

  2. 1. 含义:

     2. 1. https://www.npmjs.com/
        2. node的包管理工具Node package        manager

     3. 安装和卸载全局的包(i5ting_toc)

     4. 1. npm install 包名 -g
        2. npm uninstall 包名 -g
        3. 地址:c:\Users\用户目录\AppData\Roaming\

     5. 安装卸载本地的包

     6. 1. npm init -y 初始化包配置文件
        2. npm install jquery        -S 下载包 (--save) 安装包到本地开发环境中
        3. npm install 下载package.json中记录了但是没有的包
        4. npm uninstall        jquery -S 卸载
        5. --save-dev(-D) 安装到测试环境

-  

- 1. 4.实现一个类似于Apache的静态资源服务器

  2. 1. 导入http核心模块

- `const http = rquire('http')`

- 1. 调用http.createServer方法,创建一个web服务器对象

- `const server = http.createServer()`

- 1. 为server服务器绑定监听函数,通过on方法,绑定request事件,来监听客户端的请求,设置请求头,显示中文

- `server.on('request',function(req,res){`

- `res.writeHeader(200,{`

- `'Content-Type':'text/html;charset=utf8'`

- `})`

- `res.end('Hello 世界')`

- `}`

- 1. server.listen来启动服务器

- `server.listen(3000,'www.klxin.dev',function(){`

- `console.log('server running at http://127.0.0.1:3000')`

- `})`