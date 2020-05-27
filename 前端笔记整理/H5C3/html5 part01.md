- ##  

- 1. 语义标签(类似于div)

-  

- | nav     | 导航             |
  | ------- | ---------------- |
  | header  | 页眉             |
  | main    | 文档主要内容     |
  | aside   | 主体内容之外     |
  | article | 文章             |
  | footer  | 文档或者页的页脚 |

-  

- 语义标签的兼容性:

- IE9:行级元素在设置宽度的时候是失效的

- 处理方法:

- 将行级元素转换为块级标签:display:block;

- IE8:无法识别语义标签

- 处理方法:

- 1.手动创建标签

- 2.引入第三方插件html5shiv.min.js

-  

- 1. 表单新增的type属性

-  

- | 用途     | type           | 注释                                                         |
  | -------- | -------------- | ------------------------------------------------------------ |
  | 用户名   | text           |                                                              |
  | 密码     | password       |                                                              |
  | 邮箱     | email          | 提供了默认电子邮箱的完整验证:要求必须包含@符号和服务器名称,不满足不能提交 |
  | 电话号码 | tel            | 并不是来实现验证,本质目的是为了能够在移动端打开数字键盘,限制用户只能输入数字 |
  | 网址     | url            | 验证只能输入合法的网址,必须包含http://                       |
  | 数量     | number         | 只能输入数字和小数点,有最大值max最小值min,默认取值value,有上下箭头可点击 |
  | 搜索框   | search         | 提供更人性化的输入体验,有删除键                              |
  | 范围     | range          | max min   value                                              |
  | 颜色     | color          |                                                              |
  | 时间     | time           |                                                              |
  | 日期     | date           | 年月日                                                       |
  | 日期时间 | datetime       | 大多数不能支持,只能苹果safari支持                            |
  | 日期时间 | datetime-local | 年月日 时间                                                  |
  | 月份     | month          |                                                              |
  | 星期     | week           |                                                              |

-  

-  

- 1. 表单的新增其他属性

-  

- | placeholder  | 提示文本,提示占位                                            |
  | ------------ | ------------------------------------------------------------ |
  | autofocus    | 自动获取焦点:进入页面时,焦点自动定在这个文本框               |
  | autocomplete | 自动完成: on:打开  off:关闭   1.必须成功提交过:提交过才会记录   2.当前添加autocomplete的元素必须有name属性 |
  | required     | 必须输入,没有输入则会阻止当前数据提交                        |
  | pattern      | 正则表达式验证   pattern="^(\+86)?1\d{10}$"                  |
  | multiple     | 在file中选择多个文件 ; 在email中允许输入多个邮箱地址,逗号分隔 |
  | form         | form="id"   在指定id号的表单进行数据提交的时候,input元素的数据也会一起提交 |

- **注****:****写表单时必须要有****form****包含**

-  

- 1. 新增表单属性

-  

- | datalist | 创建选择列表 | <input type="text" list="subjects">   <datalist id="subjects">   <option value="前端"    label="非常好"></option>   </datalist> | 1.不仅可以选择还可以输入;   2.需要建立datalist和input之间的关联;   3.value:具体的值;label:提示信息,辅助值;   4.option可双标签可单标签   5.如果input type为url,value值要加http:// |
  | -------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | keygen   | 加密         | <keygen></keygen>                                            | 可单可双标签                                                 |
  | output   | 显示输出信息 | <output>总金额：￥100.00</output>                            | 1.只能显示不能修改       2.语义性更强       3.值需要设置,不能自动计算 |

-  

-  

- 1. 新增事件

-  

- | oninput   | 监听当前指定元素内容的改变 | 只要内容改变(添加内容,删除内容),就会触发这个事件 |
  | --------- | -------------------------- | ------------------------------------------------ |
  | onkeyup   | 键盘弹起的时候触发         | 每一个键的弹起都会触发一次                       |
  | oninvalid | 当验证不通过时触发         | this.setCustomValidity("   ")设置默认的提示信息  |

-  

- 1. 进度条

-  

- | progress   双标签 | 属性:   max:最大值   value:当前进度值                        |
  | ----------------- | ------------------------------------------------------------ |
  | meter   双标签    | 属性:   high:规定的较高的值   low:规定的较低的值   max:最大值   min:最小值   value:当前度量值 |

-  

- 1. 总结案例

-  ![01](/Users/jiayiwang/Downloads/01.png)

-  

- 1. 音频和视频

-  

