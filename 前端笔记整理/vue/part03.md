- 1. 1.组件

  2. - data :       组件有自己的data,必须是一个方法,返回一个对象

     - 组件的切换 : 

     - - v-if 
       - component        展示对应名称的组件,是一个占位符, :is属性,可以用来指定要展示的组件的名称
       - 切换动画 : 用transition包裹组件,使用mode属性设置组件切换时的模式,mode="out-in"

     - 组件传值 : 

     - - 父向子传值 : 属性绑定的形式        :parentmsg="msg" ,同时在子组件中注册 props : [ 'parentmsg' ]        ,props中的数据都是通过父组件传递给子组件的,是单向下行绑定的,就是为了避免,子组件中修改数据导致父组件或者其他子组件数据同时篡改
       - 子向父传值 : 自定义事件 @func="show(data)",show为父元素方法,在子组件中方法        myclick ( ) { this . $emit ( ' func ' , data ) },子组件中@click="myclick"

  3. 2.ref 获取DOM对象

- 给元素添加ref属性,可以在实例身上$refs获取DOM对象

- 1. 3.路由

  2. - 前端路由: 通过URL中的hash(#号)实现