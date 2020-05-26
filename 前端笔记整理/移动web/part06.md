# 微金所页面的制作:

 

1. 1.结构

2. 1. 头部块 .wjs_header
   2. 导航条 .wjs_nav
   3. 轮播图 .wjs_banner
   4. 信息块 .wjs_info
   5. 预约块 .wjs_revese
   6. 产品块 .wjs_product
   7. 新闻块 .wjs_news
   8. 合作伙伴 .wjs_partner

 

1. 2.准备

2. 1. 字体图标--自定义字体
   2. 引入bootstrap模板,jquery文件

 

1. 3.头部制作--栅格布局 

2. 1. container      > row > 2 : 5 : 2 : 3
   2. 从md开始写, 结构hidden-xs ,sm,小屏隐藏
   3. 字体图标:可用第三方,也可用bootstrap自带图标
   4. 用less写css样式,将通用的红色设为变量
   5. 按钮使用bootstrap按钮样式,修改时检查属性,有的放矢

 

1. 4.导航条--组件

2. 1. 用子元素撑开导航条,不直接修改高度
   2. 改样式单独修改,不可改动源文件
   3. 修改样式会受源文件默认样式的影响,需要检查分析

 

1. 5.轮播图

2. 1. 小于768 即 移动端,图片随屏幕一同缩小,自适应,通过img100%来实现

   2. 大于768 时,图片定在中间,左右变长,图片是背景图

   3. 1. background-image       : url( ) ;
      2. background-position : center       center ;
      3. background-size : cover ;

   4. 使用bootstrap插件

   5. 为了避免加载过多的资源,使用js动态创建子元素

   6. 1. 获取所有items

      2. 监听屏幕的大小改变

      3. 1. 获取屏幕宽度

         2. 判断屏幕>768? 非移动端

         3. 1. 添加子元素,$.each遍历
            2. 给item设置属性存储图片地址,遍历时获取地址
            3. 先设置a标签元素,再设置属性,.html( )方法中路径无法解析出来

         4. 判断屏幕<768? 移动端

 

 

 

 