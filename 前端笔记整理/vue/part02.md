- 1. 1.动画

- 动画能够提高用户的体验,帮助用户更好的理解页面中的功能

- 1. 使用transition元素,把需要被动画控制的元素,包裹起来

  2. 自定义两组样式,来控制transition内部的元素实现动画

  3. 1. v-enter 是进入之前,元素的起始状态,此时还没有开始进入
     2. v-enter-active 入场动画的时间段
     3. v-leave-active 离场动画的时间段
     4. v-leave-to 是动画离开后的终止状态,此时动画已经结束

  4. 钩子函数:

  5. 1. beforeEnter(el) 表示动画入场之前,此时,动画尚未开始,可以在其中,设置元素的起始位置和样式,el 表示要执行动画的那个DOM元素,是原生JS的DOM对象
     2. enter(el,done) 动画开始之后的样式,可以设置完成动画之后的,结束状态,加上el.offsetWidth,强制刷新页面,done(       ) 
     3. afterEnter(el) 动画完成后执行

  6. 列表动画

- 需要使用transition-group标签进行包裹

- 1. 组件化开发

  2. 1. 组件化 / 模块化

     2. 创建组件

     3. 1. 使用Vue.extend来创建全局的Vue组件

- var com1 = Vue.extend({

- template: ' <h3>Hello</h3>'

- })

-  

- 1. 注册组件

- Vue.component('com',com)