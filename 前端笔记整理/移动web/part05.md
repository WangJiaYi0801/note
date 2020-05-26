- 1. 1.响应式开发

  2. 1. 网页布局方式

     2. 1. 固定宽度布局
        2. 流式布局
        3. 栅格化布局
        4. 响应式布局

     3. 响应式布局:

     4. 1. 屏幕大小不一样,看到的网页不一样
        2. 一个页面可适应不同屏幕,但代码多,加载慢

-  

- 1. 2.媒体查询

  2. 1. 通过查询当前屏幕的宽度,针对不同的屏幕宽度设置不同的样式来适应不同屏幕

     2. 实现方式

     3. 1. 媒体类型mediatype的值:all / print /        speech / screen

- body {

- background-color: red;

- }

- @media screen and (min-width:768px) {

- body {

- background-color: blue;

- }

- }

- @media screen and (min-width:992px) {

- body {

- background-color: green;

- }

- }

-  

- 1. not : 不在范围之内的取值

- body {

- background-color: red;

- }

- @media not screen and (min-width:768px) and (max-width:992px) {

- body {

- background-color: pink;

- }

- }

-  

- 1. min-width:在pc端和移动端都能响应,效果一致,是视口的宽度
  2. min-device-width: 只能在移动端响应,是设备的宽度

- 1. 改变调用的文件

  2. 1. 在宽大于992px时,调用a.css文件

- <link rel="stylesheet" media="screen and (min-width:992px)" href="a.css">

-  

-  

- 1. 3.bootstrap

  2. 1. 兼容性处理: cc:ie6 在VScode中不生效

     2. 布局容器: container(width变化) /        container-fluid(width100%)

     3. 1. w>1200      :  1170
        2. 1200>w>992 :         970
        3. 992>w>768  :          750
        4. W<768       :  100%

     4. 栅格系统: 

     5. 1.  ![01-栅格系统](/Users/jiayiwang/Downloads/01-栅格系统.png)

        2. col-xs-4: 类名,设置当前元素在xs屏幕12等分中,占4等分

        3. 有宽度,浮动,定位

        4. offset:偏移 

        5. 1. col-xs-offset-2         :向右偏移两格,但是这种偏移会影响后面的元素
           2. 它是通过margin-right做

        6. push 往后推 / pull 往前拉

        7. 1. col-xs-push-2 :向右偏移两格
           2. 通过定位来实现的,不会影响其他元素,可能重合  

     6. 1. 嵌套列时,不加container,嵌入row
        2. 设置隐藏: hidden-sm 只控制一个屏幕范围,不向上兼容 

-  

- 1. 4.less

  2. 1.  注释:

     2. 1. //   在less.css中看不到
        2. /* */ 在less.css中看得到

     3. 变量: @变量名:值;

- @aa:red;

-  

- .box{

- background-color: @aa;

- }

- 1. 混入: 可以将一个样式引入到另外一个样式中

  2. 1. .add{

- border-radius: 20px;

- }

- .box{

- height: 100px;

- .add;

- }

-  

- 1. .add(@aa){

- color:@aa;

- }

- .box{

- .add(green);

- }

-  

- 1. .add(@aa:10px){

- width: @aa;

- }

- .box{

- .add(5px);

- }

- .add中不传值时.默认为10px,若传值,则为所传的值

-  

- 1. 嵌套:可以层层嵌套,&表示本身

- .header{

- width: 100%;

- height: 200px;

- \> div{

- &::before{

- content: "";

- }

- width: 100%;

- \> a{

- text-decoration: none;

- &:hover{

- color: red;

- }

- }

- \>h3{

- line-height: 30px;

- }

- }

- }

-  

- 1. 导入:

- @import "foo.less";

-  

- 1. 5.rem

  2. 1. em: 长度单位,参照当前元素的字号,如果没有设置,则参照父元素或是浏览器默认字号
     2. rem: 是css3新增元素,参照根元素html的字号

-  

-  

-  

-  