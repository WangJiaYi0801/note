- 1. 1.Vue的基本使用

  2. - 引入vue.js文件
     - 通过Vue的构造函数,创建实例
     - 创建实例时,可以传入一个配置对象,el,data.methods
     - 创建后,在实例托管的范围内,就可以使用模板语法引用data中的数据

-  

- 1. 指令

  2. 1. 插值表达式(只能写在标签内部) : {{ }} /       v-text / v-html
     2. v-bind       : 是用于绑定属性的指令,还可以绑定自定义属性,可简写为       " : "
     3. v-on :       用于绑定事件 , 简写为 " @ "

- <input  v-on:keydown="fn" />

- 1. 事件修饰符:

- .stop  阻止冒泡

- .prevent  阻止默认行为

- .capture  添加事件侦听器时使用事件捕获模式

- .self  只有点击当前元素时,才会触发事件处理函数 

- .once  只触发一次事件

- 1. v-model : 实现数据的双向绑定,只能绑定value属性
  2. 样式操作:

- 内联样式: <div :class="['red,'blue']"可以使用三元表达式

- 行内样式: <div :style="[style01,style02]"

- 1. v-for : 默认就地复用,使用key进行绑定,可为number或string
  2. v-if /      v-show : v-if每次都会重新蛇女胡或创建元素,有较高的切换性能消耗,而v-show只是切换了元素的display:none样式,有较高的初始渲染性能消耗
  3. 按键修饰符 @keyup.enter=" "

- 1. 过滤器

-  

- 1. 生命周期函数 -- Vue实例创建的过程中,从出生到死亡每个阶段所执行的函数

  2. 1. 创建期间

     2. - beforeCreate( ) 实例完全被创建出来之前,会执行它
        - created( ) 实例已经创建完毕,可以访问,data和methods已经初始化
        - beforeMount( ) 模板已经在内存中编译好可,但是尚未挂载到页面中,显示的还是旧页面
        - mounted( ) 模板挂载到页面中,用户可以看到渲染好的页面,此时DOM元素也是最新的,如果想操作DOM元素,最好在这个生命周期函数中进行,当执行完mounted就表示,实例已经完全创建好了,如果没有其他操作

     3. 运行期间

     4. - beforeUpdate( ) 数据改变了,但是页面还没有被更新
        - updated( ) 页面和数据保持一致,为最新

     5. 销毁期间

     6. - beforeDestroy(        ) 实例身上的所有data和methods等还处于可用状态,还没有真正执行销毁的过程
        - destroyed(        ) 实例完全销毁了

  3. vue-resourse      实现get,post,jsonp请求 http://vue.lovegf.cn:8899

- this . $http . get( url , [option] ) . then( success , error )

- this . $http . post( url , [body] , [options] ) . then( success , error )