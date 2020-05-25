- 1. 1.基础知识

-  

- 1. node.js中js的组成部分: ECMAScript核心+全局成员+核心API模块

  2. 1. 全局成员:console ,       setInterval , setTimeout…
     2. 核心API模块:就是node平台独特提供的一些API,这些API是node所独有的
     3. 没有DOM和BOM

-  

- 1. node命令

  2. 1. node -v 查看版本
     2. node 文件路径 执行文件
     3. "↑"获得上一条命令
     4. "tab"键自动补全路径
     5. windows中,"cls"可以清屏

-  

- 1. REPL环境(了解):

  2. 1. 进入REPL环境:终端中,直接输入node回车
     2. R:read
     3. E:evaluate
     4. P:print
     5. L:loop

-  

- 1. 2.ES6语法:

-  

- 1. 使用var定义变量

  2. 1. 使用var 定义的变量存在变量提升问题
     2. 没有块级作用域

-  

- 1. 使用let定义变量

  2. 1. 需要先定义,后使用,不存在变量提升
     2. 有块级作用域

-  

- 1. const

  2. 1. 先定义,后使用,不存在变量提升
     2. const定义的常量不许再次赋值
     3. 有块级作用域

-  

- 1. 结构赋值

  2. 1. var        {className:aa,desc)=obj

- ` `

- 1. 箭头函数

  2. 1. (形参)=>{函数体代码}
     2. var fn = (形参)=>{函数体代码}
     3. 箭头函数内部的this,指向函数外面的this

-  

- 1. 对象中定义属性和方法的快捷方式

  2. 1. var person =        {

- `name,`

- `age,`

- `show,`

- `say( ) {`

- `console.log('ok')`

- `}`

- `}`

- ` `

- 1. 文件系统

  2. 1. 引入js--只要你安装了node,那么node提供的api都可以使用require获取

- `const fs  = require( ' fs ' )`

- ` `

- 1. 使用readFile方法读取数据

- `fs.readFile('./files/1.txt',(err,data)=>{`

- `//获取的数据为Buffer,加上空字符串,转换为正常数据`

- `console.log(data + ' ');`

- `})`

- `或者加上第二个参数'utf8'`

- `fs.readFile('./files/1.txt','utf8',(err.data)=>{ })`

- `如果文件读取出错,那么err就是一个错误对象`

- `如果文件没有出错,那么err就是null`

- ` `

- 1. 使用writeFile方法写入文件

- `fs.writeFile('./files/5.txt','message',(err)=>{`

- `if(err) return console.log('文件写入失败')`

- `console.log('文件写入成功')`

- `})`

- ` `

- 1. 追加文件appendFile

- `fs.appendFile('./5.txt','message',(err)=>{})`

- ` `

- 1. 复制文件copyFile

- `fs.copyFile('./5.txt','./5-copy.txt',(err)=>{})`

- ` `

- 1. 文件方法中sync的说明: fs.readFileSync同步请求

-  

- 1. 路径问题: 文件需使用绝对路径 __dirname + '/1.txt'

-  

- 1. 读取文件信息fs.stats

- `fs.stats('./1.txt',(err,stats)=>{`

- `if(err) return console.log(err.message)`

- `console.log(stats.size) //单位是 字节 Byte`

- `console.log(stats.birthtime) //文件创建时间`

- `console.log(stats.isFile())//判断是否为文件`

- `console.log(stats.isDirectoty())//判断是否为目录`

- `})`

- ` `

- 1. Path

  2. 1. 引入

- `const path = require('path')`

- 1. 路径

- `path.join(__dirname,'./1.txt')`