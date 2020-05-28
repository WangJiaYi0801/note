- 1. 1.模板字符串

  2. 1. `这是${str}`

     2. 'sedfgh'.startsWith('se')       判断是否是以一段字符开始,返回真假  .endWith 判断结尾

     3. caniuse.com 测试兼容性的网站

     4. promise

     5. 1. 是一个构造函数

        2. 1. 需要new Promise去创建一个Promise对象
           2. 在new         Promise(函数)这个函数有两个参数,resolve(成功)和reject(失败)

        3. promise对象上有.then(        ) 还有.catch( )

        4. 1. then接受两个参数,一个是成功的回调和失败的回调

        5. 为什么要使用promise

        6. 1. 解决嵌套地狱问题

        7. 结论:

        8. 1. 在then中可以分别传递成功和失败回调函数给resolve和reject

        9. 用函数封装promise

- ` `