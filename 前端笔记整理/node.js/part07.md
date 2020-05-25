- 1. 1.session

  2. - 在服务器内存中存放客户端私有的数据,每个客户端cookie中存放地址

     - 在express中使用session

     - - 安装express-session
       - 导入session模块
       - 使用session中间件
       - 将私有数据保存到当前请求的session中
       - 通过destroy( )方法清除session

  3. 2.抽取公共模块

  4. - <% -  include(' ../layout/header.ejs ')       %>

  5. 3.富文本编辑器mditor