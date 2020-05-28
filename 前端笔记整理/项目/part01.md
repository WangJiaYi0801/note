- 1. 开发过程:

  2. 1. 需求分析
     2. 原型设计
     3. UI设计
     4. 技术选择
     5. 数据库设计
     6. 项目架构设计
     7. 业务迭代开发
     8. 集中测试
     9. 部署上线

- 1. 修改文件夹时,代码中路径可用查找功能批量删除

- 1. 批量修改文件后缀名可用cmd

-   cmd拓展:[命令行](onenote:其他.one#命令行&section-id={A884573A-E4CE-4A6D-8986-A86DDACD5AFF}&page-id={14B6BD8F-0B27-4A38-B94D-4C874D11D12A}&object-id={03057D77-E4E0-4BB6-A19E-107BD4630F6B}&10&base-path=https://d.docs.live.net/3528662b6d64c4fe/文档/嘉怡 的笔记本)

- 1. 查询语句:

  2. 1. **查询**:SELECT 类名 FROM 表名

- SELECT name,title,created,content

- FROM posts

- 1. 取别名: 原名 AS 简洁名
  2. 两表联查: 主表 LEFTJOIN 附表 ON      两表关联变量等式

- SELECT name,title,created,content

- FROM posts p

- LEFT JOIN categories c ON p.category_id=c.id

- 1. 三表联查:同上再加上一个表
  2. 附条件: WHERE 条件
  3. 加排序: 

- ORDER BY p.created DESC

- 按p.created进行排序,加DESC为降序排序,不加默认为升序排序

- 1. 限制结果条数:

- LIMIT 0 , 5

- 只要结果的0 ~5条

- 1. 统计结果数量:

- SELECT COUNT(*) AS count FROM categories

- 1. **增加**:INSERT INTO 表名 键      VALUES 值 

- INSERT INTO table key VALUES value

- 1. **修改**:UPDATE 表名      SET 键=值,键=值 

- UPDATE categories SET name = 'name',classname = 'classname' 

- 1. **删除**:DELETE FROM 表名

- DELETE FROM categories

- 1. ajax请求数据: 

- $.ajax({

- type:'post',

- url:'./api/getMorePost.php',

- data:{

- categoryId:categoryId,

- currentPage:currentPage,

- pageSize:5

- },

- success:**function**(res){

- if(res.code==1){

- **var** data=res.data;

- $.each(data,**function**(index,val){

- **var** str='';

- **var** entry=$(str);

- entry.insertBefore('.loadmore');

- })

- }

- }

- })

-  

- 1. 从数据库获取数据的过程:

- $connect = mysqli_connect(DB_HOST,DB_USER,DB_PWD,DB_NAME);

- $sql = " ";

- $result = mysqli_query($connect,$sql);

- $arr = [];

- while($row=mysqli_fetch_assoc($result)){

- $arr[]=$row;

- }

- $response = ['code'=>0,'msg'=>'操作失败'];

-  

- if($arr){

- $response['code']=1;

- $response['msg']='操作成功';

- $response['data']=$arr;

- }

-  

- header('Content-Type:application/json;charset=utf-8');

- echo json_encode($response);

-  

- 1. 登录功能:

  2. 1. 登录成功设置session;
     2. 在每个页面检测是否有session,进行登录验证,验证失败则跳转登录页面;
     3. 每次使用session都要先session_start( );
     4. 退出登录时,用unset清除session

-  

- 1. 抽取公共模块:

  2. 1. 页面中的公共部分,导航栏等需要抽取出来;
     2. 再用<?php       include_once 'public/_header.php';       ?>写入页面;

  3. 1. 当其动态改变时,所有页面均会改变

-  

- 1. jquery使用的函数:

  2. 1. 收集表单数据: $('#data').serialize()

     2. 1. 会自动收集有name属性的表单元素的值,生成key=value&key=value样式的值,可直接作为ajax的data数据传递

     3. 1. 去除前后空格: $.trim($('#name').val())
        2. 获取自定义属性的值: current_row.attr('data-categoryId')

-  

- 1. php使用的函数:

  2. 1. $_POST是数组,装着所有以post方式传递过来的数据

  3. 1. **array_keys($_POST)**是post中所有键的数组

  4. 1. **array_values($_POST)**是post中所有值的数组
     2. **implode( ' , ' , array )**将数组里的元素以逗号连接起来
     3. **substr( $sql , 0 , -1 )**将字符串最后一个元素去掉

-  

- 1. 给动态生成的元素添加事件时,不能直接加在自己身上,用事件委托,加在父元素上

- $('tbody').on('click','.edi',**function**(){ })

-  

- 1. 将获取的英文数据转为中文描述时,可用数组

- **var** statusObj = {

- 'drafted':'草稿',

- 'published':'已发布',

- 'trashed':'已作废'

- };

- 1. art-template使用

  2. 1. 引入template.js文件
     2. 创建要动态生成的结构模板
     3. 使用template(id,object)方法生成结构
     4. 将生成的结构插入指定的位置

-  

-  

- 1. 分页按钮

- 1. 文件上传

  2. 1. 标签为<input       id="feature" name="feature"       type="file">

  3. 1. 找到文件上传的按钮,添加change事件(当内容改变时执行)

     2. 获取文件: **var** file =       this.files[0];

     3. ajax上传post请求:

     4. 1. ajax无法直接上传文件,需要FromData配合:

- **var** data = new FormData();

- data.append('file',file);

- 1. 还需要设置ajax中的两个参数:

- contentType:false 允许jquery把文件带回服务器

- processData:false 告诉jquery不要序列化我们的文件

- 1. 在端口文件中用$_FILE[ ' file ' ]获取文件

- 生成不会重复的文件名,加时间戳+随机数+后缀名:

- $fileName = time().rand(00000,99999).strrchr($file['name'],'.');

- 再将文件从临时地址移动到指定地址

- move_uploaded_file($file['tmp_name'],'../../static/uploads/'.$fileName);

-  

- 1. 富文本插件:有格式的文本

-  

- 插件 -- CKEditor 4

- 1. 使用插件的步骤:

  2. 1. 引入插件
     2. 准备 文本域,需要id
     3. 调用插件方法,初始化富文本编辑器

- CKEDITOR.replace(content);

- 1. 获取富文本内容

- 在收集数据之前,需要将富文本的内容更新到文本域中:

- CKEDITOR.instances.content.updateElement();

-  

- 1. each方法

  2. 1. dom

     2. 1. for(**var** i=0;i<arr.length;i++){

- console.log(arr[i]);

- }

-  

- 1. arr.forEach(**function**(item,index){

- console.log(item,"forEach");

- }

-  

- 1. jquery

  2. 1. $.each(arr,**function**(index,item){

- console.log(item,"each");

- }

-  

- 1. $("li").each(**function**(index,item){

- console.log(item,"each");

- }

-  

- 1. 表单关联

- input标签在form表单外面,进行关联,可一同传输数据

-  

-  

-  