- | audio:音频 | <audio src="../mp3/aa.mp3"></audio>                          | src:播放的音频文件的路径   controls:播放器的控制面板   autoplay:自动播放器   loop:循环   muted:新版谷歌浏览器不能自动播放,加上muted属性即可自动播放 |
  | ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | video:视频 | <video>   <source src="../mp4/mp4.mp4" type="video/mp4">   <source src="../mp4/flv.flv" type="video/flv">   </video> | src,controls,autoplay,loop,   width:宽度(只设置宽或高,等比缩放)   height:高度   poster:当视频还没有完全下载,或者用户还没有开始播放前的默认显示的封面.默认显示当前动画的第一帧   source的使用:不同浏览器支持的视频文件格式不一样,添加视频时 可以准备多个格式的视频文件,让浏览器自动选择 |

-  

- 1. 获取元素

-  

- | querySelector(选择器名称) | 获取单个元素,如果获取的元素不止一个,取第一个   参数要求:   类选择器 加 ' . ' ;   id选择器 加 ' # ' ; |
  | ------------------------- | ------------------------------------------------------------ |
  | querySelectorAll(   )     | 获取满足条件的所有元素                                       |

-  

- 1. 10.操作样式

-  

- | classlist | 当前元素的所有样式列表,数组    |                                                 | 获取样式   document.querySelector('li').classList.item;      |
  | --------- | ------------------------------ | ----------------------------------------------- | ------------------------------------------------------------ |
  | add       | 为元素添加指定名称的样式       | 一次只能添加一个样式                            | document.querySelector('li').classList.add('red');   jq: $(obj).addClass( ); |
  | remove    | 为元素移除指定名称的样式       | 一次只能移除一个样式,class属性还在              | document.querySelector('li').classList.remove('red');   jq: $(obj).removeClass( ); |
  | toggle    | 切换元素的样式                 | 如果元素之前没有指定名称的样式则添加,没有则移除 | document.querySelector('li').classList.toggle('red');   jq: $(obj).toggleClass( ); |
  | contains  | 判断元素是否包含指定名称的样式 | 返回true/false                                  | document.querySelector('li').contains('red');   jq: $(obj).hasClass( ); |

-  

- className 与 classList.add( ) 的区别:

- className     会对元素原先所有的类名进行覆盖

- classList.add( )  会在元素原来类名之后添加

-  

- 1. 自定义属性

- 定义:

- data- 开头

- data- 后必须有一个字符

- 名称都应该使用小写,不要有特殊字符,不要纯数字

- data-school-name="itcast"

-  

- 取值:

- document.querySelector('p').dataset['schoolName'];

- 取值时,将data-后面的单词使用camel命名法连接

-  

- jQuery之中属性取值:

- $(obj).attr('data-school-name')

- $(obj).data('schoolName / school-name')

- $(obj).prop()          属性值不能改变的属性取值用prop,如checked,disabled,selected

-  

- 1. 新增的接口

-  

- | ononline               | 网络连通时触发 | window.addEventListener('online',**function**(){});          |                                                              |
  | ---------------------- | -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | onoffline              | 网络断开时触发 | window.addEventListener('offline',**function**(){});         |                                                              |
  | requestFullScreen(   ) | 全屏           | if(div.requestFullScreen){   div.requestFullscreen();   }else if(div.webkitRequstFullScreen){   div.webkitRequstFullScreen();   }else if ... | 不同浏览器需要添加不同的前缀:   chrome:webkit   firefox:moz   ie:ms   opera:o |
  | cancelFullScreen(   )  | 取消全屏       | document.CancelFullScreen();                                 | 退出全屏,只能使用document来执行                              |
  | fullscreenElement      | 判断是否全屏   | if(document.fullscreenElement \|\| document.webkitFullscreenElement \|\| document.mozFullscreenElement){   alert('true');   }else{   alert('false');   } | 也是用document来实现   火狐是最标准的驼峰命名法              |

-  

- 1. FileReader的使用

- FileReader:读取文件内容

- 1.readAsText( ):读取文本文件(可以使用TXT打开的文件),返回文本字符串,默认编码UTF-8

- 2.readAsBinaryString( ) :读取任意类型的文件.返回二进制字符串,用于存储文件

- 3.readAsDataURL( ) : 读取文件获取一段以data开头的字符串,这段字符串的本质就是DataURL.DataURL是一种将文件嵌入到文档的方案,将资源转换为base16编码的字符串形式,并将这些内容直接存储在url中,用于优化网站的加载速度和执行效率

- abort( ) :中断读取

- FileReader提供一个完整的事件模型,用来捕获文件时的状态

- onabout : 读取文件中断片时触发

- onerror : 读取错误时触发

- onload : 文件读取完成时触发

- onloadend : 读取完成时触发,无论成功还是失败

- onloadstart : 开始读取时触发

- onprogress : 读取文件过程中持续触发

-  

- 案例:

- 需求:即时预览-当用户选择完图片之后就立即进行文件预览

-  ![02](/Users/jiayiwang/Downloads/02.png)

-  

-  

-  

- 多文件上传:

-  ![03](/Users/jiayiwang/Downloads/03.png)

-  

-  

- 1. 地图