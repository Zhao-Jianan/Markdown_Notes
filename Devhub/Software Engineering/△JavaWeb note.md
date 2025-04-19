# Web前端开发
## 初识Web前端
### Web
#### 概念
Web:全球广域网，也称为万维网（www World Wide Web），能够通过浏览器访问的网站
#### Web网站的工作流程
##### 前后端分离开发模式（主流开发模式）
| 发起方                      | 接收方                           | 操作类型 | 内容                |
|:--------------------------|:--------------------------------|:---------|:-------------------|
| 浏览器                     | 前端服务器（前端程序）             | 请求      | 请求页面/资源         |
| 前端服务器（前端程序）         | 浏览器                           | 响应      | 返回前端代码（HTML/CSS/JS） |
| 浏览器                     | 后端服务器（Java程序）             | 请求      | 请求数据             |
| 后端服务器（Java程序）         | 数据库服务器                       | 请求      | 查询数据             |
| 数据库服务器                 | 后端服务器（Java程序）             | 响应      | 返回查询结果          |
| 后端服务器（Java程序）         | 浏览器                           | 响应      | 返回数据（通常是JSON）   |

##### 前后端混合开发模式（早期开发模式）
前后端在同一台服务器，后端服务器（前端程序+Java程序）一并将页面代码（含数据）响应到浏览器

### 网页
#### 组成
网页由文字、图片、音频、视频、超链接等组成

**网页的本质是程序员写的前端代码**

前端代码如何转换成用户眼中的网页
- 通过浏览器转化（解析和渲染）
- 浏览器中对代码进行解析渲染的部分，称为浏览器内核
*不同的浏览器，内核不同，对于相同的前端代码解析的效果会存在差异*
#### Web标准
Web标准也称为网页标准，由一系列标准组成，大部分由W3C（World Wide Web Consortium，万维网联盟）负责制定
有三个组成部分
##### HTML
负责网页的结构（页面元素和内容）
##### CSS
负责网页的表现（页面元素的外观、位置等页面样式，如：颜色、大小等）
##### JavaScript
负责网页的行为（交互效果）

## HTML
### 定义
HTML(HyperText Markup Language)超文本标记语言
#### 超文本
超越了文本的限制，比普通文本更强大。除了文字信息，还可以定义图片、音频、视频等内容
#### 标记语言
由标签构成的语言
- HTML标签都是预定义好的。例如：使用\<a>展示超链接，使用\<img>展示图片，\<video>展示视频
- HTML代码直接在浏览器中运行，HTML标签由浏览器解析


### 语法格式
#### HTML结构标签
```
<html>
   <head>
      <title>标题</title>
   </head>
   <body>

   </body>
</html>
```

#### 语法特点
- HTML标签不区分大小写，开发中一般使用小写
- HTML标签属性值单双引号都可以
- HTML语法松散

#### 注意事项
在HTML中无论输入多少个空格，只会显示一个，可以使用空格占位符```&nbsp;```

### 基础标签
#### 图片标签
##### 格式
```
<img src="">
```
##### 属性
###### ```src```
```
src
```
指定图像的url（绝对路径/相对路径）
路径书写方式
- 绝对路径
  - 绝对磁盘路径
  - 绝对网络路径
- 相对路径
  - ./ 
表示当前目录，./可以省略
  - ../
表示上一级目录， ../不能省略

###### ```width```
```
width
```
图像的宽度（像素/相对于父元素的百分比）
单位有两种写法
- px
像素
- %
相对于父元素的百分比

###### ```height```
```
height
```
图像的高度（像素/相对于父元素的百分比）
#### 标题标签```<h1> - <h6>```
#### 水平线标签```<hr>```

#### 布局标签
实际开发网页中，会大量频繁的使用```div```和```span```这两个没有语义的布局标签
##### ```div```标签
###### 格式
```
<div></div>
```
###### 特点
- 一行只显示一个（独占一行）
- 宽度默认是父元素的宽度，高度默认由内容撑开
- 可以设置宽高（width、height）
##### ```span```标签
没有任何语义的布局标签，开发网页时会大量使用
###### 格式
```
<span></span>
```
###### 特点
- 一行可以显示多个（组合行内元素）
- 宽度和高度默认由内容撑开
- 不可以设置宽高（width、height）


#### 超链接标签
##### 格式
```
<a href="..." target="..."></a>
```
##### 属性
###### ```href```
指定资源访问的url
###### ```target```
指定在何处打开资源链接
- ```_self```
默认值，在当前页面打开
- ```_blank```
在空白页面打开

#### 视频标签
##### 格式
```
<video>
```
##### 属性
###### ```src```
规定视频的url
###### ```controls```
显示播放控件
###### ```width```
播放器的宽度
###### ```height```
播放器的高度

#### 音频标签
##### 格式
```
<audio>
```
##### 属性
###### ```src```
规定音频的url
###### ```controls```
显示播放控件

#### 段落标签
##### 格式
```
<p>
```

#### 文本加粗标签
##### 格式
- ```<b>```
仅加粗
- ```<strong>```
加粗且表示强调

#### 表格标签
##### 场景
在网页中以表格（行、列）形式整齐展示数据，如：班级表
##### 标签
```
<table>
```
定义表格整体，可以包裹多个\<tr>
- 属性
  - ```border```
规定表格边框的宽度
  - ```width```
规定表格的宽度
  - ```cellspacing```
规定单元之间的空间
```
<tr>
```
表格的行，可以包裹多个```<td>```
```
<td>
```
表格单元格（普通），可以包裹内容
```
<th>
```
表格单元格（表头），用法和```<td>```相同，会自动加粗

#### 表单标签
##### 场景
在网页中主要负责数据采集功能，如注册、登录等数据采集
##### 标签
```
<form>
```
##### 表单项
```
<input>
```
定义表单项，通过type属性控制输入形式
- type取值
  - text
默认值，定义单行的输入字段
  - password
定义密码字段
  - radio
定义单选按钮
  - checkbox
定义复选框
  - file
定义文件上传按钮
  - date/time/datetime-local
定义日期/时间/日期时间
  - number
定义数字输入框
  - email
定义邮件输入框
  - hidden
定义隐藏域
  - submit/rest/button
定义提交按钮/重置按钮/可点击按钮


```
<select>
```
定义下拉列表
```
<textarea>
```
定义文本域
**注意：表单项必须有name属性，才可以提交**

##### 属性
- action
规定当提交表单时，向何处发送表单数据，URL
- method
规定用于发送表单数据的方式。GET、POST
- GET
method的默认值，会在url后面拼接表单数据，比如：```?username=tom&age=12```，url长度有限制
- POST
在消息体（请求体）中传递的，参数大小无限制


## CSS
CSS(Cascading Style Sheet)层叠样式表，用于控制页面的样式（表现）
### CSS引入方式
#### 行内样式
写在标签的style属性中（不推荐）
##### 语法格式
```
<h1 style="color:red">
```
#### 内嵌样式
写在style标签中（可以写在页面任何位置，但通常约定写在head标签中）
##### 语法格式
```
    <style>
        h1{
            color:blue;
        }
    </style>
```
#### 外联样式
写在一个单独的.css文件中（需要通过link标签在网页中引入）
##### 语法格式
###### .css文件
```
h1{
    color:green;
}
```
###### .html文件
```
    <link rel="stylesheet" href="css\news.css">
```

#### CSS选择器
用来选取需要设置样式的元素（标签）
**优先级：ID选择器 > 类选择器 > 元素选择器**
##### 元素选择器
根据标签名选取需要设置样式的元素
###### 语法格式
css
```
元素名{
   color:red;
}
```

##### ID选择器
给标签指定id属性，通过id选取需要设置样式的元素
###### 语法格式
- css
```
#id属性值{
   color:red;
}
```
- html
```
<元素名 id="属性值">CSS id Selector</元素名>
```
##### 类选择器
给标签指定class属性，通过class选取需要设置样式的元素
###### 语法格式
- css
```
.class属性值{
   color:red;
}
```
- html
```
<元素名 class="属性值">CSS class Selector</元素名>
```

### CSS属性
#### 颜色属性color
color，设置文本内容的颜色
##### 颜色表示方式
- 关键字
预定义的颜色名，取值格式为red、green、blue等
= RGB表示法
红绿蓝三原色，每项取值范围0-255，取值格式为rgb(0,0,0)
= 十六进制表示法
#开头，将数字转换成十六进制表示，取值格式为#000000、#ff0000、#cccccc等，简写为#000、#f00、#ccc

#### 字体大小属性```font-size```
设置字体大小，要加px

#### 文本修饰属性```text-decoration```
规定添加到文本的修饰
##### 属性值
###### text-decoration-line
设置要使用的文本装饰类型（如下划线、上划线、划线）
- none
默认值。规定 text-decoration 没有线条
- underline
规定在文本下方显示线条
- overline
规定在文本上方显示线条
- line-through
规定显示横穿文本的线条
###### text-decoration-color
设置文字装饰的颜色
###### text-decoration-style
设置文本装饰的样式（如实心、波浪形、点线、虚线、双线）
###### thickness
设置装饰线的粗细

#### text-indent
定义第一行内容改的缩进

#### text-align
规定元素中的文本的水平对齐方式

#### line-height
设置行高


### 盒子模型
#### 盒子
页面中所有的元素（标签），都可以看做是一个盒子，由盒子将页面中的元素包含在一个矩形区域内，通过盒子的视角更方便的进行页面布局
#### 盒子模型的组成
- 内容区域（content）
- 内边距区域（padding）
- 边框区域（border）
- 外边距区域（margin）
#### CSS属性
- width
设置宽度
- height
设置高度
- border
设置边框的属性，如1px solid #000;
- padding
内边距
- margin
外边距，四个数值表示上右下左，两个数值表示上下和左右，可以使用auto来自动计算

*注意：如果只需要设置某一个方位的边框、内边距、外边距，可以在属性名后加上-位置，如：padding-top、padding-left、padding-right、padding-bottom等*


## JavaScript
### 定义
- JavaScript，简称JS，是一门跨平台、面向对象的脚本语言，是用来控制网页行为的，它能使网页可交互
- JavaScript和Java是完全不同的语言，不论是概念还是设计。但是基础语法类似
- JavaScript1995年由Brendan Eich发明，于1997年成为ECMA标准
- ECMAScript 6（ES6）是最新的JavaScript版本（发布于2015年）

*ECMA国际（前身为欧洲计算机制造商协会），制定了标准化的脚本程序设计语言ECMAScript，这种语言的到广泛应用。而JavaScript是遵守ECMAScript的标准的*
### JS引入方式
即JavaScript与HTML的结合方式，主要有两种形式
#### 内部脚本
将JS代码定义在HTML页面中
##### 语法规则
- JavaScript代码必须位于\<script></script>标签之间
- 在HTML文档中，可以在任意地方，放置任意数量的\<script>
- 一般会把脚本置于<body>元素的底部，可以在页面加载完成后再执行Javascript代码，改善显示速度
- HTML5新规则
  - 把Javascript代码放在head里，在\<script>起始标签里最后加上defer，也可以达到在页面加载完成后再执行Javascript代码的效果，改善显示速度
  - 把Javascript代码放在head里，在\<script>起始标签里最后加上async，会同时执行Javascript代码和加载页面

##### 语法格式
```
<script>
   alert("Hello JavaScript")
</script>
```
#### 外部脚本
将JS代码定义在外部JS文件中，然后引入到HTML页面中
##### 语法规则
- 外部JS文件中，只包含JS代码，不包含\<script>标签
- \<script>标签不能自闭合
##### 语法格式
- .js文件
```
alert("Hello JavaScript")
```
- .html文件
```
<script src="js/demo.js"></script>
```

### JS基础语法
#### JS书写语法
##### 语法规则
- 区分大小写，与Java一样，变量名、函数名以及其他一切东西都是区分大小写的
- 每行结尾的分号可有可无，一般要写上分号
- 注释格式
  - 单行注释：```//注释内容```
  - 多行注释：```/*注释内容*/```
- 大括号表示代码块

##### 输出语句
- 使用```window.alert()```写入警告框
- 使用```document.write()```写入HTML输出
- 使用```console.log()```写入浏览器控制台
```
<script>
   window.alert("Hello JavaScript");   //浏览器弹出警告框
   document.write("Hello JavaScript");//写入HTML，在浏览器中展示
   console.log("Hello JavaScript");  //写入浏览器控制台
</script>
```

#### 变量
##### 语法规则
- JavaScript中用var关键字（variable缩写）来声明变量
- JavaScript是一门弱类型语言，变量可以存放不同类型的值
- 变量名需要遵循如下规则
  - 组成字符可以是任何字母、数字、下划线或美元符号
  - 不能以数字开头
  - 建议使用驼峰命名法

##### var关键字
- 作用域比较大，它是全局变量
- 可以重复声明

##### let关键字
ECMAScript 6新增的用来定义变量的关键字。它的用法类似于var，但是声明的变量只能在let关键字所在的代码块内有效，且不允许重复声明
##### const关键字
ECMAScript 6新增的用来定义变量的关键字。它用来声明一个只读的常量。一旦声明，常量的值就不能改变

#### 数据类型
JavaScript中数据分为原始类型和引用类型
##### 原始类型
- number
数字（整数、小数、NaN(Not a Number)）
- string
字符串，单双引号都可以
- boolean
布尔
- null
空对象
- undefined
当声明的变量未初始化时，该变量的默认值是undefined

#### 运算符
##### 算术运算符
```
+ - * / % ++ --
```
##### 赋值运算符
```
= += -= *= /= %=
```
##### 比较运算符
```
- > < >= <= != ==
- ===
```
全等运算，在进行比较时，```==```会进行类型转换，而```===```不会进行类型转换
```
var a = 10;
alert(a == "10");   //true
alert(a === "10"); //false
alert(a === 10);   //true
```
##### 逻辑运算符
```
&& || !
```
##### 三元运算符
```
条件表达式?true_value:false_value
```
##### typeof
使用typeof运算符，可以获取数据类型

#### 类型转换
##### 字符串类型转为数字
将字符串字面值转为数字。如果字面值不是数字，则转为NaN
```
alert(parseInt("12"));     //12
alert(parseInt("12A45"));  //12
alert(parseInt("A45"));    //NaN
```
##### 其他类型转为boolean
- Number
0和NaN转为false，其他均转为true
- String
空字符串转为false，其他均转为true
- Null和undefined
均转为false

#### 流程控制
- ```if...else if...else...```
- ```switch```
- ```for```
- ```while```
- ```do...while```

### JS函数
函数（方法）是被设计为执行特定任务的代码块
#### 定义方法
JavaScript函数通过function关键字进行定义
##### 定义方式1
- 语法
```
function functionName(参数1,参数2...){
   //要执行的代码
}
```
- 注意事项
  - 形式参数不需要类型，因为JavaScript是弱类型语言
  - 返回值也不需要定义类型，可以在函数内部直接使用return返回即可

##### 定义方式2
- 语法
```
var functionName = function(参数1,参数2...){
   //要执行的代码
}
```

#### 调用方法
函数名称(实际参数列表)

**注意事项**
**JS中，函数调用可以传递任意个数的参数**

*JavaScript本身没有main函数。可以将浏览器视为main函数。在HTML文档的头部或正文中的 \<script> 中编写的任何代码都只会从第一行到最后一行执行。 但此后程序不需要终止*

### JS对象
#### 对象分类
##### 基础对象
- ```Array```
- ```String```
- ```JSON```
##### BOM对象
##### DOM对象

#### Array对象
JavaScript中```Array```对象用于定义数组
##### 定义语法
- 方式1
```
var 变量名 = new Array(元素列表);
```
- 方式2
```
var 变量名 = [元素列表];
```

*注意，这种简化定义方式和Java中不同，Java是用{}，JavaScript是用[]*

##### 访问语法
```
arr[索引] = 值;
```
##### 特点
JavaScript中的数组相当于Java的集合，数组的长度可变，JavaScript是弱类性，类型可变，可以存储任意类型的数据

##### 属性
- length
设置或返回数组中元素的数量
##### 方法
- forEach()
遍历数组中的每个有值的元素，并调用一次传入的函数
  - 语法格式
```
arr.forEach(function(e){
    console.log(e);
})
```
  - ES6新增的箭头函数
类似Lambda函数，格式为```(...) => {...}```
```
arr.forEach((e) =>console.log(e));
```
- push()
将新元素添加到数组的末尾，并返回新的长度
- splice()
从数组中删除元素

#### String字符串对象
##### 创建方式
String字符串对象创建方式有两种
- 方式一
```
var 变量名 = new String("...");
```
- 方式二
```
var 变量名 = "...";
```
##### 属性
- length
获取字符串的长度
##### 方法
- charAt()
返回在指定位置的字符
- indexOf()
检索字符串
- trim()
去除字符串两边的空格
- substring()
提取字符串中两个指定的索引号之间的字符

#### JavaScript自定义对象
##### 定义格式
```
var 对象名 = {
    属性名1:属性值1,
    属性名2:属性值2,
    属性名3:属性值3,
    函数名称:function(形参列表){}
    函数名称(形参列表){}  //函数的简写形式
};
```
##### 调用格式
```
对象名.属性名;
对象名.函数名();
```
#### JSON
##### 概念
- JavaScript Object Notation，Javascript对象标记法
- JSON是通过JavaScript对象标记书写的文本
##### 用途
由于其语法简单，层次结构鲜明，现多用于作为数据载体，在网络中进行数据传输，是当前前后端传输复杂数据的主流格式

##### 语法格式
是key和value的键值对，key需要用双引号括起来，中间使用冒号连接，不同键值对中间用逗号隔开
###### 定义
```
var 变量名 = '{
    "key1":value1,
    "key2":value2,
    "key3":value3
}';
```
##### value的数据类型
| 数据类型 | 表示形式                  |
|:----------|:---------------------------|
| 数字       | 整数或浮点数                |
| 字符串     | 放在双引号中，例如 `"hello"` |
| 逻辑值     | `true` 或 `false`           |
| 数组       | 放在方括号中，例如 `[1, 2, 3]` |
| 对象       | 放在花括号中，例如 `{"key": "value"}` |
| null      | `null`                     |


##### 解析方法
- JSON字符串转为JS对象
```
var jsObject = JSON.parse(userStr);
```
- JS对象转为JSON字符串
```
var jsonStr = JSON.stringify(jsObject);
```

#### BOM
##### 概念
Browser Object Model 浏览器对象模型，允许JavaScript与浏览器对话，JavaScript将浏览器的各个组成部分封装为对象
##### 组成
- Window浏览器窗口对象
- Navigator浏览器对象
- Screen屏幕对象
- History历史记录对象
- Location地址栏对象

##### Window
浏览器窗口对象
###### 获取
直接使用window，其中window可以省略
window.alert("Hello Window");
alert("Hello Window");
###### 属性
- history
对History对象的只读引用
- location
用于窗口或框架的Location对象
- navigator
对navigator对象的只读引用
###### 方法
- alert()
显示带有一段消息和一个确认按钮的警告框
- confirm()
显示带有一段消息以及确认按钮和取消按钮的对话框,它有一个布尔类型返回值，选择确认返回true，选择取消返回false
- setInterval()
按照指定的周期（以毫秒计）来调用函数或计算表达式
```
        var count = 0;
        setInterval(function(){
            count ++;
            console.log("定时器执行了" + count + "次");
        },2000);
```
- setTimeout()
在指定的毫秒数后调用函数或计算表达式

##### Location
地址栏对象
- 获取
使用window.location.属性，其中window.可以省略
window.location.属性;
location.属性;
- 属性
  - href
设置或返回完整的URL
```
location.href = "";
```

#### DOM
##### 概念
Document Object Model 文档对象模型，它可以将标记语言的各个组成部分封装为对应的对象。它是中立于平台和语言的接口，它允许程序和脚本动态地访问、更新文档的内容、结构和样式

##### HTML DOM
HTML DOM 是 HTML 的标准对象模型和编程接口。它定义了：
- 作为对象的 HTML 元素
- 所有 HTML 元素的属性
- 访问所有 HTML 元素的方法
- 所有 HTML 元素的事件
HTML DOM 是关于如何获取、更改、添加或删除 HTML 元素的标准

##### DOM的组成部分
DOM是W3C（万维网联盟）的标准，定义了访问HTML的XML文档的标准，分为3个不同的部分
- CoreDOM - 所有文档类型的标准模型
  - Document整个文档对象
  - Element元素对象
  - Attribute属性对象
  - Text文本对象
  - Comment注释对象
- XML DOM - XML文档的标准模型
- HTML DOM -HTML文档的标准模型
  - Image:```<img>```
  - Button:```<input type='button'>```

##### DOM 编程界面
- HTML DOM 能够通过 JavaScript 进行访问（也可以通过其他编程语言）
- 在 DOM 中，所有 HTML 元素都被定义为对象
- 编程界面是每个对象的属性和方法
- 属性是能够获取或设置的值（比如改变 HTML 元素的内容）
- 方法是能够完成的动作（比如添加或删除 HTML 元素）

##### 对象
- Document整个文档对象
- Element元素对象
- Attribute属性对象
- Text文本对象
- Comment注释对象

##### DOM树
DOM将标记语言的各个组成部分封装为对应的对象后，以DOM树的方式存储
- 文档对象 `Document`
  - 根元素 `<html>`（元素对象 Element）
    - 元素 `<head>`（元素对象 Element）
      - 元素 `<title>`（元素对象 Element）
        - 标题文本（文本对象 Text）
    - 元素 `<body>`（元素对象 Element）
      - 元素 `<h1>`（元素对象 Element）
        - 属性 `href`（属性对象 Attribute）
        - 内容文本（文本对象 Text）



##### DOM的用途
JavaScript通过DOM，就能对HTML进行操作
- 改变HTML元素的内容
- 改变HTML元素的样式（CSS）
- 对HTML DOM事件做出反应
- 添加和删除HTML元素

##### DOM获取对象
HTML中的Element对象可以通过Document对象获取，而Document对象是通过window对象获取的
Document对象中提供了以下获取Element元素对象的函数
- 根据ID属性值获取，返回单个Element对象
```
var h1 = document.getElementById('h1');
```
- 根据标签名称获取，返回Element
```
var divs = document.getElementsByTagName('div');
```
- 根据name属性值获取，返回Element对象数组
```
var hobbys = document.getElementsByName('hobby');
```
- 根据class属性值获取，返回Element对象数组
```
var class = document.getElementsByClassName('cls');
```

### JS事件监听
#### 定义
##### 事件
HTML事件是发生在HTML元素上的“事情”，例如：
- 按钮被点击
- 鼠标移动到元素上
- 按下键盘按键
##### 事件监听
JavaScript可以在事件被侦测到时执行代码

#### 事件驱动编程
与在固定时间间隔内执行代码不同，一种非常强大的编程风格是提供在页面上发生特定条件（称为事件）时执行的代码

例如，一段 JavaScript 代码可以在用户点击链接或提交表单时执行。与编写单一的庞大程序不同，JavaScript设计小型功能块，称为事件处理程序或事件监听器，以处理特定的事件

这种编码风格在图形用户界面（GUI）编程中很典型，其中 GUI 框架提供一个主函数来观察用户界面的变化，并在发生特定事件（如用户操作）时将执行权交给应用程序代码

在JavaScript中，主函数是一个浏览器，我们可以告诉它想要监听的一些事件，即事件绑定

在现代标准兼容的 HTML+JavaScript 中，有三种主要的方法来实现这一点

#### 事件绑定
##### 方法1：通过HTML标签中的事件属性进行绑定
直接在HTML源代码中通过提供以on...开头的属性将事件处理程序附加到HTML元素上
###### HTML代码
```
<input type="button" onclick="on()" value="按钮1">
```
###### JavaScript代码
```
function on(){
  alert("点击事件触发");
}
```

对于偶尔使用的事件处理程序而言这种方法很简单，但这种方法破坏了关注点分离，因为它混淆了Web内容与其行为。而且，在HTML中以一种不可扩展的方式混淆了行为注解


##### 方法2：通过DOM元素属性绑定
通过JavaScript内部附加事件监听器。如果在外部链接的脚本文件中这样做，就能够实现很好的关注点分离，不影响HTML内容
###### HTML代码
```
<input type="button" id="btn" value="按钮2">
```
###### JavaScript代码
```
document.getElementById('btn').onclick=function(){
  alert("点击事件触发");
}
```

##### 方法3：附加通用的事件监听器
为了更灵活地附加事件监听器，可以使用通用的方法，而不是直接在HTML属性中指定。通过JavaScript代码，可以在页面加载后选择特定的元素，并为其添加事件监听器
用事件名称作为参数来调用任何 HTML DOM 元素的通用方法 ```addEventListener```
通过这种方式，能够在代码中集中处理行为，而不是将其散布在HTML中，从而更好地保持关注点的分离。这种通用的事件监听器附加方式使得代码更易维护和扩展
###### JavaScript代码
```
function sayThanks(event) {
    window.alert("Thanks for clicking me");
}
let button = document.getElementByID("click-me-button");
button.onclick = sayThanks;
```

##### DOMContentLoaded
上述方法除了第一个之外，其他都依赖于在执行脚本之前内容完全加载。否则，脚本将尝试修改尚未创建的DOM元素。确保脚本只在页面设置完成后运行的方法有3种
- 方法1
将依赖内容加载的任何 ```<script>``` 元素放在页面 ```<body>``` 底部。脚本只有在页面完全构建后才会加载
  - 虽然在过去这是一种广泛采用的方法，但现在有更好的方法来实现相同的行为，而且在 <body> 中的脚本有点不雅观。毕竟，它们实际上不是视觉页面内容的一部分，因此在语义上应该放在 <head> 部分
- 方法2
使用 ```<script src="..." defer>``` 加载任何外部脚本，以确保它们仅在页面构建时执行
  - 这肯定有效，但可能有点过于粗暴，因为可能存在其他不依赖于DOM完全构建的脚本操作
- 方法3
将所有初始化代码放入 DOMContentLoaded 事件的事件监听器中。只有在DOM完全构建后，此监听器中的代码才会执行
  - 使用这种方法的脚本最好在HTML文档的 ```<head>``` 部分以 ```<script src="..." async>``` 的方式加载

#### 常见事件
##### onclick
鼠标单击事件
##### onblur
元素失去焦点
##### onfocus
元素获得焦点
##### onload
某个页面或图像被完成加载
##### onsubmit
当表单提交时触发该事件
##### onkeydown
某个键盘的键被按下
##### onmouseover
鼠标被移到某元素之上
##### onmouseout
鼠标从某元素移开

## 前端框架
### VUE
#### 基本概念
- Vue是一套前端框架，免除原生JavaScript中的DOM操作，简化书写
- Vue基于MVVM（Model-View-ViewModel）思想，实现数据的双向绑定，将编程的关注点放在数据上
  - Model
数据模型，特指前端中通过请求从后台获取的数据。Model可以通过Ajax来发起请求从后台获取
  - View
视图，用于展示数据的页面，可以理解成html+css搭建的页面，但是没有数据。可以使用ElementUI框架来替代HTML+CSS来更加方便的搭建View
  - ViewModel
数据绑定到视图，负责将数据（Model）通过JavaScript的DOM技术，将数据展示到视图（View）上。vue前端框架侧重于ViewModel部分开发，用来替代JavaScript的DOM操作，让数据展示到视图的开发变得更加简单
#### 官网
https://v2.cn.vuejs.org/

#### 定义
##### Vue.js
Vue.js（读音 /vjuː/, 类似于 view）是一套构建用户界面的渐进式框架。与其他重量级框架
不同的是，Vue 采用自底向上增量开发的设计。Vue的核心库只关注视图层，并且非常容易学习，非常容易与其它库或已有项目整合。Vue.js的目标是通过尽可能简单的API实现响应的数据绑定和组合的视图组件
##### 框架
框架是一个半成品软件，是一套可重复使用的、通用的软件基础代码模型。基于框架进行开发，更加快捷，更加高效

#### 快速入门
##### 使用步骤
- 第1步==>新建HTML页面，引入Vue.js文件
```
<script src="js/vue.js"></script>
```
- 第2步==>在JS代码区域，创建Vue核心对象，定义数据模型
```
<script>
   new Vue({
       el: "#app",  //Vue接管的区域
       data: {
           message: "Hello Vue!"
       }
   })
</script>
```
在创建vue对象时，有几个常用的属性：
  - el
用来指定哪儿些标签受Vue管理。 该属性取值#app中的app需要是受管理的标签的id属性值
  - data
用来定义数据模型
  - methods
用来定义函数

- 第3步==>编写视图
```
<div id="app">
    <input type="text" v-model="message">  //v- 指令
    {{ message }}
</div>
```
##### 插值表达式
用来将vue对象中定义的model展示到页面上
###### 形式
```
{{表达式}}
```
###### 内容
可以是
- 变量
- 三元运算符
- 函数调用
- 算术运算

#### Vue常用指令
##### 指令
HTML标签上带有v-前缀的特殊属性，不同指令具有不同含义。在vue中，通过大量的指令来实现数据绑定到视图
##### 常用指令
###### v-bind
```
v-bind
```
为HTML标签绑定属性值，如设置href、CSS样式等。当vue对象中的数据模型发生变化时，标签的属性值会随之发生变化
- HTML代码
```
<div id="app">
<a v-bind:href="url">文字</a>
</div>
```
简化版本：```<a :href="url">文字</a>  //v-bind可以省略，但是:不能省略```
- JavaScript代码
```
<script>
  new Vue({
     el:"#app",
     data: {
        url: "https://www.baidu.com"
     }
  })
</script>
```
###### v-model
```
v-model
```
在表单元素上创建双向数据绑定。vue对象的data属性中的数据变化，视图展示会一起变化；视图数据发生变化，vue对象的data属性中的数据也会随着变化

*双向绑定一定是使用在表单项标签上的*

*双向绑定的作用：可以获取表单的数据的值，然后提交给服务器*

- HTML代码
```
<input type="text" v-model="url">
```
- JavaScript代码
```
<script>
  new Vue({
     el:"#app",
     data: {
        url: "https://www.baidu.com"
     }
  })
</script>
```
###### v-on
```
v-on
```
为HTML标签绑定事件
*注意：*
*v-on语法给标签的事件绑定的函数，必须是vue对象中声明的函数*
*v-on语法绑定事件时，事件名相比较js中的事件名，没有on*


- HTML代码
```
<input type="button" value="按钮" v-on:click="handle()">
```
简化版本
```
<input type="button" value="按钮" @click="handle()">
```
- JavaScript代码
```
<script>
  new Vue({
     el:"#app",
     data: {
        ...
     },
     methods: {
         handle:function(){
            alert("点击事件触发");
         }
      },    
  })
</script>
```
###### v-if
```
v-if
```
条件性的渲染某元素，判定为true时渲染，否则不渲染
- HTML代码
```
<div id="app">
年龄<input type="text" v-model="age">经判定，为：
<span v-if="age <= 35">年轻人（35岁及以下）</span>
<span v-else-if="age > 35 && age < 60">中年人（35-60）</span>
<span v-else>老年人（60岁及以上）</span>
</div>
```
- JavaScript代码
```
<script>
  new Vue({
     el:"#app",
     data: {
        age: 20
     }
  })
</script>
```
###### v-else-if
条件性的渲染某元素，判定为true时渲染，否则不渲染
###### v-else
条件性的渲染某元素，判定为true时渲染，否则不渲染
###### v-show
根据条件展示某元素，区别在于切换的是display属性的值
- HTML代码
```
<div id="app">
年龄<input type="text" v-model="age">经判定，为：
<span v-show="age <= 35">年轻人（35岁及以下）</span>
<span v-show="age > 35 && age <= 60">中年人（35-60）</span>
<span v-show="age > 60">老年人（60岁及以上）</span>
</div>
```
- JavaScript代码
```
<script>
  new Vue({
     el:"#app",
     data: {
        age: 20
     }
  })
</script>
```
###### v-for
列表渲染，遍历容器的元素或对象的属性
- HTML代码
```
<标签 v-for="变量名 in 集合模型数据">
      {{变量名}}
</标签>
```
需要使用索引时
```
<标签 v-for="(变量名,索引变量) in 集合模型数据">
<!--索引变量是从0开始，所以要表示序号的话，需要手动的加1-->
 {{索引变量 + 1}} {{变量名}}
</标签>
```

例如：
```
<div v-for="addr in addrs">{{addr}}</div>
<div v-for="(addr,index) in addrs">{{index+1}} : {{addr}}</div>
```
- JavaScript代码
```
<script>
  new Vue({
     el:"#app",
     data: {
       addrs:['北京','上海','广州','深圳','杭州','成都']
     }
  })
</script>
```

*通过 ```v-bind``` 或 ```v-model``` 绑定的变量，必须在数据模型中声明，否则会报错*


#### Vue生命周期
##### 生命周期
指的是vue对象从创建到销毁的过程
##### 生命周期8个阶段
每触发一个生命周期事件，会自动执行一个生命周期方法，这些生命周期方法也被称为钩子方法
| 生命周期钩子       | 触发时机                                           | 说明                                               |
|:------------------|:--------------------------------------------------|:--------------------------------------------------|
| beforeCreate       | 创建前，在初始化事件和生命周期之后，初始化注入和校验之前 | 组件实例刚被创建，数据观测和事件配置尚未开始               |
| created            | 创建后，在初始化注入和校验之后                      | 完成数据观测、属性和方法的运算，尚未挂载 DOM               |
| beforeMount        | 挂载前，在创建 `vm.$el` 并替换 `el` 选项前触发       | 模板已编译，尚未挂载到页面上                             |
| mounted            | 挂载完成，Vue 初始化完成，HTML 页面渲染完成后触发       | 常用于页面初始化自动发送 ajax 请求，加载后台数据             |
| beforeUpdate       | 更新前，当 `data` 被修改，虚拟 DOM 重新渲染前触发      | 在视图更新前调用，适合在此时访问现有 DOM                   |
| updated            | 更新后，当 `data` 被修改，虚拟 DOM 重新渲染后触发      | 视图已更新完成，可进行基于新 DOM 的操作                     |
| beforeDestroy      | 销毁前，调用 `vm.$destroy()` 时触发                  | 实例还未被销毁，适合在此时做善后操作（解绑事件、销毁子组件等） |
| destroyed          | 销毁后，实例和子组件、事件监听器都被移除后触发          | 资源清理完毕，组件生命周期结束                             |



### Ajax
#### 定义
Asynchronous JavaScript And XML，异步的JavaScript和XML，AJAX 是一种从网页访问 Web 服务器的技术
#### 作用
- 数据交换
通过Ajax可以给服务器发送请求，并获取服务器响应的数据
- 异步交互
可以在不重新加载整个界面的情况下，与服务器交换数据并更新部分网页的技术，如：搜索联想、用户名是否可用的校验等等

#### 同步与异步
##### 同步
客户端请求服务器后，服务器在处理中客户端只能等待，待服务端响应客户端后，客户端才能继续访问，例如：输入网址打开网页
##### 异步
客户端请求服务器后，服务器在处理中时，客户端可以执行其他操作，待服务端响应客户端后，客户端可以继续访问，例如：搜索引擎关键词联想

#### 原生Ajax
- 传输数据的方法
  - 准备数据地址
  - 创建 ```XMLHttpRequest``` 对象，用于和服务器交换数据
  - 向服务器发送请求
  - 获取服务器响应数据
- 缺点
代码繁琐

#### Axios
Axios对原生的Ajax进行了封装，简化书写，快速开发
##### 概念
Axios 是一个基于 promise 网络请求库，作用于node.js 和浏览器中。 它是 isomorphic 的(即同一套代码可以运行在浏览器和node.js中)。在服务端它使用原生 node.js http 模块, 而在客户端 (浏览端) 则使用 XMLHttpRequests
##### 使用步骤
- 第1步==>如果是在Vue项目中使用Axios，首先要在项目目录下安装axios
```
npm install axios;
```
- 第2步==>引入Axios的js文件
  - 在Vue项目中使用Axios
```
import axios from 'axios';
```
  - 在普通项目中使用Axios
```
<script src="js/axios-018.0.js"></script>
```
- 第3步==>使用Axios发送请求，并获取响应结果
  - get请求
```
axios({
   method:"get",
   url:"https://mock.apifox.cn/m1/3128855-0-default/emp/list"
}).then((result) =>{
   console.log(result.data);
});
```
  - post请求
```
axios({
   method:"post",
   url:"https://mock.apifox.cn/m1/3128855-0-default/emp/deleteById",
   data:"id=1"
}).then((result) =>{
   console.log(result.data);
});
```
*axios()是用来发送异步请求的，小括号中使用js的JSON对象传递请求相关的参数*
- *method属性：用来设置请求方式的。取值为get或者post*
- *url属性：用来书写请求的资源路径。如果是get请求，需要将请求参数拼接到路径的后面，格式为：url?参数名=参数值&参数名2=参数值2*
- *data属性：作为请求体被发送的数据。如果是post请求的话，数据需要作为data属性的值*

*then()需要传递一个匿名函数。then()中传递的匿名函数称为回调函数，意思是该匿名函数在发送请求时不会被调用，而是在成功响应后调用的函数。而该回调函数中的resp参数是对响应的数据进行封装的对象，通过resp.data可以获取到响应的数据*


##### 请求方式别名
###### ```axios.get(url[,config])```
- 发送GET请求
```
axios.get("https://mock.apifox.cn/m1/3128855-0-default/emp/list").then((result) =>{
   console.log(result.data);
});
```
###### ```axios.delete(url[,config])```
###### ```axios.post(url[,data[,config]])```
- 发送POST请求
```
axios.post("https://mock.apifox.cn/m1/3128855-0-default/emp/deleteById","id=1").then((result) =>{
   console.log(result.data);
});
```
###### ```axios.put(url[,data[,config]])```


### 前后端分离开发
#### 前后端混合开发的缺点
- 沟通成本高
- 分工不明确
- 不便管理
- 不便维护扩展

#### 前后端混合开发模式
将原先的工程分为前端工程和后端工程2个工程，然后前端工程交给专业的前端人员开发，后端工程交给专业的后端人员开发。前端页面需要数据，可以通过发送异步请求，从后台工程获取

#### 接口文档
前后端分离开发是要遵循开发规范，叫做接口，一个业务功能就是一个接口，接口文档汇总了所有使用的接口。接口文档一般由项目经理根据页面原型和项目需求制定的

*注意：与Java中的接口（Interface）不同*

#### 前后端分离开发模式的开发流程
##### 需求分析
阅读需求文档，分析需求，理解需求
##### 接口定义（API接口文档）
查询接口文档中关于需求的接口的定义，包括地址，参数，响应数据类型等等
##### 前后端并行开发（遵守规范）
各自按照接口文档进行开发，实现需求
##### 测试（前端、后端）
前后台开发完成后，各自按照接口文档进行测试
##### 前后端联调测试
前段工程请求后端工程，测试功能

#### YAPI
YApi是高效、易用、功能强大的API管理平台，旨在为开发、产品、测试人员提供更优雅的接口管理服务
官网：http://yapi.smart-xwork.cn/
##### 功能
- API接口管理
根据需求撰写接口，包括接口的地址，参数，响应等等信息
- Mock服务
模拟真实接口，生成接口的模拟测试数据，用于前端的测试
##### 接口文档管理

### 前端工程化
#### 目前的前端开发存在问题
目前的前端开发中，当我们需要使用一些资源时，例如：vue.js，和axios.js文件，都是直接再工程中导入的
- 每次开发都是从零开始，比较麻烦
- 多个页面中的组件共用性不好
- js、图片等资源没有规范化的存储目录，没有统一的标准，不方便维护
#### 前端工程化概念
前端工程化是指在企业级的前端项目开发中，把前端开发所需的工具、技术、流程、经验等进行规范化、标准化
#### 前端工程化特点
- 模块化
JS、CSS。将js和css等，做成一个个可复用模块
- 组件化
UI结构、样式、行为。将UI组件，css样式，js行为封装成一个个的组件，便于管理
- 规范化
目录结构、编码、接口。提供一套标准的规范的目录接口和编码规范，所有开发人员遵循这套规范
- 自动化
构建、部署、测试。项目的构建，测试，部署全部都是自动完成

#### Vue-cli
前端工程化是通过vue官方提供的脚手架Vue-cli来完成的，用，用于快速生成一个Vue项目模板
##### vue-cli提供的功能
- 统一的目录结构
- 本地调试
- 热部署
- 单元测试
- 集成打包上线
##### 依赖环境
NodeJS

#### Vue项目
##### Vue项目--创建
- 方式1：命令行
```
vue create vue-project01
```
- 方式2：图形化界面
```
vue ui
```
在命令行中输入后，会弹出图形化界面，然后再进行vue工程的创建

*注意：路径无法识别大写字母，创建文件夹时vue要小写*

##### Vue项目--目录结构
基于Vue脚手架创建出来的工程，有标准的目录结构
- ```node_modules```
整个项目的依赖包
- ```public```
存放项目的静态文件
- ```src```
存放项目的源代码（核心文件夹）
  - ```assets```
静态资源
  - ```components```
可重用的组件
  - ```router```
路由配置
  - ```views```
视图组件（页面）
  - ```App.vue```
入口页面（根组件）
  - ```main.js```
入口js文件
- ```.gitignore```
- ```babel.config.js```
- ```jsconfig.json```
- ```package-lock.json```
- ```package.json```
模块基本信息，项目开发所需要模块，版本信息
- ```README.md```
- ```vue.config.js```
保存vue配置的文件，如：代理、端口的配置等

##### Vue项目--启动
- 方式1
图形化界面上NPM SCRIPTS中点击启动图标
**图形化界面中，按Ctrl+C停止NPM服务**
- 方式2
命令行
```
npm run serve
```
##### Vue项目--配置端口
在vue.config.js中配置
- 语法格式
```
const { defineConfig } = require('@vue/cli-service')
module.exports = defineConfig({
  transpileDependencies: true,
  devServer: {
    port: 7000,
  }
})
```

#### Vue项目开发流程
对于vue项目，index.html文件默认是引入了入口函数main.js文件
##### main.js文件
- import
导入指定文件，并且重新起名。例如 ```import App from './App.vue'``` 导入当前目录下得App.vue并且起名为App
- new Vue()
创建vue对象
- $mount('#app')
将vue对象创建的dom对象挂在到id=app的这个标签区域中，作用vue对象的el属性一致
- router
路由
- render
主要使用视图的渲染
##### Vue组件文件
Vue的组件文件以.vue结尾，每个组件由三个部分组成：```<template>```、```<script>```、```<style>```
- ```<template>```
模板部分，由它生成HTML代码，用来展示页面主体结构的
- ```<script>```
js代码区域，通过js代码来控制模板的数据来源和行为
- ```<style>```
css样式部分，通过css样式控制模板的页面效果


### VUE组件库Element
ElementUI是一款侧重于VUE开发的前端框架，主要用于开发美观的页面的
#### 概念
Element是饿了么团队研发的，一套为开发者、设计师和产品经理准备的基于Vue2.0的桌面端组件库
##### 组件
组成网页的部件，例如超链接、按钮、图片、表格、表单、分页条等
##### 官网
https://element.eleme.cn/#/zh-CNListener

#### 使用步骤
##### 第1步==>安装ElementUI组件库（在当前工程的目录下），在命令行执行指令：
```
npm install element-ui@2.15.3
```
*可以在VSCode中选中项目，右键选择Open in Integrated Terminal*

##### 第2步==>引入ElementUI组件库
在main.js这个入口js文件中引入ElementUI的组件库，其代码如下：
```
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
Vue.use(ElementUI);
```
##### 第3步==>创建vue组件文件
按照vue项目的开发规范，在src/views目录下创建一个vue组件文件，注意组件名称后缀是.vue，并且在组件文件中编写基本组件语法，代码如下：
```
<template></template>
<script>
   export default {
}
</script>
<style></style>
```

##### 第4步==>访问官网，复制组件代码，调整
到ElementUI的官网，找到组件库，然后找到所需组件，抄写代码，注意代码放置在vue组件文件中的模板、脚本、样式对应位置

##### 第5步==>在默认访问的根组件src/App.vue中引入自定义的组件
在根组件src/App.vue中的```<template>```代码块中输入```<element-view>```，会自动在```<script>```代码块中增加
```
import ElementView from './views/Element/ElementView.vue'
export default {
components: { ElementView }
}
```

##### 第6步==>运行vue项目

#### Element常见组件
##### Basic类型
###### Container布局容器
用于布局的容器组件，方便快速搭建页面的基本结构
- 容器组件
  - ```<el-container>```
外层容器。当子元素中包含 ```<el-header>``` 或 ```<el-footer>``` 时，全部子元素会垂直上下排列，否则会水平左右排列
  - ```<el-header>```
顶栏容器
  - ```<el-aside>```
侧边栏容器
  - ```<el-main>```
主要区域容器
  - ```<el-footer>```
底栏容器

*这些组件采用了 flex 布局，使用前要确定目标浏览器是否兼容。此外，```<el-container>``` 的子元素只能是后四者，后四者的父元素也只能是 ```<el-container>``` *
##### Form类型
###### Form表单
由输入框、选择器、单选框、多选框等控件组成，用以收集、校验、提交数据
###### DatePicker日期选择器
用于选择或输入日期

##### Data类型
###### Table表格
用于展示多条结构类似的数据，可对数据进行排序、筛选、对比或其他自定义操作
- 组件属性
  - ```data```
主要定义table组件的数据模型
  - ```prop```
定义列的数据应该绑定data中定义的具体的数据模型
  - ```label```
定义列的标题
  - ```width```
定义列的宽度

###### Pagination分页
当数据量过多时，使用分页分解数据
- 组件属性
  - ```background```
添加背景颜色
  - ```layout```
控制分页工具条的布局

| 功能项   | 说明                     |
|:----------|:--------------------------|
| sizes      | 显示每页多少条               |
| prev       | 显示上一页按钮               |
| pager      | 显示页码按钮                 |
| next       | 显示下一页按钮               |
| jumper     | 显示前往...页的跳转输入框按钮   |


  - ```total```
数据的总数量
- 组件事件
  - ```size-change```
pageSize改变时会触发，回调参数：每页条数
  - ```current-change```
currentPage改变时会触发，回调参数：当前页
##### Others类型
###### Dialog对话框
在保留当前页面状态的情况下，告知用户并承载相关操作
- 组件属性
  - ```visible.sync```
是否显示Dialog，ElementUI通过这个属性来控制对话框的显示和隐藏

#### Vue路由
##### 概念
###### 前端路由
URL中的 ```hash(#号之后的内容)``` 与组件之间的对应关系
##### Vue Router
Vue Router是Vue的官方路由
- 组成
  - VueRouter
路由器类，根据路由请求在路由视图中动态渲染选中的组件。在路由器类中维护了一份路由表，记录了哈希片段和vue文件的一一对应关系
  - ```<router-link>```
请求链接组件，浏览器会解析成 ```<a>```
  - ```<router-view>```
动态视图组件，用来渲染展示与路由路径对应的组件

##### Vue路由使用方法
###### 第1步==>安装（创建Vue项目时已选择）
```
npm install vue-router@3.5.1
```
###### 第2步==>定义路由
在src-->router-->index.js中定义
- 定义语法
```
  {
    path: '/emp',
    name: 'emp',
    component: () => import('../views/tlias/EmpView.vue')
  }
```
- 重定向语法
即将默认访问页自动跳转到 ```/emp``` ，否则会变为空白页
```
  {
    path: '/',
    redirect: '/emp'
  },
```
###### 第3步==>配置超链接
在对应的vue文件中配置，用 ```<router-link to=""></router>``` 包裹要点击的位置，配置好后，会成为超链接
- 语法
```
<el-menu-item index="1-2">
    <router-link to="/emp">员工管理</router-link>
 </el-menu-item>
```

###### 第4步==>配置View
在App.vue中，删除原先的View配置，增加 ```<router-view></router-view>```
- 语法
```
<router-view></router-view>
```

#### 打包部署
前端工程开发好后，需要发布，发布分为两步
- 前端工程打包
- 通过nginx服务器发布前端工程

##### 前端工程打包
直接通过VS Code的NPM脚本中提供的build按钮来完成

##### 部署
###### Nginx
Nginx是一款轻量级的Web服务器/反向代理服务器及电子邮件（IMAP/POP3）代理服务器。其特点是占有内存少，并发能力强，在各大型互联网公司都有非常广泛的使用
官网https://nginx.org/
###### Nginx目录
- conf
配置文件目录
- html
静态资源文件目录
- logs
日志文件目录
- temp
临时文件目录

###### 第1步==>部署
将打包好的dist目录下的文件，复制到nginx目录下的html目录下
###### 第2步==>启动
双击nginx.exe文件即可
**nginx服务器默认占用80端口号，但是80端口被System占用，需要在conf-->nginx.conf中更改nginx的占用端口**

**查询端口号被占用情况的cmd命令：**
```
netstat -ano | findStr 80
```
###### 第3步==>访问
在浏览器中访问 ```localhost:端口号```


# Web后端开发
## maven
### maven
#### 概念
Maven是apache旗下的一个开源项目，是一款用于管理和构建java项目的工具，它基于项目对象模型（POM,Project object model）的概念，通过一小段描述信息来管理项目的构建
##### Apache软件基金会
成立于1999年7月，是目前世界上最大的最受欢迎的开源软件基金会，也是一个专门为支持开源项目而生的非盈利性组织
开源项目：https://www.apache.org/index.html#projects-list
#### Maven的作用
##### 依赖管理
方便快捷的管理项目依赖的资源(jar包)，避免版本冲突问题
##### 统一项目结构
提供标准、统一的项目结构
##### 项目构建
maven提供了标准的、跨平台(Linux、Windows、MacOS) 的自动化项目构建方式

#### Maven模型
##### 项目对象模型 (Project Object Model)
项目对象模型，就是将我们自己的项目抽象成一个对象模型，有自己专属的坐标
###### 坐标
就是资源(jar包)的唯一标识，通过坐标可以定位到所需资源(jar包)位置
###### 坐标标签
- ```<groupId>```
定义当前Maven项目隶属组织名称（通常是域名反写，例如：com.smiler）
- ```<artifactId>```
定义当前Maven项目名称（通常是模块名称，例如：order-service、goods-service）
- ```<version>```
定义当前项目版本号
##### 依赖管理模型(Dependency)
使用坐标来描述当前项目依赖哪些第三方jar包
在纯Java项目中需要jar包时，直接就把jar包复制到项目下的lib目录，而在Maven中，写在pom.xml文件中的坐标通过Maven仓库找到所需要的jar包文件
##### 构建生命周期/阶段(Build lifecycle & phases)
当需要编译时，Maven提供了一个编译插件供使用；当需要打包时，Maven就提供了一个打包插件供使用

#### Maven仓库
##### 概念
用于存储资源，管理各种jar包
仓库的本质就是一个目录(文件夹)，这个目录被用来存储开发中所有依赖(就是jar包)和插件
##### 分类
- 本地仓库
自己计算机上的一个目录(用来存储jar包)
- 中央仓库
由Maven团队维护的全球唯一的。仓库地址：https://repo1.maven.org/maven2/
- 远程仓库(私服)
一般由公司团队搭建的私有仓库
##### jar包查找顺序
- 没有远程仓库时
当项目中使用坐标引入对应依赖jar包后，首先会查找本地仓库中是否有对应的jar包，如果有，则在项目直接引用；如果没有，则去中央仓库中下载对应的jar包到本地仓库
- 搭建远程仓库(私服)时
jar包的查找顺序则变为： 本地仓库 --> 远程仓库--> 中央仓库

#### Maven安装
##### 第1步==>下载Maven安装包
##### 第2步==>解压安装
###### 解压后的目录结构
- bin目录
存放的是可执行命令（mvn命令需要重点关注）
- conf目录
存放Maven的配置文件（settings.xml配置文件后期需要修改）
- lib目录
存放Maven依赖的jar包（Maven也是使用java开发的，所以它也依赖其他的jar包）
##### 第3步==>配置仓库
- 第3.1步===>在自己计算机上新建一个目录（本地仓库，用来存储jar包），命名一般是mvn_repo
- 第3.2步===>进入到conf目录下修改settings.xml配置文件
  - 第3.2.1步====>使用记事本打开settings.xml文件，定位到53行
  - 第3.2.2步====>复制标签，粘贴到注释的外面（55行）
  - 第3.2.3步====>复制之前新建的用来存储jar包的路径，替换掉标签体内容
- 第3.3步===>配置阿里云私服
由于中央仓库在国外，所以下载jar包速度可能比较慢，而阿里公司提供了一个远程仓库，里面基本也都有开源项目的jar包
进入到conf目录下修改settings.xml配置文件：
  - 第3.3.1步====>使用记事本软件打开settings.xml文件，定位到160行左右
  - 第3.3.2步====>在标签下为其添加子标签，内容如下：
```
<mirror>
    <id>alimaven</id>
    <name>aliyun maven</name>
    <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    <mirrorOf>central</mirrorOf>
</mirror>
```
**注意：只可配置一个(另一个要注释!) ，不然两个可能发生冲突，导致jar包无法下载**
##### 第4步==>配置Maven环境变量
Maven环境变量的配置类似于JDK环境变量配置一样
- 第4.1步===>在系统变量处新建一个变量 ```MAVEN_HOME```
```MAVEN_HOME``` 环境变量的值，设置为maven的解压安装目录
- 第4.2步===>在Path中进行配置
PATH环境变量的值，设置为：```%MAVEN_HOME%\bin```
- 第4.3步===>打开DOS命令提示符进行验证，出现如图所示表示安装成功
指令为 ```mvn -v``

#### 依赖管理
##### 依赖配置
- 依赖
指当前项目运行所需要的jar包。一个项目中可以引入多个依赖
- 引入依赖的具体步骤
  - 第1步：在pom.xml中编写标签
  - 第2步：在标签中使用引入坐标
  - 第3步：定义坐标的 groupId、artifactId、version
  - 第4步：点击刷新按钮，引入最新加入的坐标
- 语法
```
    <dependencies>
        <dependency>
            <groupId>jar包路径</groupId>
            <artifactId>jar包包名</artifactId>
            <version>版本号</version>
        </dependency>
    </dependencies>
```
例如：
```
    <dependencies>
        <dependency>
            <groupId>ch.qos.logback</groupId>
            <artifactId>logback-classic</artifactId>
            <version>1.2.11</version>
        </dependency>
    </dependencies>
```
- 刷新依赖
保证每一次引入新的依赖，或者修改现有的依赖配置，都可以加入最新的坐标
- 注意事项
  - 如果引入的依赖，在本地仓库中不存在，将会连接远程仓库 / 中央仓库，然后下载依赖（这个过程会比较耗时）
  - 如果不知道依赖的坐标信息，可以到mvn的中央仓库（https://mvnrepository.com/）中搜索
- 添加依赖的几种方式
  - 利用中央仓库搜索的依赖坐标
  - 利用IDEA工具搜索依赖
  - 熟练上手maven后，快速导入依赖
##### 依赖传递
依赖具有传递性，早期我们没有使用maven时，向项目中添加依赖的jar包，需要把所有的jar包都复制到项目工程下，现在使用了maven，当项目中需要使用logback-classic时，只需要在pom.xml配置文件中，添加logback-classic的依赖坐标即可

在pom.xml文件中只添加了logback-classic依赖，但由于maven的依赖具有传递性，所以会自动把所依赖的其他jar包也一起导入
- 依赖传递分类
  - 直接依赖
在当前项目中通过依赖配置建立的依赖关系
  - 间接依赖
被依赖的资源如果依赖其他资源，当前项目间接依赖其他资源
- 排除依赖
指主动断开依赖的资源。（被排除的资源无需指定版本）
- 语法
```
    <exclusions>
       <exclusion>
            <groupId>jar包名</groupId>
            <artifactId>jar包名</artifactId>
       </exclusion>
    </exclusions>
```
##### 依赖范围
在项目中导入依赖的jar包后，默认情况下，可以在任何地方使用
如果希望限制依赖的使用范围，可以通过标签设置其作用范围
- 作用范围
  - 主程序范围有效（main文件夹范围内）
  - 测试程序范围有效（test文件夹范围内）
  - 是否参与打包运行（package指令范围内）
在pom.xml中通过scope标签指定依赖的作用范围
- scope标签的取值范围
  - compile（默认）
范围：主程序、测试程序、打包（运行）
例如：log4j
  - test
范围：测试程序
例如：junit
  - provided
范围：主程序、测试程序
例如：servlet-api
  - runtime
范围：测试程序、打包（运行）
例如：jdbc驱动
##### 生命周期
Maven对项目构建的生命周期划分为3套（相互独立）
- clean
清理工作
具体阶段包括:
  - pre-clean
  - clean
移除上一次构建生成的文件
  - post-clean
- default
核心工作，包括编译、测试、打包、安装、部署等
具体阶段包括:
  - validate
  - initialize
  - generate-sources
  - process-sources
  - generate-resources
  - process-resources
  - compile
编译项目源代码
  - process-classes
  - generate-test-sources
  - process-test-sources
  - generate-test-resources
  - process-test-resources
  - test-compile
  - process-test-classes
  - test
使用合适的单元测试框架运行测试（junit）
  - prepare-package
  - package
将编译后的文件打包，如：jar、war等
  - verify
  - install
安装项目到本地仓库
  - deploy
- site
生成报告、发布站点等
具体阶段包括:
  - pre-site
  - site
  - post-site
  - site-deploy

**Maven的生命周期是抽象的，这意味着生命周期本身不做任何实际工作。在Maven的设计中，实际任务（如源代码编译）都交由插件来完成**

**在同一套生命周期中，执行后面的生命周期时，前面的生命周期都会执行**

- 执行方式
  - 方式一
在idea工具右侧的maven工具栏中，选择对应的生命周期，双击执行
  - 方式二
在DOS命令行中，通过maven命令执行，例如：```mvn clean```


## SpringBoot
### 基本概念
#### Spring
Spring发展到今天已经形成了一种开发生态圈，Spring提供了若干个子项目，每个项目用于完成特定的功能。在项目开发时，一般会偏向于选择这一套spring家族的技术，来解决对应领域的问题，我们称这一套技术为spring全家桶
##### SpringFramework
Spring家族旗下这么多的技术，最基础、最核心的是SpringFramework。其他的spring家族的技术，都是基于SpringFramework的，SpringFramework中提供很多实用功能，如：依赖注入、事务管理、web开发支持、数据访问、消息服务等等
- 而如果我们在项目中，直接基于SpringFramework进行开发，存在两个问题
  - 配置繁琐
  - 入门难度大
##### Springboot
Spring Boot可以帮助我们非常快速的构建应用程序、简化开发、提高效率
- springboot最大的特点有两个
  - 简化配置
  - 快速开发

### SpringBootWeb快速入门
#### 开发步骤
##### 第1步：创建SpringBoot工程项目
- 方法1
新建工程或模块，选择Spring Initializr，仅支持旗舰版Idea
- 方法2
在下面的网址中创建
https://start.spring.io/
- 方法3
用插件创建，例如：SpringBoot-Gen（免费）
**特别注意：
pom.xml中的版本号，有的版本不带Release，例如3.1.4，版本号是```<version>3.1.4</version>```**
##### 第2步：定义HelloController类，添加方法hello，并添加注解
```
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.RequestMapping;

@RestController
public class HelloController {

    @RequestMapping("Hello")
    public String Hello(){
        System.out.println("Hello on console");
        return "Hello on web";
    }
}
```
如果Idea无法识别包，需要进行下面的操作
- 第1步：
在首选项中Build-->Build Tools-->Maven-->Runner中勾选Delegate IDE build/run actions to Maven
- 第2步：
在pom.xml中把 ```<artifactId>spring-boot-starter</artifactId>``` 改成 ```<artifactId>spring-boot-starter-web</artifactId>```

##### 第3步：测试运行

#### Web分析
##### 浏览器
输入网址： http://192.168.100.11:8080/hello
- 通过IP地址192.168.100.11定位到网络上的一台计算机
- 通过端口号8080找到计算机上运行的程序
- ```/hello```是请求资源位置
  - 资源
对计算机而言资源就是数据
  - web资源
通过网络可以访问到的资源（通常是指存放在服务器上的数据）
##### 服务器（可以理解为ServerSocket）
- 接收到浏览器发送的信息（如：```/hello```）
- 在服务器上找到 ```/hello``` 的资源
- 把资源发送给浏览器
##### 浏览器和服务器两端进行数据交互，使用http协议

### HTTP协议
#### HTTP概述
##### 概念
HTTP：Hyper Text Transfer Protocol(超文本传输协议)，规定了浏览器与服务器之间数据传输的规则
*http是互联网上应用最为广泛的一种网络协议*
##### http协议要求
浏览器在向服务器发送请求数据时，或是服务器在向浏览器发送响应数据时，都必须按照固定的格式进行数据传输

##### http特点
- 基于TCP协议
面向连接，安全
TCP是一种面向连接的(建立连接之前是需要经过三次握手)、可靠的、基于字节流的传输层通信协议，在数据传输方面更安全
- 基于请求-响应模型
一次请求对应一次响应（先请求后响应）
请求和响应是一一对应关系，没有请求，就没有响应
- HTTP协议是无状态协议
对于数据没有记忆能力。每次请求-响应都是独立的
无状态指的是客户端发送HTTP请求给服务端之后，服务端根据请求响应数据，响应完后，不会记录任何信息
  - 缺点: 多次请求间不能共享数据
  - 优点: 速度快

请求之间无法共享数据会引发的问题：
如：京东购物。加入购物车和去购物车结算是两次请求
- 由于HTTP协议的无状态特性，加入购物车请求响应结束后，并未记录加入购物车是何商品。发起去购物车结算的请求后，因为无法获取哪些商品加入了购物车，会导致此次请求无法正确展示数据
- 但是具体使用的时候，我们发现京东是可以正常展示数据的，原因是Java早已考虑到这个问题，并提出了使用会话技术(Cookie、Session)来解决这个问题

#### HTTP-请求协议
浏览器和服务器是按照HTTP协议进行数据通信的
HTTP协议又分为：请求协议和响应协议
##### 请求协议
浏览器将数据以请求格式发送到服务器
包括：
- 请求行
- 请求头
- 请求体
##### 响应协议
服务器将数据以响应格式返回给浏览器
包括：
- 响应行
- 响应头
- 响应体

##### 在HTTP1.1版本中，浏览器访问服务器的几种方式
###### GET
获取资源
向特定的资源发出请求。例如：http://www.baidu.com/s?wd=itheima
###### POST
传输实体主体。
向指定资源提交数据进行处理请求（例如：上传文件），数据被包含在请求体中
###### OPTIONS
返回服务器针对特定资源所支持的HTTP请求方式
因为并不是所有的服务器都支持规定的方法，为了安全有些服务器可能会禁止掉一些方法，例如：DELETE、PUT等。那么OPTIONS就是用来询问服务器支持的方法
###### HEAD
获得报文首部
HEAD方法类似GET方法，但是不同的是HEAD方法不要求返回数据。通常用于确认
URI的有效性及资源更新时间等
###### PUT
传输文件
PUT方法用来传输文件。类似FTP协议，文件内容包含在请求报文的实体中，然后请求保存到URL指定的服务器位置
###### DELETE
删除文件
请求服务器删除Request-URI所标识的资源
###### TRACE
追踪路径
回显服务器收到的请求，主要用于测试或诊断
###### CONNECT
要求用隧道协议连接代理
HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器

实际应用中常用的也就是GET和POST

##### GET方式的请求协议
```
GET /brand/findAll?name=OPPO&status=1 HTTP/1.1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*
Accept-Encoding: gzip,deflate, br
Accept-Language: zh-CN,zh;q=0.9
Host: localhost:8080
User-Agent:Mozilla/5.0(Windows NT 10.0; Win64; x64)AppleWebKit/537.36(KHTML,like Gecko)Chrome/...
```
###### 请求行
HTTP请求中的第一行数据。由：请求方式、资源路径、协议/版本 组成（之间使用空格分隔）
- 请求方式
GET 
- 资源路径
/brand/findAll?name=OPPO&status=1
- 请求路径
/brand/findAll
- 请求参数
name=OPPO&status=1
请求参数是以key=value形式出现，多个请求参数之间使用&连接，请求路径和请求参数之间使用?连接
- 协议/版本
HTTP/1.1

###### 请求头
第二行开始，就是请求头。格式为key: value形式
http是个无状态的协议，所以在请求头设置浏览器的一些自身信息和想要响应的形式。这样服务器在收到信息后，就可以知道是谁，想干什么了
常见的HTTP请求头有:
- Host
表示请求的主机名
- User-Agent
浏览器版本。 例如：
  - Chrome浏览器的标识类似Mozilla/5.0...Chrome/79 
  - IE浏览器的标识类似Mozilla/5.0 (Windows NT ...)likeGecko
- Accept
表示浏览器能接收的资源类型，如text/*，image/*或者*/*表示所有
- Accept-Language
表示浏览器偏好的语言，服务器可以据此返回不同语言的网页
- Accept-Encoding
表示浏览器可以支持的压缩类型，例如gzip, deflate等
- Content-Type
请求主体的数据类型
- Content-Length
数据主体的大小（单位：字节）

服务端可以根据请求头中的内容来获取客户端的相关信息，有了这些信息服务端就可以处理不同的业务需求
例如:
- 不同浏览器解析HTML和CSS标签的结果会有不一致，所以就会导致相同的代码在不同的浏览器会出现不同的效果
- 服务端根据客户端请求头中的数据获取到客户端的浏览器类型，就可以根据不同的浏览器设置不同的代码来达到一致的效果（这就是我们常说的浏览器兼容问题）

###### 请求体
存储请求参数。GET请求的请求参数在请求行中，故不需要设置请求体

##### POST方式的请求协议
```
POST /brand HTTP/1.1
Accept: application/json, text/plain,*/*
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Content-Length: 161
Content-Type: application/json;charset=UTF-8
Cookie:Idea-8296eb32=841b16f0-0cfe-495a-9cc9-d5aaa71501a6; JSESSIONID=OFDE4E430876BD9C5C955F061207386F
Host: localhost:8080
User-Agent: Mozilla/5.0(Windows NT 10.0; Win64; x64)AppleNebkit/537.36(KHTML,like Gecko) Chrome/...

{"status":1,"brandName":"黑马","companyName":"黑马程序员","id":"","description":"黑马程序员"}
```

###### 请求行
上面第一行：包含请求方式、资源路径、协议/版本
- 请求方式：POST
- 资源路径：/brand
- 协议/版本：HTTP/1.1
###### 请求头
上面除去第一行和最后一行
###### 请求体
上面最后一行，用来存储请求参数
请求体和请求头之间是有一个空行隔开（作用：用于标记请求头结束）


##### GET请求和POST请求的区别
###### 请求参数
- GET请求
请求参数在请求行中。例如：/brand/findAll?name=OPPO&status=1
- POST请求
请求参数在请求体中
###### 请求参数长度
- GET请求
请求参数长度有限制(浏览器不同限制也不同)
- POST请求
请求参数长度没有限制
###### 安全性
- GET请求
安全性低。原因：请求参数暴露在浏览器地址栏中
- POST请求
安全性相对高

#### HTTP-响应协议
与HTTP的请求一样，HTTP响应的数据也分为3部分：响应行、响应头 、响应体
```
HTTP/1.1200 OK
Content-Type: application/json
Transfer-Encoding: chunked
Date: Tue,10 May 202207:51:07 GMT
Keep-Alive: timeout=60
Connection: keep-alive

[{id:1, brandName:"阿里巴巴",companyName:"腾讯计算机系统有限公司",description:"玩玩玩"}]
```
##### 响应行
(上面第一行)
响应数据的第一行。响应行由 协议及版本 、 响应状态码、 状态码描述 组成
- 协议/版本：HTTP/1.1
- 响应状态码：200
- 状态码描述：OK
##### 响应头
(上面除第一行和最后一行)
响应数据的第二行开始。格式为key：value形式
http是个无状态的协议，所以可以在请求头和响应头中设置一些信息和想要执行的动作，这样，对方在收到信息后，就可以知道你是谁，你想干什么
常见的HTTP响应头有:
###### Content-Type
表示该响应内容的类型，例如text/html，image/jpeg
###### Content-Length
表示该响应内容的长度（字节数）
###### Content-Encoding
表示该响应压缩算法，例如gzip 
###### Cache-Control
指示客户端应如何缓存，例如max-age=300表示可以最多缓存300秒 
###### Set-Cookie
告诉浏览器为当前页面所在的域设置cookie
##### 响应体
(上面最后一行)
响应数据的最后一部分。存储响应的数据
响应体和响应头之间有一个空行隔开（作用：用于标记响应头结束）


##### 响应状态码
- 1xx
响应中 --- 临时状态码。表示请求已经接受，告诉客户端应该继续请求或者如果已经完成则忽略
- 2xx
成功 --- 表示请求已经被成功接收，处理已完成
- 3xx
重定向 --- 重定向到其它地方，让客户端再发起一个请求以完成整个处理
- 4xx
客户端错误 --- 处理发生错误，责任在客户端，如：客户端的请求一个不存在的资源，客户端未被授权，禁止访问等
- 5xx
服务器端错误 --- 处理发生错误，责任在服务端，如：服务端抛出异常，路由出错，HTTP版本不支持等

常见响应状态码
- 200 ok 客户端请求成功
- 404 Not Found 请求资源不存在
- 500 Internal Server Error 服务端发生不可预期的错误


### WEB服务器-Tomcat
#### 概述
##### 服务器概述
###### 服务器硬件
指的也是计算机，只不过服务器要比我们日常使用的计算机大很多

服务器，也称伺服器。是提供计算服务的设备。由于服务器需要响应服务请求，并进行处理，因此一般来说服务器应具备承担服务并且保障服务的能力

服务器的构成包括处理器、硬盘、内存、系统总线等，和通用的计算机架构类似，但是由于需要提供高可靠的服务，因此在处理能力、稳定性、可靠性、安全性、可扩展性、可管理性等方面要求较高

在网络环境下，根据服务器提供的服务类型不同，可分为：文件服务器，数据库服务器，应用程序服务器，WEB服务器等

服务器只是一台设备，必须安装服务器软件才能提供相应的服务

###### 服务器软件
基于ServerSocket编写的程序
- 服务器软件本质是一个运行在服务器设备上的应用程序
- 能够接收客户端请求，并根据请求给客户端响应数据

##### Web服务器
Web服务器是一个应用程序(软件)，对HTTP协议的操作进行封装，使得程序员不必直接对协议进行操作(不用程序员自己写代码去解析http协议规则)，让Web开发更加便捷。主要功能是"提供网上信息浏览服务"

Web服务器是安装在服务器端的一款软件，Web项目部署到Tomcat服务器软件中，当Web服务器软件启动后，部署在Web服务器软件中的页面就可以直接通过浏览器来访问了
###### Web服务器软件使用步骤
- 第1步：准备静态资源
- 第2步：下载安装Web服务器软件
- 第3步：将静态资源部署到Web服务器上
- 第4步：启动Web服务器使用浏览器访问对应的资源

#### Tomcat
##### 概念
- Tomcat服务器软件是一个免费的开源的web应用服务器。是Apache软件基金会的一个核心项目。由Apache，Sun和其他一些公司及个人共同开发而成
- 由于Tomcat只支持Servlet/JSP少量JavaEE规范，所以是一个开源免费的轻量级Web服务器

*JavaEE规范： JavaEE => Java Enterprise Edition(Java企业版)*
JavaEE规范就是指Java企业级开发的技术规范总和。包含13项技术规范：JDBC、JNDI、EJB、RMI、JSP、Servlet、XML、JMS、Java IDL、JTS、JTA、JavaMail、JAF

- 因为Tomcat支持Servlet/JSP规范，所以Tomcat也被称为Web容器、Servlet容器。JavaWeb程序需要依赖Tomcat才能运行

- Tomcat的官网: https://tomcat.apache.org/

##### 基本使用
###### 下载
直接从官方网站下载：https://tomcat.apache.org/download-90.cgi
Tomcat软件类型说明：
- tar.gz文件
是linux和mac操作系统下的压缩版本
- zip文件
是window操作系统下压缩版本
###### 目录结构
- bin
可执行文件。bin目录下有两类文件，一种是以.bat结尾的，是Windows系统的可执行文件，一种是以.sh结尾的，是Linux系统的可执行文件
- conf
配置文件
- lib
Tomcat依赖的jar包
- logs
日志文件
- temp
临时文件
- webapps
应用发布目录，即项目部署的目录
- work
工作目录

###### 启动Tomcat
双击tomcat解压目录/bin/startup.bat文件即可启动tomcat
**注意: tomcat服务器启动后,黑窗口不会关闭,只要黑窗口不关闭,就证明tomcat服务器正在运行**
- Tomcat的默认端口为8080，所以在浏览器的地址栏输入： http://127.0.0.1:8080 即可访问tomcat服务器

  - **127.0.0.1 也可以使用localhost代替。如： http://localhost:8080**

能看到Apache Tomcat的欢迎内容就说明Tomcat已经启动成功

- Tomcat启动的过程中，遇到控制台有中文乱码时，可以通常修改conf/logging.prooperties文件解决
  - 将第51行的java.util.logging.ConsoleHandler.encoding = UTF-8改为GBK

###### 关闭Tomcat
有三种关闭方法
- 强制关闭：直接x掉Tomcat窗口（不建议）
- 正常关闭：双击bin\shutdown.bat
- 正常关闭：在Tomcat启动窗口中按下 Ctrl+C，如果按下Ctrl+C没有反应，可以多按几次

##### 常见问题
###### 问题1：Tomcat启动时，窗口一闪而过
检查JAVA_HOME环境变量是否正确配置
###### 问题2：端口号冲突
- 发生问题的原因：Tomcat使用的端口被占用了
- 解决方案：换Tomcat端口号
要想修改Tomcat启动的端口号，需要修改 conf/server.xml文件

**注意: HTTP协议默认端口号为80，如果将Tomcat端口号改为80，则将来访问Tomcat时，将不用输入端口号**

#### Spring与Tomcat
##### 起步依赖
在SpringBoot的项目中，有很多的起步依赖，他们有一个共同的特征：就是以 spring-boot-starter- 作为开头
例如：
###### spring-boot-starter-web
spring-boot-starter-web内部把关于Web开发所有的依赖都已经导入并且指定了版本，只需引入 spring-boot-starter-web 依赖就可以实现Web开发的需要的功能

**Spring的官方提供了很多现成的starter(起步依赖)，我们在开发相关应用时，只需要引入对应的starter即可**

##### SpringBoot父工程
通过maven引入的依赖，是没有指定具体的依赖版本号的。因为每一个SpringBoot工程，都有一个父工程。依赖的版本号，在父工程中统一管理

##### 内嵌Tomcat
在SpringBoot中，引入web运行环境(即引入spring-boot-starter-web起步依赖)后，其内部已经集成了内置的Tomcat服务器，在SpringBoot中可以直接使用Tomcat服务器


### SpringBootWeb请求响应
其实在Tomcat这类Web服务器中，是不识别我们自己定义的Controller的。但是Tomcat是一个Servlet容器，是支持Serlvet规范的，所以在tomcat中是可以识别Servlet程序的。

那我们所编写的XxxController 是如何处理请求的，又与Servlet之间有什么联系呢？

在SpringBoot进行web程序开发时，它内置了一个核心的Servlet程序DispatcherServlet，称之为 核心控制器。DispatcherServlet负责接收页面发送的请求，然后根据执行的规则，将请求再转发给后面的请求处理器Controller，请求处理器处理完请求之后，最终再由DispatcherServlet给浏览器响应数据

浏览器发送请求，会携带请求数据，包括：请求行、请求头；请求到达tomcat之后，tomcat会负责解析这些请求数据，然后将解析后的请求数据传递给Servlet程序的HttpServletRequest对象，HttpServletRequest对象就可以获取到请求数据。而Tomcat，还给Servlet程序传递了一个参数 HttpServletResponse，通过这个对象，我们就可以给浏览器设置响应数据

浏览器/服务器的架构模式，称为：BS架构(Browser/Server)，浏览器/服务器架构模式。客户端只需要浏览器，应用程序的逻辑和数据都存储在服务端

#### 请求
##### Postman
前后端分离开发模式中，对后端技术人员来讲，在开发过程中，是没有前端页面的，可以用下面的方式测试自己所开发的程序
###### 方式1
直接使用浏览器。在浏览器中输入地址，测试后端程序
- 弊端：在浏览器地址栏中输入地址这种方式都是GET请求，要解决POST请求，需要程序员自己编写前端代码（比较麻烦）
###### 方式2
使用专业的接口测试工具，例如：Postman

###### Postman简介
Postman是一款功能强大的网页调试与发送网页HTTP请求的Chrome插件

**Postman原是Chrome浏览器的插件，可以模拟浏览器向后端服务器发起任何形式(如:get、post)的HTTP请求**

使用Postman还可以在发起请求时，携带一些请求参数、请求头等信息

###### 作用
常用于进行接口测试
###### 特点
简单、实用、美观、大方

##### 简单参数
在向服务器发起请求时，向服务器传递的是一些普通的请求数据
后端程序中，接收传递过来的普通参数数据的方式：
###### 原始方式
- 在原始的Web程序当中，需要通过Servlet中提供的API：HttpServletRequest（请求对象），获取请求的相关信息
- Tomcat接收到http请求时：把请求的相关信息封装到HttpServletRequest对象中
- 在Controller中，我们要想获取Request对象，可以直接在方法的形参中声明HttpServletRequest 对象。然后就可以通过该对象来获取请求信息
```
//根据指定的参数名获取请求参数的数据值
String request.getParameter("参数名")
```
例如：
```
@RestController
public class RequestController {
    //原始方式
    @RequestMapping("/simpleParam")
    public String simpleParam(HttpServletRequest request){
       // http://localhost:8080/simpleParam?name=Tom&age=10
       // 请求参数： name=Tom&age=10 （有2个请求参数）
       // 第1个请求参数： name=Tom 参数名:name，参数值:Tom
       // 第2个请求参数： age=10 参数名:age , 参数值:10
       String name = request.getParameter("name");//name就是请求参数名
       String ageStr = request.getParameter("age");//age就是请求参数名
       int age = Integer.parseInt(ageStr);//需要手动进行类型转换
       System.out.println(name+" : "+age);
       return "OK";
   }
}
```

###### SpringBoot方式
在Springboot的环境中，对原始的API进行了封装，接收参数的形式更加简单。 如果是简单参数，参数名与形参变量名相同，定义同名的形参即可接收参数
例如：
```
    @RestController
    public class RequestController {
       // http://localhost:8080/simpleParam?name=Tom&age=10
       // 第1个请求参数： name=Tom 参数名:name，参数值:Tom
       // 第2个请求参数： age=10 参数名:age , 参数值:10
       //springboot方式
       @RequestMapping("/simpleParam")
       public String simpleParam(String name , Integer age ){//形参名和
       请求参数名保持一致
       System.out.println(name+" : "+age);
       return "OK";
    }
}
```
不论是GET请求还是POST请求，对于简单参数来讲，只要保证 请求参数名和Controller方法中的形参名保持一致 ，就可以获取到请求参数中的数据值

###### 参数名不一致
对于简单参数来讲，请求参数名和controller方法中的形参名不一致时，无法接收到请求数据，但是不会报错，数据会显示为null

解决请求参数名和controller方法中的形参名不相同时，无法接受到请求数据的问题，可以使用Spring提供的@RequestParam注解完成映射
在方法形参前面加上 @RequestParam 然后通过value属性执行请求参数名，从而完成映射
例如：
```
    @RestController
    public class RequestController {
       // http://localhost:8080/simpleParam?name=Tom&age=10
       // 第1个请求参数： name=Tom 参数名:name，参数值:Tom
       // 第2个请求参数： age=10 参数名:age , 参数值:10
       //springboot方式
       @RequestMapping("/simpleParam")
       public String simpleParam((@RequestParam("name") String username , Integer age ){//形参名和
       请求参数名保持一致
       System.out.println(username+" : "+age);
       return "OK";
    }
}
```
*注意事项：*
* ```@RequestParam``` 中的required属性默认为true（默认值也是true），代表该请求参数必须传递，如果不传递将报错。如果该参数是可选的，可以将required属性设置为false*

##### 复杂实体对象
复杂实体对象指的是，在实体类中有一个或多个属性，也是实体对象类型的。例如：User类中有一个Address类型的属性（Address是一个实体类）

复杂实体对象的封装，需要遵守如下规则：
请求参数名与形参对象属性名相同，按照对象层次结构关系即可接收嵌套实体类属性参数

##### 数组集合参数
数组集合参数的使用场景：在HTML的表单中，有一个表单项是支持多选的(复选框)，可以提交选择的多个值
多个值也是一个一个的提交
后端程序接收上述多个值的方式有两种：
###### 数组
- 数组参数
请求参数名与形参数组名称相同且请求参数为多个，定义数组类型形参即可接收参数
- Controller方法
例如：
```
@RestController
public class RequestController {
     //数组集合参数
     @RequestMapping("/arrayParam")
     public String arrayParam(String[] hobby){
         System.out.println(Arrays.toString(hobby));
         return "OK";
    }
}
```
- Postman测试
在前端请求时，有两种传递形式

| 方式   | URL 示例                                | 说明                         |
|:----------|:-----------------------------------------|:--------------------------|
| 方式 1   | `xxxxxxxxxx?hobby=game&hobby=java`        | 使用多个相同参数名拼接，表示多个值 |
| 方式 2   | `xxxxxxxxxxxxx?hobby=game,java`            | 使用逗号分隔，一个参数对应多个值   |


###### 集合
- 集合参数
请求参数名与形参集合对象名相同且请求参数为多个，使用@RequestParam 绑定参数关系

**默认情况下，请求中参数名相同的多个值，是封装到数组。如果要封装到集合，要使用@RequestParam绑定参数关系**

- Controller方法
例如：
```
@RestController
public class RequestController {
     //数组集合参数
     @RequestMapping("/listParam")
     public String listParam(@RequestParam List<String> hobby){
         System.out.println(hobby);
         return "OK";
    }
}
```
- Postman测试
在前端请求时，有两种传递形式

| 方式   | URL 示例                                |
|:---------|:-----------------------------------------|
| 方式 1   | xxxxxxxxxx?hobby=game&hobby=java         |
| 方式 2   | xxxxxxxxxxxxx?hobby=game,java            |


##### 日期参数
在一些特殊的需求中，可能会涉及到日期类型数据的封装
因为日期的格式多种多样，那么对于日期类型的参数在进行封装的时候，需要通过@DateTimeFormat注解，以及其pattern属性来设置日期的格式
###### 格式要求
- @DateTimeFormat注解的pattern属性中指定了哪种日期格式，前端的日期参数就必须按照指定的格式传递
- 后端controller方法中，需要使用Date类型或LocalDateTime类型，来封装传递的参数
###### Controller方法
```
@RestController
public class RequestController {
    //日期时间参数
    @RequestMapping("/dateParam")
    public String dateParam(@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss") LocalDateTime updateTime){
    System.out.println(updateTime);
    return "OK";
    }
}
```
###### Postman测试
```
localhost:8080/dateParam?updateTime=2023-10-02 10:23:51
```
##### JSON参数
在前后端进行交互时，如果是比较复杂的参数，前后端通过JSON格式的数据进行传输（JSON是开发中最常用的前后端数据交互方式）
###### Postman发送JSON格式数据
- 请求方式只能使用POST
- 在Body中选择raw，然后选择JSON
- JSON格式为
```
{"属性1":"值1","属性2":"值2",..."属性n":{"属性n1":"值n1","属性n2":"值n2"}}
```
例如：
```
{
    "name":"Tom",
    "age":23,
    "address":{
    "county":"Tyne and Wear",
    "city":"Newcastle upon Tyne"
    }
}
```

###### 服务端Controller方法接收JSON格式数据
- 传递json格式的参数，在Controller中使用实体类进行封装
- 封装规则：JSON数据键名与形参对象属性名相同，定义POJO类型形参即可接收参数。需要使用@RequestBody标识
- @RequestBody注解：将JSON数据映射到形参的实体类对象中（JSON中的key和实体类中的属性名保持一致）

例如：
实体类：Address
```
public class Address {
    private String province;
    private String city;
    //省略GET , SET 方法
}
```
实体类：User
```
public class User {
    private String name;
    private Integer age;
    private Address address;
    //省略GET , SET 方法
}
```
Controller方法：
```
@RestController
public class RequestController {
    //JSON参数
    @RequestMapping("/jsonParam")
    public String jsonParam(@RequestBody User user){
        System.out.println(user);
        return "OK";
    }
}
```

##### 路径参数
传统的开发中请求参数是放在请求体(POST请求)传递或跟在URL后面通过?key=value的形式传递(GET请求)
在现在的开发中，经常还会直接在请求的URL中传递参数。例如：
http://localhost:8080/user/1 
http://localhost:880/user/1/0
上述的这种传递请求参数的形式称为：路径参数
###### 路径参数
- 前端
通过请求URL直接传递参数
- 后端
使用{…}来标识该路径参数，需要使用@PathVariable获取路径参数

###### 传递单个参数
- 服务端Controller方法
```
@RestController
public class RequestController {
    //路径参数
    @RequestMapping("/path/{id}")
    public String pathParam(@PathVariable Integer id){
        System.out.println(id);
        return "OK";
    }
}
```
- Postman测试
http://localhost:8080/path/1

###### 传递多个参数
- 服务端Controller方法
```
@RestController
public class RequestController {
    //路径参数
    @RequestMapping("/path/{name}/{age}")
    public String pathParam2(@PathVariable String name, @PathVariable Integer age){
        System.out.println("name:" + name + "\tage:" + age);
        return "OK";
    }
}
```
- Postman测试
http://localhost:8080/path/Tom/20


#### 响应
HTTL协议的交互方式：请求响应模式（有请求就有响应）。那么Controller程序，除了接收请求外，还可以进行响应
##### ```@ResponseBody```
controller方法中的return的结果，使用@ResponseBody注解就可以响应给浏览器

###### ```@ResponseBody```注解
- 类型
方法注解、类注解
- 位置
书写在Controller方法上或类上
- 作用
将方法返回值直接响应给浏览器
  - 如果返回值类型是实体对象/集合，将会转换为JSON格式后在响应给浏览器

*在书写Controller时，在类上添加@RestController注解就可以给浏览器相应，并不用使用@ResponseBody注解*
- *原因：在类上添加的@RestController注解，是一个组合注解*
- *```@RestController = @Controller + @ResponseBody```*

@RestController源码：
```
  @Target({ElementType.TYPE}) //元注解（修饰注解的注解）
  @Retention(RetentionPolicy.RUNTIME) //元注解
  @Documented //元注解
  @Controller
  @ResponseBody
  public @interface RestController {
      @AliasFor(
          annotation = Controller.class
      )
      String value() default "";
  }
```
**类上有@RestController注解或@ResponseBody注解时：表示当前类下所有的方法返回值做为响应数据方法的返回值，如果是一个POJO对象或集合时，会先转换为JSON格式，在响应给浏览器**

##### 统一响应结果
在前面所编写的这些Controller方法中，返回值各种各样，没有任何的规范。开发一个大型项目，项目中controller方法将成千上万，使用上述方式将造成整个项目难以维护
在真实的项目开发中，无论是哪种方法，我们都会定义一个统一的返回结果
在后端会定义一个实体类Result来统一返回结果的格式，前端只需要按照统一格式的返回结果进行解析(仅一种解析方案)，就可以拿到数据

###### 统一的返回结果使用类来描述，在这个结果中包含：
- 响应状态码
当前请求是成功，还是失败
- 状态码信息
给页面的提示信息
- 返回的数据
给前端响应的数据（字符串、对象、集合）

###### Result代码如下：
```
public class Result {
    private Integer code;//响应码，1 代表成功; 0 代表失败
    private String msg; //响应码 描述字符串
    private Object data; //返回的数据

    public Result() { }
    public Result(Integer code, String msg, Object data) {
        this.code = code;
        this.msg = msg;
        this.data = data;
    }

    //增删改 成功响应(不需要给前端返回数据)
    public static Result success(){
        return new Result(1,"success",null);
    }
    //查询 成功响应(把查询结果做为返回数据响应给前端)
    public static Result success(Object data){
        return new Result(1,"success",data);
    }
    //失败响应
    public static Result error(String msg){
        return new Result(0,msg,null);
    }

    public Integer getCode() {
        return code;
    }
    public void setCode(Integer code) {
        this.code = code;
    }
    public String getMsg() {
        return msg;
    }
    public void setMsg(String msg) {
        this.msg = msg;
    }
    public Object getData() {
        return data;
    }
    public void setData(Object data) {
        this.data = data;
    }

}
```

#### 分层解耦
##### 三层架构
###### 概念
在我们进行程序设计以及程序开发时，尽可能让每一个接口、类、方法的职责更单一些（单一职责原则）

**单一职责原则：一个类或一个方法，就只做一件事情，只管一块功能。这样就可以让类、接口、方法的复杂度更低，可读性更强，扩展性更好，也更利用后期的维护**

项目开发中，可以将代码分为三层：
- Controller
控制层。接收前端发送的请求，对请求进行处理，并响应数据
- Service
业务逻辑层。处理具体的业务逻辑
- Dao
数据访问层(Data Access Object)，也称为持久层。负责数据访问操作，包括数据的增、删、改、查

###### 基于三层架构的程序执行流程
- 前端发起的请求，由Controller层接收（Controller响应数据给前端）
- Controller层调用Service层来进行逻辑处理（Service层处理完后，把处理结果返回给Controller层）
- Serivce层调用Dao层（逻辑处理过程中需要用到的一些数据要从Dao层获取）
- Dao层操作文件中的数据（Dao拿到的数据会返回给Service层）

###### 代码拆分
- 控制层（Controller）
接收前端发送的请求，对请求进行处理，并响应数据
  - 包名：```xxxx.controller```
  - 初始化一个Service层对象作为私有成员变量
  - 调用Service层, 获取数据
- 业务逻辑层(Service)
处理具体的业务逻辑
  - 包名：```xxxx.service```
  - 一个业务接口
  - 一个业务实现类
  - 业务实现类中初始化一个Dao层对象作为私有成员变量
  - 调用Dao层, 获取数据
- 数据访问层(Dao)
负责数据的访问操作，包含数据的增、删、改、查
  - 包名：```xxxx.dao```
  - 一个数据访问接口
  - 一个数据访问实现类

###### 三层架构的优点
- 复用性强
- 便于维护
- 利用扩展


##### 耦合问题
###### 内聚和耦合
- 内聚
软件中各个功能模块内部的功能联系
- 耦合
衡量软件中各个层/模块之间的依赖、关联的程度
###### 高内聚低耦合
软件设计原则：高内聚低耦合
- 高内聚
一个模块中各个元素之间的联系的紧密程度，如果各个元素(语句、程序段)之间的联系程度越高，则内聚性越高，即 "高内聚"
- 低耦合
软件中各个层、模块之间的依赖关联程序越低越好
- 高内聚、低耦合的目的
使程序模块的可重用性、移植性大大增强

###### 解耦思路
之前我们在编写代码时，需要什么对象，就直接new一个就可以了。 这种做法，层与层之间代码就耦合了，当service层的实现变了之后， 我们还需要修改controller层的代码
解决思路是：
- 提供一个容器，容器中存储一些对象(例：EmpService对象)
- Controller程序从容器中获取EmpService类型的对象

要实现上述解耦操作，就涉及到Spring中的两个核心概念：
###### 控制反转(Inversion Of Control)
简称IOC。对象的创建控制权由程序自身转移到外部（容器），这种思想称为控制反转
**对象的创建权由程序员主动创建转移到容器(由容器创建、管理对象)。这个容器称为：IOC容器或Spring容器**
###### 依赖注入(Dependency Injection)
简称DI。容器为应用程序提供运行时，所依赖的资源，称之为依赖注入

**程序运行时需要某个资源，此时容器就为其提供这个资源。例：EmpController程序运行时需要EmpService对象，Spring容器就为其提供并注入EmpService对象**

###### bean对象
IOC容器中创建、管理的对象，称之为：bean对象

##### IOC(控制反转/Inversion Of Control)
###### bean对象的声明
IOC控制反转，就是将对象的控制权交给Spring的IOC容器，由IOC容器创建及管理对象。IOC容器创建的对象称为bean对象
###### @Component注解及其衍生注解
Spring框架为了更好的标识web应用程序开发当中，bean对象到底归属于哪一层，提供了@Component的衍生注解
要把某个对象交给IOC管理器，需要在对应的类上加上@Component注解或其衍生注解
- ```@Component```
声明bean的基础注解，当不属于下面三类时，用此注解
- ```@Controller```
@Component的衍生注解，标注在控制器类上
※※※※※@RestController注解包含@Controller，不需要再额外标注
- ```@Service```
@Component的衍生注解，标注在业务类上
- ```@Repository```
@Component的衍生注解，标注在数据访问类上（由于与mybatis整合，使用较少）
###### bean对象的的名字
在IOC容器中，每一个Bean都有一个属于自己的名字，可以通过注解的value属性指定bean的名字。如果没有指定，默认为类名首字母小写

###### 注意事项
- 声明bean的时候，可以通过value属性指定bean的名字，如果没有指定，默认为类名首字母小写
- 使用以上四个注解都可以声明bean，但是在springboot集成web开发中，声明控制器bean只能用@Controller

###### 组件扫描
- 使用四大注解声明的bean，要想生效，还需要被组件扫描注解@ComponentScan扫描
- @ComponentScan注解虽然没有显式配置，但是实际上已经包含在了引导类声明注解@SpringBootApplication中，默认扫描的范围是SpringBoot启动类所在包及其子包
- 如果不在启动类所在包及其子包，可以手动添加@ComponentScan注解，指定要扫描的包（不推荐）
- 推荐做法：
将定义的controller，service，dao这些包，都放在引导类所在包的子包下，这样定义的bean就会被自动扫描到

##### DI(依赖注入/Dependency Injection)
依赖注入，是指IOC容器要为应用程序去提供运行时所依赖的资源，而资源指的就是对象
###### @Autowired注解
自动装配，默认是按照类型进行自动装配的（去IOC容器中找某个类型的对象，然后完成注入操作）
如果在IOC容器中，存在多个相同类型的bean对象，程序运行会报错
###### 多个相同类型的bean对象解决方案
- @Primary注解
当存在多个相同类型的Bean注入时，在类前加上@Primary注解，来确定默认的实现。给哪个类加上@Primary注解，就会运行相应的Bean对象
- @Qualifier注解
指定当前要注入的bean对象。在@Autowired注解后加上@Qualifier注解。@Qualifier的value属性中，指定注入的bean的名称（bean的名称是对应类名首字母小写）
- @Resource注解
是按照bean的名称进行注入。通过name属性指定要注入的bean的名称。用@Resource注解替换@Autowired注解后。@Resource的name属性中，指定注入的bean的名称（bean的名称是对应类名首字母小写）

**面试题 ：@Autowird 与 @Resource的区别**
- @Autowired 是spring框架提供的注解，而@Resource是JDK提供的注解
- @Autowired 默认是按照类型注入，而@Resource是按照名称注入

### 数据库开发
#### 概述
xml文件中可以存储数据，但是在企业项目开发中不会使用xml文件存储数据，因为不便管理维护，操作难度大。在真实的企业开发中，都会采用数据库来存储和管理数据
##### 数据库
英文为DataBase，简称DB，它是存储和管理数据的仓库
##### 数据库管理系统（DataBase Management System，简称DBMS）
DBMS是操作和管理数据库的大型软件。可以通过这个软件来操纵和管理数据库
##### SQL（Structured Query Language，简称SQL）
结构化查询语言，它是操作关系型数据库的编程语言，定义了一套操作关系型数据库的统一标准

程序员给数据库管理系统(DBMS)发送SQL语句，再由数据库管理系统操作数据库当中的数据
##### 主流的数据库
###### Oracle
大型的收费数据库，Oracle公司产品，价格昂贵
###### MySQL
开源免费的中小型数据库，后来Sun公司收购了MySQL，而Oracle又收购了Sun公司。目前Oracle推出两个版本的Mysql：社区版(开源免费)、商业版(收费)
###### SQL Server
Microsoft公司推出的收费的中型数据库，C#、.net等语言常用
###### PostgreSQL
开源免费的中小型数据库
###### DB2
IBM公司的大型收费数据库产品
###### SQLLite
嵌入式的微型数据库。Android内置的数据库采用的就是该数据库
###### MariaDB
开源免费的中小型数据库。是MySQL数据库的另外一个分支、另外一个衍生产品，与MySQL数据库有很好的兼容性

操作关系型数据库都是通过 SQL语句来实现的，而SQL语句又是操作关系型数据库的统一标准，可以通过SQL语句来操作Mysql，也可以通过SQL语句来操作Oracle或SQL Server

#### 安装
##### 版本
MySQL官方提供了两个版本：
###### 商业版本（MySQL Enterprise Edition）
该版本是收费的，我们可以使用30天。 官方会提供对应的技术支持
###### 社区版本（MySQL Community Server）
该版本是免费的，但是MySQL不会提供任何的技术支持
官网下载地址：https://downloads.mysql.com/archives/community/
##### 连接
MySQL服务器启动完毕后，使用如下指令，来连接MySQL服务器
```
mysql -u用户名 -p密码 [-h数据库服务器的IP地址 -P端口号]
```
- -h 参数不加，默认连接的是本地 127.0.0.1 的MySQL服务器
- -P 参数不加，默认连接的端口号是 3306

###### 上述指令，可以有两种形式：
- 密码直接在-p参数之后直接指定 （这种方式不安全，密码直接以明文形式出现在命令行）
- 密码在-p回车之后，在命令行中输入密码，然后回车

##### 企业使用方式
- 在真实的企业开发中，MySQL数据库服务器是在公司的服务器上安装的，而服务器还需要放置在专门的IDC机房中的，需要保证恒温、恒湿、恒压，而且还要保证网络、电源的可靠性(备用电源及网络)
- 要想使用服务器上的这台MySQL服务器，就需要在电脑上去远程连接这台MySQL。而服务器上安装的MySQL数据库，项目组的开发人员都需要访问这台MySQL的
- 体验企业中数据库的使用方式，可以借助于VMware虚拟机来实现。在Vmware虚拟机上在安装一个服务器操作系统Linux，再在Linux服务器上安装各种企业级软件

#### 数据模型
##### 关系型数据库（RDBMS）
建立在关系模型基础上，由多张相互连接的二维表组成的数据库
##### 二维表
二维表，指的是由行和列组成的表
###### 二维表的优点
- 使用表存储数据，格式统一，便于维护
- 使用SQL语言操作，标准统一，使用方便，可用于复杂查询

**MySQL、Oracle、DB2、SQLServer这些都是属于关系型数据库，里面都是基于二维表存储数据的**

**基于二维表存储数据的数据库就是关系型数据库，不是基于二维表存储数据的数据库，就是非关系型数据库（例如Redis，就属于非关系型数据库**

##### 数据模型
- 通过MySQL客户端连接数据库管理系统DBMS，然后通过DBMS操作数据库
- 使用MySQL客户端，向数据库管理系统发送一条SQL语句，由数据库管理系统根据SQL语句指令去操作数据库中的表结构及数据
- 一个数据库服务器中可以创建多个数据库，一个数据库中也可以包含多张表，而一张表中又可以包含多行记录

##### 在Mysql数据库服务器当中存储数据，需要：
- 第1步：创建数据库（可以创建多个数据库，之间是相互独立的）
- 第2步：在数据库下创建数据表（一个数据库下可以创建多张表）
- 第3步：将数据存放在数据表中（一张表可以存储多行数据）

#### SQL语言
SQL：结构化查询语言。一门操作关系型数据库的编程语言，定义操作所有关系型数据库的统一标准
##### SQL通用语法
- SQL语句可以单行或多行书写，以分号结尾
- SQL语句可以使用空格/缩进来增强语句的可读性
- MySQL数据库的SQL语句不区分大小写
###### 注释：
- 单行注释
```
-- 注释内容 或 # 注释内容(MySQL特有)
```
- 多行注释
```
 /* 注释内容 */
```
##### 分类
SQL语句根据其功能被分为四大类：DDL、DML、DQL、DCL
###### DDL
Data Definition Language，数据定义语言，用来定义数据库对象(数据库，表，字段)
###### DML
Data Manipulation Language，数据操作语言，用来对数据库表中的数据进行增删改
###### DQL
Data Query Language，数据查询语言，用来查询数据库中表的记录
###### DCL
Data Control Language，数据控制语言，用来创建数据库用户、控制数据库的访问权限

#### 数据库设计
##### 项目开发流程
###### 需求文档
在我们开发一个项目或者项目当中的某个模块之前，会先会拿到产品经理给我们提供的页面原型及需求文档
###### 设计
- 拿到产品原型和需求文档之后，要先进行项目的设计，其中就包括概要设计、详细设计、接口设计、数据库设计等等 
- 数据库设计根据产品原型以及需求文档，要分析各个模块涉及到的表结构以及表结构之间的关系，以及表结构的详细信息。最终需要将数据库以及数据库当中的表结构设计创建出来
###### 开发/测试
参照页面原型和需求进行编码，实现业务功能。在这个过程当中，我们就需要来操作设计出来的数据库表结构，来完成业务的增删改查操作等
###### 部署上线
在项目的功能开发测试完成之后，项目就可以上线运行了，后期如果项目遇到性能瓶颈，还需要对项目进行优化。优化很重要的一个部分就是数据库的优化，包括数据库当中索引的建立、SQL 的优化、分库分表等操作


##### 在上述的流程当中，针对于数据库来说，主要包括三个阶段：
###### 数据库设计阶段
参照页面原型以及需求文档设计数据库表结构
###### 数据库操作阶段
根据业务功能的实现，编写SQL语句对数据表中的数据进行增删改查操作
###### 数据库优化阶段
通过数据库的优化来提高数据库的访问性能。优化手段：索引、SQL优化、分库分表等

#### 数据库操作-数据定义语言-DDL
在进行数据库设计，需要使用到SQL分类中的DDL语句
DDL英文全称是Data Definition Language(数据定义语言)，用来定义数据库对象(数据库、表)
##### 数据库操作
DDL中数据库的常见操作：查询、创建、使用、删除
###### 查询数据库
- 查询所有数据库
```
show databases;
```
- 查询当前数据库：
```
select database();
```
**要操作某一个数据库，必须要切换到对应的数据库中。通过指令：```select database()``` ，就可以查询到当前所处的数据库**

###### 创建数据库
- 语法
```
create database [ if not exists ] 数据库名;
```
**注意：在同一个数据库服务器中，不能创建两个名称相同的数据库，否则将会报错**
- 可以使用if not exists来避免这个问题
- 数据库不存在,则创建该数据库；如果存在则不创建
```
create database if not extists itcast;
```

###### 使用数据库
- 语法
```
use 数据库名;
```
要操作某一个数据库下的表时，就需要通过该指令，切换到对应的数据库下，否则不能操作

###### 删除数据库
- 语法
```
drop database [ if exists ] 数据库名 ;
```
**如果删除一个不存在的数据库，将会报错。可以加上参数 if exists ，如果数据库存在，再执行删除，否则不执行删除**

*说明：上述语法中的database，也可以替换成 schema*
例如：```create schema db01;```
例如：```show schemas;```

##### 表操作
DDL语句当中关于表结构的操作包含四个部分：创建表、查询表、修改表、删除表
###### 创建表
- 语法
```
create table 表名(
 字段1 字段1类型 [约束] [comment 字段1注释 ],
 字段2 字段2类型 [约束] [comment 字段2注释 ],
 ......
 字段n 字段n类型 [约束] [comment 字段n注释 ]
) [ comment 表注释 ] ;
```

注意： [ ] 中的内容为可选参数； 最后一个字段后面没有逗号

- 主键自增
关键字为 ```auto_increment```
每次插入新的行记录时，数据库自动生成id字段(主键)下的值
具有 ```auto_increment``` 的数据列是一个正数序列开始增长(从1开始自增)


###### 查询表
- 查询当前数据库所有表
语法：
```
show tables;
```
- 查看指定表结构
语法：
```
desc 表名 ;
```
可以查看指定表的字段、字段的类型、是否可以为NULL、是否存在默认值等信息
- 查询指定表的建表语句
语法：
```
show create table 表名 ;
```

###### 修改表
- 添加字段
```
alter table 表名 add 字段名 类型(长度) [comment 注释] [约束];
```
- 修改数据类型
```
alter table 表名 modify 字段名 新数据类型(长度);
```
或
```
alter table 表名 change 旧字段名 新字段名 类型(长度) [comment 注释][约束];
```
- 删除字段
```
alter table 表名 drop 字段名;
```
- 修改表名
```
rename table 表名 to 新表名;
```

###### 删除表
- 删除表语法
```
drop table [ if exists ] 表名;
```
**if exists ：只有表名存在时才会删除该表，表名不存在，则不执行删除操作(如果不加该参数项，删除一张不存在的表，执行将会报错)**


##### 约束
###### 概念
约束就是作用在表中字段上的规则，用于限制存储在表中的数据
###### 作用
保证数据库当中数据的正确性、有效性和完整性
###### 约束类型
在MySQL数据库当中，提供了5种约束
- 非空约束
限制该字段值不能为null，关键字为not null
- 唯一约束
保证字段的所有数据都是唯一、不重复的，关键字为unique
- 主键约束
主键是一行数据的唯一标识，要求非空且唯一，关键字为primary key
- 默认约束
保存数据时，如果未指定该字段值，则采用默认值，关键字为default
- 外键约束
让两张表的数据建立连接，保证数据的一致性和完整性，关键字为```foreign key```

外键约束语法
- 创建表时指定
```
create table 表名(
     字段名 数据类型,
      ...
     [constraint] [外键名称] foreign key (外键字段名) references 主表 (主表列名) 
);
```
- 建完表后，添加外键
```
alter table 表名 add constraint 外键名称 foreign key(外键字段名) references 主表(主表列名);
```
**当我们添加外键约束时，我们得保证当前数据库表中的数据是完整的。 所以，我们需要将之前删除掉的数据再添加回来**


**注意：约束是作用于表中字段上的，可以在创建表/修改表的时候添加约束**

##### 数据类型
MySQL中的数据类型有很多，主要分为三类：数值类型、字符串类型、日期时间类型
###### 数值类型
| 类型       | 大小     | 有符号 (SIGNED) 范围                         | 无符号 (UNSIGNED) 范围                        | 说明                     |
|:------------|:----------|:-----------------------------------------------|:------------------------------------------------|:--------------------------|
| TINYINT      | 1 byte    | -128 到 127                                     | 0 到 255                                         | 小整数值                  |
| SMALLINT     | 2 bytes   | -32,768 到 32,767                               | 0 到 65,535                                      | 较大整数值                 |
| MEDIUMINT    | 3 bytes   | -8,388,608 到 8,388,607                         | 0 到 16,777,215                                  | 中等整数值                 |
| INT/INTEGER  | 4 bytes   | -2,147,483,648 到 2,147,483,647                 | 0 到 4,294,967,295                                | 大整数值                  |
| BIGINT       | 8 bytes   | -2^63 到 2^63-1                                 | 0 到 2^64-1                                       | 极大整数值                 |
| FLOAT        | 4 bytes   | -3.402823466E+38 到 3.402823466351E+38          | 0 和 1.175494351E-38 到 3.402823466E+38           | 单精度浮点数值             |
| DOUBLE       | 8 bytes   | -1.7976931348623157E+308 到 1.7976931348623157E+308 | 0 和 2.2250738585072014E-308 到 1.7976931348623157E+308 | 双精度浮点数值             |
| DECIMAL      | 自定义    | 取决于 M(精度) 和 D(标度)                      | 取决于 M(精度) 和 D(标度)                         | 精确定点小数，适合存储金额 |


**在SQL标准中，存在bool和boolean类型。在MySQL中也可以定义这两种类型，但是这两种类型最终转换成的是TINYINT（1）类型。所以在MySQL中，布尔类型等价于TINYINT(1)。因此创建表时定义的bool和Boolean类型，数据库中真实存储的是TINYINT(1)**

###### 字符串类型
| 类型         | 大小范围                   | 说明                               |
|:--------------|:----------------------------|:------------------------------------|
| CHAR           | 0 - 255 bytes                | 定长字符串，需要指定长度               |
| VARCHAR        | 0 - 65,535 bytes             | 变长字符串，需要指定长度               |
| TINYBLOB       | 0 - 255 bytes                | 不超过 255 个字符的二进制数据          |
| TINYTEXT       | 0 - 255 bytes                | 短文本字符串                         |
| BLOB           | 0 - 65,535 bytes             | 二进制形式的长文本数据                |
| TEXT           | 0 - 65,535 bytes             | 长文本数据                           |
| MEDIUMBLOB     | 0 - 16,777,215 bytes         | 二进制形式的中等长度文本数据          |
| MEDIUMTEXT     | 0 - 16,777,215 bytes         | 中等长度文本数据                     |
| LONGBLOB       | 0 - 4,294,967,295 bytes      | 二进制形式的极大文本数据              |
| LONGTEXT       | 0 - 4,294,967,295 bytes      | 极大文本数据                         |

char与varchar的区别：
- char 与 varchar 都可以描述字符串
- char是定长字符串，指定长度多长，就占用多少个字符，和字段值的长度无关
- 而varchar是变长字符串，指定的长度为最大占用长度
- 相对来说，char的性能会更高些
- char是以空间换时间，varchar是以时间换空间

###### 日期时间类型

| 类型       | 大小 (bytes) | 范围                                            | 格式                      | 说明                     |
|:------------|:---------------|:------------------------------------------------|:---------------------------|:--------------------------|
| DATE         | 3             | 1000-01-01 至 9999-12-31                       | YYYY-MM-DD                  | 日期值                     |
| TIME         | 3             | -838:59:59 至 838:59:59                        | HH:MM:SS                    | 时间值或持续时间             |
| YEAR         | 1             | 1901 至 2155                                   | YYYY                        | 年份值                     |
| DATETIME     | 8             | 1000-01-01 00:00:00 至 9999-12-31 23:59:59     | YYYY-MM-DD HH:MM:SS         | 混合日期和时间值             |
| TIMESTAMP    | 4             | 1970-01-01 00:00:01 至 2038-01-19 03:14:07     | YYYY-MM-DD HH:MM:SS         | 混合日期和时间值，时间戳     |


#### 数据库操作-数据操作语言-DML
DML英文全称是Data Manipulation Language(数据操作语言)，用来对数据库中表的数据记录进行增、删、改操作
##### 添加数据（INSERT）
###### insert语法
- 向指定字段添加数据
```
insert into 表名 (字段名1, 字段名2) values (值1, 值2);
```
- 全部字段添加数据
```
insert into 表名 values (值1, 值2, ...);
```
- 批量添加数据（指定字段）
```
insert into 表名 (字段名1, 字段名2) values (值1, 值2), (值1, 值2);
```
- 批量添加数据（全部字段）
```
insert into 表名 values (值1, 值2, ...), (值1, 值2, ...);
```

###### Insert操作的注意事项：
- 插入数据时，指定的字段顺序需要与值的顺序是一一对应的
- 字符串和日期型数据应该包含在引号中
- 插入的数据大小，应该在字段的规定范围内

##### 修改数据（UPDATE）
###### update语法
```
update 表名 set 字段名1 = 值1 , 字段名2 = 值2 , .... [where 条件] ;
```
###### update注意事项:
- 修改语句的条件可以有，也可以没有，如果没有条件，则会修改整张表的所有数据
- 在修改数据时，一般需要同时修改公共字段update_time，将其修改为当前操作时间

##### 删除数据（DELETE）
###### delete语法
```
delete from 表名 [where 条件] ;
```
###### delete注意事项
- DELETE 语句的条件可以有，也可以没有，如果没有条件，则会删除整张表的所有数据
- DELETE 语句不能删除某一个字段的值(可以使用UPDATE，将该字段值置为NULL即可)
- 当进行删除全部数据操作时，会提示询问是否确认删除所有数据，直接点击Execute即可


#### 数据库操作-数据查询语言-DQL
DQL英文全称是Data Query Language(数据查询语言)，用来查询数据库表中的记录

查询关键字：```SELECT```

查询操作是所有SQL语句当中最为常见，也是最为重要的操作。在一个正常的业务系统中，查询操作的使用频次是要远高于增删改操作的。当我们打开某个网站或APP所看到的展示信息，都是通过从数据库中查询得到的，而在这个查询过程中，还会涉及到条件、排序、分页等操作

##### 语法
DQL查询语句，语法结构如下
```
SELECT     字段列表
FROM       表名列表
WHERE      条件列表
GROUP BY   分组字段列表
HAVING     分组后条件列表
ORDER BY   排序字段列表
LIMIT      分页参数
```
##### 聚合函数
横向查询，就是根据条件一行一行的进行判断，而使用聚合函数查询就是纵向查询，它是对一列的值进行计算，然后返回一个结果值。（将一列数据作为一个整体，进行纵向计算）
###### 语法
```
select 聚合函数(字段列表) from 表名 ;
```
**注意 : 聚合函数会忽略空值，对NULL值不作为统计**

###### 常用聚合函数
- count 统计数量
按照列去统计有多少行数据。在根据指定的列统计的时候，如果这一列中有null的行，该行不会被统计在其中
count有三种用法：
  - ```count(字段)```，例如：```select count(id) from tb_emp;```
  - ```count(常量)```，例如：```select count('A') from tb_emp;```
  - ```count(*)```，例如：```select count(*) from tb_emp;```推荐此写法（MySQL底层进行了优化）

- max 最大值
计算指定列的最大值
- min 最小值
计算指定列的最小值
- avg 平均值
计算指定列的平均值
- sum 求和
计算指定列的数值和，如果不是数值类型，那么计算结果为0

##### 基本查询（不带任何条件）
在基本查询的DQL语句中，不带任何的查询条件
###### 查询多个字段
```
select 字段1, 字段2, 字段3 from 表名;
```
###### 查询所有字段（通配符）
```
select * from 表名;
```
* 号代表查询所有字段，在实际开发中尽量少用（不直观、影响效率）
###### 设置别名
```
select 字段1 [ as 别名1 ] , 字段2 [ as 别名2 ] from 表名;
```
设置别名时中括号不用写，AS可以省略，如果别名中有空格，别名需加引号
###### 去除重复记录
```
select distinct 字段列表 from 表名;
```
##### 条件查询（where）
###### 语法
```
select 字段列表 from 表名 where 条件列表 ;
```
条件列表：意味着可以有多个条件

学习条件查询就是学习条件的构建方式，而在SQL语句当中构造条件的运算符分为两类：比较运算符和逻辑运算符
###### 比较运算符
| 运算符                  | 说明                                              |
|:--------------------------|:-------------------------------------------------|
| `>`                        | 大于                                              |
| `>=`                       | 大于等于                                          |
| `<`                        | 小于                                              |
| `<=`                       | 小于等于                                          |
| `=`                        | 等于                                              |
| `<>` 或 `!=`                | 不等于                                            |
| `BETWEEN ... AND ...`       | 在某个范围之内（含最小、最大值）                       |
| `IN (...)`                  | 在 `IN` 后面的列表中的值，多选一                         |
| `LIKE`                      | 模糊匹配（`_` 匹配单个字符，`%` 匹配任意多个字符）        |
| `IS NULL`                   | 判断是否为 `NULL`                                   |

###### 逻辑运算符
| 运算符        | 说明                      |
|:---------------|:---------------------------|
| `AND` 或 `&&`   | 并且，多个条件同时成立        |
| `OR` 或 `||`    | 或者，多个条件任意一个成立    |
| `NOT` 或 `!`    | 非，取反，不是               |


##### 分组查询（group by）
分组： 按照某一列或者某几列，把相同的数据进行合并输出
分组其实就是按列进行分类(指定列下相同的数据归为一类)，然后可以对分类完的数据进行合并计算
分组查询通常会使用聚合函数进行计算
###### 语法
```
select 字段列表
from 表名
[where 条件]
group by 分组字段名
[having分组后过滤条件];
```
注意事项:
- 分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义
- 执行顺序：where > 聚合函数 > having

where与having区别（面试题）
- 执行时机不同：where是分组之前进行过滤，不满足where条件，不参与分组；而having是分组之后对结果进行过滤
- 判断条件不同：where不能对聚合函数进行判断，而having可以

##### 排序查询（order by）
排序在日常开发中是非常常见的一个操作，有升序排序，也有降序排序
###### 语法
```
select 字段列表
from 表名
[where 条件列表]
[group by 分组字段 ]
order by 字段1 排序方式1 , 字段2 排序方式2 … ;
```
###### 排序方式
- ASC
升序（默认值）
- DESC
降序

**注意事项：如果是升序, 可以不指定排序方式ASC**
**注意事项：如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序**

##### 分页查询（limit）
分页操作在业务系统开发时，也是非常常见的一个功能，日常我们在网站中看到的各种各样的分页条，后台也都需要借助于数据库的分页操作
###### 语法
```
select 字段列表
from 表名
limit 起始索引, 查询记录数 ;
```
注意事项:
- 起始索引从0开始。 计算公式 ： 起始索引 = （查询页码 - 1）* 每页显示记录数
- 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT
- 如果查询的是第一页数据，起始索引可以省略，直接简写为 limit 条数


##### 流程控制
###### IF语句
```
if(表达式, tvalue, fvalue) 
```
当表达式为true时，取值tvalue；当表达式为false时，取值fvalue

###### CASE语句
```
case 表达式 when 值1 then 结果1 [when 值2 then 结果2 ...] [else result] end
```
相当于java中的switch

#### 多表设计
项目开发中，在进行数据库表结构设计时，会根据业务需求及业务模块之间的关系，分析并设计表结构，由于业务之间相互关联，所以各个表结构之间也存在着各种联系，基本上分为三种：一对多、多对多、一对一
##### 一对多
###### 表设计
一对多关系实现：在数据库表中多的一方，添加字段，来关联属于一这方的主键，一的一方称为父表，多的一方称为子表

##### 外键约束
让两张表的数据建立连接，保证数据的一致性和完整性，关键字为```foreign key```
###### 外键约束语法
- 创建表时指定
```
create table 表名(
     字段名 数据类型,
      ...
     [constraint] [外键名称] foreign key (外键字段名) references 主表 (主表列名) 
);
```
- 建完表后，添加外键
```
alter table 表名 add constraint 外键名称 foreign key(外键字段名) references 主表(主表列名);
```
###### 物理外键和逻辑外键
- 物理外键
  - 概念
使用foreign key定义外键关联另外一张表
  - 缺点
    - 影响增、删、改的效率（需要检查外键关系）
    - 仅用于单节点数据库，不适用与分布式、集群场景
    - 容易引发数据库的死锁问题，消耗性能
- 逻辑外键
  - 概念
在业务层逻辑中，解决外键关联
  - 通过逻辑外键，就可以很方便的解决物理外键存在的问题

*在现在的企业开发中，很少会使用物理外键，都是使用逻辑外键。甚至在一些数据库开发规范中，会明确指出禁止使用物理外键 foreign key*

##### 一对一
一对一关系表在实际开发中应用起来比较简单，通常是用来做单表的拆分，也就是将一张大表拆分成两张小表，将大表中的一些基础字段放在一张表当中，将其他的字段放在另外一张表当中，以此来提高数据的操作效率

如果在业务系统当中，对用户的基本信息查询频率特别的高，但是对于用户的身份信息查询频率很低，此时出于提高查询效率的考虑，我就可以将这张大表拆分成两张小表，第一张表存放的是用户的基本信息，而第二张表存放的就是用户的身份信息。他们两者之间一对一的关系，一个用户只能对应一个身份证，而一个身份证也只能关联一个用户

一对一可以看成一种特殊的一对多。通过外键来体现一对一之间的关系，只需要在任意一方来添加一个外键就可以了

###### 表设计
在任意一方加入外键，关联另外一方的主键，并且设置外键为唯一的(UNIQUE)

##### 多对多
多对多的关系在开发中属于也比较常见的
###### 表设计
建立第三张中间表，中间表至少包含两个外键，分别关联两方主键

#### 多表查询
##### 概念
查询时从多张表中获取所需数据
单表查询的SQL语句：```select 字段列表 from 表名;```
多表查询，只需要使用逗号分隔多张表即可，如： ```select 字段列表 from 表1, 表2;```

*笛卡尔积：笛卡尔乘积是指在数学中，两个集合(A集合和B集合)的所有组合情况*

在多表查询时，需要消除无效的笛卡尔积，只保留表关联部分的数据
在SQL语句中，只需要给多表查询加上连接查询的条件即可去除无效的笛卡尔积

##### 分类
多表查询可以分为
###### 连接查询
- 内连接
相当于查询A、B交集部分数据
###### 外连接
- 左外连接
查询左表所有数据(包括两张表交集部分数据)
- 右外连接
查询右表所有数据(包括两张表交集部分数据)
###### 子查询

##### 内连接
###### 内连接查询
查询两表或多表中交集部分数据。
###### 内连接从语法上可以分为
- 隐式内连接
隐式内连接语法：
```
select 字段列表 from 表1 , 表2 where 条件 ... ;
```
例如：
```
select tb_emp.name , tb_dept.name -- 分别查询两张表中的数据
from tb_emp , tb_dept -- 关联两张表
where tb_emp.dept_id = tb_dept.id; -- 消除笛卡尔积
```
- 显式内连接
显式内连接语法：
```
select 字段列表 from 表1 [ inner ] join 表2 on 连接条件 ... ;
```
例如：
```
select tb_emp.name , tb_dept.name
from tb_emp inner join tb_dept
on tb_emp.dept_id = tb_dept.id;
```

##### 外连接
###### 左外连接
左外连接语法：
```
select 字段列表 from 表1 left [ outer ] join 表2 on 连接条件 ... ;
```
左外连接相当于查询表1(左表)的所有数据，当然也包含表1和表2交集部分的数据
###### 右外连接
右外连接语法：
```
select 字段列表 from 表1 right [ outer ] join 表2 on 连接条件 ... ;
```
右外连接相当于查询表2(右表)的所有数据，当然也包含表1和表2交集部分的数据

注意事项：
左外连接和右外连接是可以相互替换的，只需要调整连接查询时SQL语句中表的先后顺序。在日常开发使用时，更偏向于左外连接

##### 子查询
###### 定义
SQL语句中嵌套select语句，称为嵌套查询，又称子查询
```
SELECT * FROM t1 WHERE column1 = ( SELECT column1 FROM t2 ... );
```
子查询外部的语句可以是insert / update / delete / select 的任何一个，最常见的是select

###### 分类
根据子查询结果的不同分为：
- 标量子查询（子查询结果为单个值[一行一列]）
- 列子查询（子查询结果为一列，但可以是多行）
- 行子查询（子查询结果为一行，但可以是多列）
- 表子查询（子查询结果为多行多列[相当于子查询结果是一张表]）

###### 子查询可以书写的位置
- where之后
- from之后
- select之后

###### 标量子查询
子查询返回的结果是单个值(数字、字符串、日期等)，最简单的形式，这种子查询称为标量子查询
常用的操作符： = <> > >= < <=

###### 列子查询
子查询返回的结果是一列(可以是多行)，这种子查询称为列子查询
常用的操作符：
- IN
在指定的集合范围之内，多选一
- NOT IN
不在指定的集合范围之内

###### 行子查询
子查询返回的结果是一行(可以是多列)，这种子查询称为行子查询
常用的操作符：= 、<> 、IN 、NOT IN

###### 表子查询
子查询返回的结果是多行多列，常作为临时表，这种子查询称为表子查询

*由于子查询要多次查询表，效率不高，因此，尽量使用内连接和外连接*


#### 事务
##### 概念
在实际的业务开发中，有些业务操作要多次访问数据库。一个业务要发送多条SQL语句给数据库执行。需要将多次访问数据库的操作视为一个整体来执行，要么所有的SQL语句全部执行成功。如果其中有一条SQL语句失败，就进行事务的回滚，所有的SQL语句全部执行失败
###### 定义
事务是一组操作的集合，它是一个不可分割的工作单位。事务会把所有的操作作为一个整体
一起向系统提交或撤销操作请求，即这些操作要么同时成功，要么同时失败
###### 作用
保证在一个事务中多次操作数据库表中数据时，要么全都成功,要么全都失败

##### 操作
MYSQL中有两种方式进行事务的操作：
- 自动提交事务：即执行一条sql语句提交一次事务。（默认MySQL的事务是自动提交）
- 手动提交事务：先开启，再提交

##### 事务操作有关的SQL语句
```
start transaction; / begin;
```
开启手动控制事务
```
commit;
```
提交事务
```
rollback;
```
回滚事务

##### 手动提交事务步骤
- 第1种情况
开启事务 => 执行SQL语句 => 成功 => 提交事务
- 第2种情况
开启事务 => 执行SQL语句 => 失败 => 回滚事务

##### 四大特性（ACID）
###### 原子性（Atomicity）
- 原子性是指事务包装的一组SQL是一个不可分割的工作单元
- 事务中的操作要么全部成功，要么全部失败
###### 一致性（Consistency）
事务完成时，必须使所有的数据都保持一致状态
- 如果事务成功的完成，那么数据库的所有变化将生效
- 如果事务执行出现错误，那么数据库的所有变化将会被回滚(撤销)，返回到原始状态
###### 隔离性（Isolation）
- 数据库系统提供的隔离机制，保证事务在不受外部并发操作影响的独立环境下运行
- 多个用户并发的访问数据库时，一个用户的事务不能被其他用户的事务干扰，多个并发的事务之间要相互隔离
- 一个事务的成功或者失败对于其他的事务是没有影响
###### 持久性（Durability）
- 事务一旦提交或回滚，它对数据库中的数据的改变就是永久的
- 哪怕数据库发生异常，重启之后数据亦然存在


#### 索引(index)
##### 概念
索引(index)是帮助数据库高效获取数据的数据结构。使用索引可以提高查询的效率
##### 索引的优缺点
###### 优点
- 提高数据查询的效率，降低数据库的IO成本
- 通过索引列对数据进行排序，降低数据排序的成本，降低CPU消耗
###### 缺点
- 索引会占用存储空间
- 索引大大提高了查询效率，同时却也降低了insert、update、delete的效率

##### 索引的数据结构
MySQL数据库支持的索引结构有很多，如：Hash索引、B+Tree索引、Full-Text索引等

我们平常所说的索引，如果没有特别指明，都是指默认的 B+Tree 结构组织的索引

###### 二叉查找树
左边的子节点比父节点小，右边的子节点比父节点大

当我们向二叉查找树保存数据时，是按照从大到小(或从小到大)的顺序保存的，此时就会形成一个单向链表，搜索性能会打折扣

可以选择平衡二叉树或者是红黑树来解决上述问题。（红黑树也是一棵平衡的二叉树）

###### 红黑树
但是如果数据结构是红黑树，那么查询1000万条数据，根据计算树的高度大概是23左右，这样确实比之前的方式快了很多，但是如果高并发访问，那么一个用户有可能需要23次磁盘IO，那么100万用户，那么会造成效率极其低下。所以为了减少红黑树的高度，那么就得增加树的宽度，就是不再像红黑树一样每个节点只能保存一个数据，可以引入另外一种数据结构，一个节点可以保存

多个数据，这样宽度就会增加从而降低树的高度。这种数据结构例如BTree就满足

###### B+Tree(多路平衡搜索树)
- 每一个节点，可以存储多个key（有n个key，就有n个指针）
- 节点分为：叶子节点、非叶子节点
  - 叶子节点，就是最后一层子节点，所有的数据都存储在叶子节点上
  - 非叶子节点，不是树结构最下面的节点，用于索引数据，存储的的是：key+指针
- 为了提高范围查询效率，叶子节点形成了一个双向链表，便于数据的排序及区间范围查询

非叶子节点都是由key+指针域组成的，一个key占8字节，一个指针占6字节，而一个节点总共容量是16KB，那么可以计算出一个节点可以存储的元素个数：16*1024字节 / (8+6)=1170个元素
- 查看mysql索引节点大小：```show global status like 'innodb_page_size'; ```
  - 节点大小：16384

当根节点中可以存储1170个元素，那么根据每个元素的地址值又会找到下面的子节点，每个子节点也会存储1170个元素，那么第二层即第二次IO的时候就会找到数据大概是：1170*1170=135W。也就是说B+Tree数据结构中只需要经历两次磁盘IO就可以找到135W条数据

对于第二层每个元素有指针，那么会找到第三层，第三层由key+数据组成，假设key+数据总大小是1KB，而每个节点一共能存储16KB，所以一个第三层一个节点大概可以存储16个元素(即16条记录)。那么结合第二层每个元素通过指针域找到第三层的节点，第二层一共是135W个元素，那么第三层总元素大小就是：135W*16结果就是2000W+的元素个数

###### B+Tree的优点
- 千万条数据，B+Tree可以控制在小于等于3的高度
- 所有的数据都存储在叶子节点上，并且底层已经实现了按照索引进行排序，还可以支持范围查询，叶子节点是一个双向链表，支持从小到大或者从大到小查找

##### 索引的语法
###### 创建索引
```
create [ unique ] index 索引名 on 表名 (字段名,... ) ;
```
在创建表时，如果添加了主键和唯一约束，就会默认创建：主键索引、唯一约束。唯一约束本质上就是唯一索引

###### 查看索引
```
show index from 表名;
```
###### 删除索引
```
drop index 索引名 on 表名;
```
注意事项：
- 主键字段，在建表时，会自动创建主键索引
- 添加唯一约束时，数据库实际上会添加唯一索引


## Mybatis
在客户端工具中，编写增删改查的SQL语句，发给MySQL数据库管理系统，由数据库管理系统执行SQL语句并返回执行结果
增删改操作：返回受影响行数
查询操作：返回结果集(查询的结果)

后端程序开发人员，通常会使用Java程序来完成对数据库的操作。Java程序操作数据库，现在主流的方式是：Mybatis
### Mybatis概念
MyBatis是一款优秀的 持久层 框架，用于简化JDBC的开发

MyBatis本是 Apache的一个开源项目iBatis，2010年这个项目由apache迁移到了google code，并且改名为MyBatis2013年11月迁移到Github

官网：https://mybatis.org/mybatis-3/zh/index.html

**持久层：指的是就是数据访问层(dao)，是用来操作数据库的**
**框架：是一个半成品软件，是一套可重用的、通用的、软件基础代码模型。在框架的基础上进行软件开发更加高效、规范、通用、可拓展**

Mybatis操作数据库，就是在Mybatis中编写SQL查询代码，发送给数据库执行，数据库执行后返回结果。Mybatis会把数据库执行的查询结果，使用实体类封装起来（一行记录对应一个实体类对象）

### Mybatis操作数据库的步骤：
#### 第1步：准备工作(创建springboot工程、数据库表user、实体类User)
创建springboot工程，并导入 mybatis的起步依赖、mysql的驱动包。（Mybatis依赖是MyBatis Framework,MySQL依赖是MySQL Driver）
#### 第2步：引入Mybatis的相关依赖，配置Mybatis(数据库连接信息)
在Mybatis中要连接数据库，需要4个参数配置:MySQL驱动类、登录名、密码、数据库连接字符串

在springboot项目中，可以编写application.properties文件，配置数据库连接信息，包括：driver-class-name、url 、username，password

##### 在application.properties文件中
```
#驱动类名称
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
#数据库连接的url
spring.datasource.url=jdbc:mysql://localhost:3306/数据库名
#连接数据库的用户名
spring.datasource.username=root
#连接数据库的密码
spring.datasource.password=123456
```
#### 第3步：编写SQL语句(注解/XML)
在创建出来的springboot工程中，在引导类所在包下，在创建一个包 mapper。在mapper包下创建一个接口 UserMapper ，这是一个持久层接口（Mybatis的持久层接口规范一般都叫XxxMapper）
##### @Mapper注解
表示是mybatis中的Mapper接口
程序运行时：框架会自动生成接口的实现类对象(代理对象)，并给交Spring的IOC容器管理
##### @Select注解
代表的就是select查询，用于书写select查询语句
#### 第4步：单元测试
在创建出来的SpringBoot工程中，在src下的test目录下，已经自动帮我们创建好了测试类 ，并且在测试类上已经添加了注解 @SpringBootTest，代表该测试类已经与SpringBoot整合。该测试类在运行时，会自动通过引导类加载Spring的环境（IOC容器）。我们要测试那个bean对象，就可以直接通过@Autowired注解直接将其注入进行，然后就可以测试了

### 解决SQL警告与提示
默认我们在UserMapper接口上的@Select注解中编写SQL语句是没有提示的。如果想让idea给出提示，可以做如下配置：
```
Show Context Actions --> inject language or reference --> MySQL(SQL)
```

配置完成之后，发现SQL语句中的关键字有提示了，但还存在不识别表名(列名)的情况：
- 产生原因：Idea和数据库没有建立连接，不识别表信息
- 解决方案：在Idea中配置MySQL数据库连接

### JDBC
#### 概念
java语言操作数据库，只能通过一种方式：使用sun公司提供的 JDBC 规范

*Mybatis框架，就是对原始的JDBC程序的封装*

#### 定义
JDBC( Java DataBase Connectivity )，就是使用Java语言操作关系型数据库的一套API

#### 本质
- sun公司官方定义的一套操作所有关系型数据库的规范，即接口
- 各个数据库厂商去实现这套接口，提供数据库驱动jar包
- 可以使用这套接口(JDBC)编程，真正执行的代码是驱动jar包中的实现类

#### JDBC程序操作数据库的步骤
- 第1步：注册驱动
- 第2步：获取连接对象
- 第3步：执行SQL语句，返回执行结果
- 第4步：处理执行结果
- 第5步：释放资源

在pom.xml文件中已引入MySQL驱动依赖，我们直接编写JDBC代码即可

#### JDBC具体代码实现
```
import com.itheima.pojo.User;
import org.junit.jupiter.api.Test;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;
import java.util.ArrayList;
import java.util.List;
public class JdbcTest {
@Test
public void testJdbc() throws Exception {
      //1. 注册驱动
      Class.forName("com.mysql.cj.jdbc.Driver");
      //2. 获取数据库连接
      String url="jdbc:mysql://127.0.0.1:3306/mybatis";
      String username = "root";
      String password = "1234";
      Connection connection = DriverManager.getConnection(url,username, password);
      //3. 执行SQL
      Statement statement = connection.createStatement(); //操作SQL的对象
      String sql="select id,name,age,gender,phone from user";
      ResultSet rs = statement.executeQuery(sql);//SQL查询结果会封装在ResultSet对象中
      List<User> userList = new ArrayList<>();//集合对象（用于存储User对象）
      //4. 处理SQL执行结果
      while (rs.next()){
      //取出一行记录中id、name、age、gender、phone下的数据
            int id = rs.getInt("id");
            String name = rs.getString("name");
            short age = rs.getShort("age");
            short gender = rs.getShort("gender");
            String phone = rs.getString("phone");
            //把一行记录中的数据，封装到User对象中
            User user = new User(id,name,age,gender,phone);
            userList.add(user);//User对象添加到集合
      }
      //5. 释放资源
      statement.close();
      connection.close();
      rs.close();
      //遍历集合
      for (User user : userList) {
            System.out.println(user);
      }
   }
}
```

#### DriverManager(类)
数据库驱动管理类。
- 作用
  - 注册驱动
  - 创建java代码和数据库之间的连接，即获取Connection对象
#### Connection(接口)
建立数据库连接的对象
- 作用
用于建立java程序和数据库之间的连接
#### Statement(接口)
数据库操作对象(执行SQL语句的对象)。
- 作用
用于向数据库发送sql语句
#### ResultSet(接口)
结果集对象（一张虚拟表）
- 作用
sql查询语句的执行结果会封装在ResultSet中

直接基于JDBC程序来操作数据库，代码实现非常繁琐，所以在项目开发中，我们很少使用。 在项目开发中，通常会使用Mybatis这类的高级技术来操作数据库，从而简化数据库操作、提高开发效率

#### 问题分析
原始的JDBC程序，存在以下几点问题：
- 数据库链接的四要素(驱动、链接、用户名、密码)全部硬编码在java代码中
- 查询结果的解析及封装非常繁琐
- 每一次查询数据库都需要获取连接,操作完毕后释放连接, 资源浪费, 性能降低

#### 技术对比
mybatis中，是如何解决这些问题的：
- 数据库连接四要素(驱动、链接、用户名、密码)，都配置在springboot默认的配置文件 ```application.properties``` 中
- 查询结果的解析及封装，由mybatis自动完成映射封装，我们无需关注
- 在mybatis中使用了数据库连接池技术，从而避免了频繁的创建连接、销毁连接而带来的资源浪费

使用SpringBoot+Mybatis的方式操作数据库，能够提升开发效率、降低资源浪费

对于Mybatis来说，我们在开发持久层程序操作数据库时，需要重点关注以下两个方面：
##### application.properties
```
#驱动类名称
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
#数据库连接的url
spring.datasource.url=jdbc:mysql://localhost:3306/数据库名
#连接数据库的用户名
spring.datasource.username=root
#连接数据库的密码
spring.datasource.password=123456
```
##### Mapper接口（编写SQL语句）
```
@Mapper
public interface UserMapper {
    @Select("select id, name, age, gender, phone from user")
    public List<User> list();
}
```

### 数据库连接池
数据库连接池技术，可以避免频繁的创建连接、销毁连接而带来的资源浪费

没有使用数据库连接池时，客户端执行SQL语句：要先创建一个新的连接对象，然后执行SQL语句，SQL语句执行后又需要关闭连接对象从而释放资源，每次执行SQL时都需要创建连接、销毁链接，这种频繁的重复创建销毁的过程是比较耗费计算机的性能
#### 概念
##### 数据库连接池是个容器，负责分配、管理数据库连接(Connection)
程序在启动时，会在数据库连接池(容器)中，创建一定数量的Connection对象
##### 允许应用程序重复使用一个现有的数据库连接，而不是再重新建立一个
客户端在执行SQL时，先从连接池中获取一个Connection对象，然后在执行SQL语句，SQL语句执行完之后，释放Connection时就会把Connection对象归还给连接池（Connection对象可以复用）
##### 释放空闲时间超过最大空闲时间的连接，来避免因为没有释放连接而引起的数据库连接遗漏
客户端获取到Connection对象了，但是Connection对象并没有去访问数据库(处于空闲)，数据库连接池发现Connection对象的空闲时间 > 连接池中预设的最大空闲时间，此时数据库连接池就会自动释放掉这个连接对象
##### 数据库连接池的好处
- 资源重用
- 提升系统响应速度
- 避免数据库连接遗漏

#### 常见的数据库连接池
##### 连接池接口
官方(sun)提供了数据库连接池标准（javax.sql.DataSource接口）
- 功能：获取连接
```
public Connection getConnection() throws SQLException;
```
- 第三方组织必须按照DataSource接口实现

##### 常见的数据库连接池
- C3P0
- DBCP
- Druid（德鲁伊）
Druid连接池是阿里巴巴开源的数据库连接池项目
功能强大，性能优秀，是Java语言最好的数据库连接池之一
- Hikari（追光者） (springboot默认) [默认的连接池]

现在使用更多的是：Hikari、Druid （性能更优越）

#### 切换Druid数据库连接池
如果我们想把默认的数据库连接池切换为Druid数据库连接池，只需要完成以下两步操作：
##### 在pom.xml文件中引入依赖
```
<dependency>
    <!-- Druid连接池依赖 -->
    <groupId>com.alibaba</groupId>
    <artifactId>druid-spring-boot-starter</artifactId>
    <version>1.2.8</version>
</dependency>
```
##### 在application.properties中引入数据库连接配置
###### 方式1
```
spring.datasource.druid.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.druid.url=jdbc:mysql://localhost:3306/mybatis
spring.datasource.druid.username=root
spring.datasource.druid.password=123456
```
###### 方式2
```
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/mybatis
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.type = com.alibaba.druid.pool.DruidDataSource
```

### lombok
#### 概念
Lombok是一个实用的Java类库，可以通过简单的注解来简化和消除一些必须有但显得很臃肿的Java代码

通过注解的形式自动生成构造器、getter/setter、equals、hashcode、toString等方法，并可以自动化生成日志变量，简化java开发、提高效率

#### 注解
##### @Getter/@Setter
为所有的属性提供get/set方法
##### @ToString
会给类自动生成易阅读的 toString 方法
##### @EqualsAndHashCode
根据类所拥有的非静态字段自动重写 equals 方法和 hashCode方法
##### @Data
提供了更综合的生成代码功能（@Getter + @Setter + @ToString + @EqualsAndHashCode）
##### @NoArgsConstructor
为实体类生成无参的构造器方法
##### @AllArgsConstructor
为实体类生成除了static修饰的字段之外带有各参数的构造器方法

#### 使用方法
##### 第1步：在pom.xml文件中引入依赖
```
<!-- 在springboot的父工程中，已经集成了lombok并指定了版本号，故当前引入依赖时不需要指定version -->
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
</dependency>
```
##### 第2步：在实体类上添加注解
在实体类上添加了@Data注解，那么这个类在编译时期，就会生成getter/setter、equals、hashcode、toString等方法

*注意：@Data注解中不包含全参构造方法，通常在实体类上，还需要添加全参构造和无参构造*


#### Lombok的注意事项
- Lombok会在编译时，会自动生成对应的java代码
- 在使用lombok时，还需要安装一个lombok的插件（新版本的IDEA中自带）



### Mybatis基础操作
#### 准备工作
- 准备数据库表
- 创建一个新的springboot工程，选择引入对应的起步依赖（springbootWeb、mybatis、mysql驱动、lombok）
- application.properties中引入数据库连接信息
- 创建对应的实体类 Emp（实体类属性采用驼峰命名）
- 准备Mapper接口 EmpMapper

#### 删除数据
##### 功能实现
当点击后面的"删除"按钮时，前端页面会给服务端传递一个参数，也就是该行数据的ID。接收到ID后，根据ID删除数据即可
###### @Delete注解
用于编写delete操作的SQL语句
###### SQL语句
```
delete from emp where id = 17;
```
###### 接口方法
```
@Mapper
public interface EmpMapper {
    @Delete("delete from emp where id = #{id}")//使用#{key}方式获取方法中的参数值
    public void delete(Integer id);
}
```
SQL语句中的id值不能写成固定数值，需要变为动态的数值
解决方案：在delete方法中添加一个参数(用户id)，将方法中的参数，传给SQL语句

**如果mapper接口方法形参只有一个普通类型的参数，#{…} 里面的属性名可以随便写，如：#{id}、#{value}。但是建议保持名字一致**

###### 测试
在单元测试类中通过@Autowired注解注入EmpMapper类型对象
```
@SpringBootTest
class SpringbootMybatisCrudApplicationTests {
    @Autowired //从Spring的IOC容器中，获取类型是EmpMapper的对象并注入
    private EmpMapper empMapper;
    @Test
    public void testDel(){
    //调用删除方法
    empMapper.delete(16);
    }
}
```
##### 日志输入
在Mybatis当中我们可以借助日志，查看到sql语句的执行、执行传递的参数以及执行结果。具体操作如下：
###### 第1步：打开application.properties文件
###### 第2步：开启mybatis的日志，并指定输出到控制台
```
#指定mybatis输出日志的位置, 输出控制台
mybatis.configuration.log impl=org.apache.ibatis.logging.stdout.StdOutImpl
```
开启日志之后，再次运行单元测试，可以看到在控制台中，输出了SQL语句信息
但是输出的SQL语句：```delete from emp where id = ?``` ，输入的参数并没有在后面拼接，id的值是使用?进行占位。那这种SQL语句称为预编译SQL

##### 预编译SQL
预编译SQL有两个优势：
- 性能更高
预编译SQL，编译一次之后会将编译后的SQL语句缓存起来，后面再次执行这条语句时，不会再次编译。（只是输入的参数不同）
- 更安全(防止SQL注入)
将敏感字进行转义，保障SQL的安全性

##### SQL注入
是通过操作输入的数据来修改事先定义好的SQL语句，以达到执行代码对服务器进行攻击的方法

由于没有对用户输入进行充分检查，而SQL又是拼接而成，在用户输入参数时，在参数中添加一些SQL关键字，达到改变SQL运行结果的目的，也可以完成恶意攻击

用户在页面提交数据的时候人为的添加一些特殊字符，使得sql语句的结构发生了变化，最终可以在没有用户名或者密码的情况下进行登录

预编译SQL把整个 ```'or' 1 '=' 1``` 作为一个完整的参数，赋值给第2个问号```'or' 1 '=' 1``` 进行了转义，只当做字符串使用

##### 参数占位符
在Mybatis中提供的参数占位符有两种：```${...}``` 、```#{...}```
- ```#{...}```
  - 执行SQL时，会将#{…}替换为?，生成预编译SQL，会自动设置参数值
  - 使用时机：参数传递，都使用#{…}
- ```${...}```
  - 拼接SQL:直接将参数拼接在SQL语句中，存在SQL注入问题
  - 使用时机:如果对表名、列表进行动态设置时使用

*注意事项：在项目开发中，建议使用#{...}，生成预编译SQL，防止SQL注入安全*


#### 新增数据
##### 基本新增
###### SQL语句
```
insert into emp(username, name, gender, image, job, entrydate,dept_id, create_time, update_time) values ('songyuanqiao','宋远桥',1,'1.jpg',2,'2012-10-09',2,'2022-10-01 10:00:00','2022-10-01 10:00:00');
```
###### 接口方法
```
@Mapper
public interface EmpMapper {
     @Insert("insert into emp(username, name, gender, image, job, entrydate, dept_id, create_time, update_time)values (#{username}, #{name}, #{gender}, #{image}, #{job}, #{entrydate}, #{deptId}, #{createTime}, #{updateTime})")
     public void insert(Emp emp);
}
```
**#{...} 里面写的名称是对象的属性名**

###### 测试类
```
@SpringBootTest
class SpringbootMybatisCrudApplicationTests {
    @Autowired
    private EmpMapper empMapper;
    @Test
    public void testInsert(){
        //创建员工对象
        Emp emp = new Emp();
        emp.setUsername("tom");
        emp.setName("汤姆");
        emp.setImage("1.jpg");
        emp.setGender((short)1);
        emp.setJob((short)1);
        emp.setEntrydate(LocalDate.of(2000,1,1));
        emp.setCreateTime(LocalDateTime.now());
        emp.setUpdateTime(LocalDateTime.now());
        emp.setDeptId(1);
        //调用添加方法
        empMapper.insert(emp);
    }
}
```
##### 主键返回
在数据添加成功后，需要获取插入数据库数据的主键
- 默认情况下，执行插入操作时，是不会主键值返回的
- 如果想要拿到主键值，需要在Mapper接口中的方法上添加一个Options注解，并在注解中指定属性 ```useGeneratedKeys=true``` 和 ```keyProperty="实体类属性名"```
- 主键返回代码实现
```
@Mapper
public interface EmpMapper {
    //会自动将生成的主键值，赋值给emp对象的id属性
    @Options(useGeneratedKeys = true,keyProperty = "id")
    @Insert("insert into emp(username, name, gender, image, job, entrydate, dept_id, create_time, update_time) values (#{username}, #{name}, #{gender}, #{image}, #{job}, #{entrydate}, #{deptId}, #
{createTime}, #{updateTime})")
    public void insert(Emp emp);
}
```
#### 修改数据
##### SQL语句
```
update emp set username = 'linghushaoxia', name = '令狐少侠', gender =1 , image = '1.jpg' , job = 2, entrydate = '2012-01-01', dept_id = 2,update_time = '2022-10-01 12:12:12' where id = 18;
```
##### 接口方法
```
@Mapper
public interface EmpMapper {
    /**
    * 根据id修改员工信息
    * @param emp
    */
    @Update("update emp set username=#{username}, name=#{name}, gender=#{gender}, image=#{image}, job=#{job}, entrydate=#{entrydate}, dept_id=#{deptId}, update_time=#{updateTime} where id=#
{id}")
    public void update(Emp emp);
}
```
##### 测试类
```
@SpringBootTest
class SpringbootMybatisCrudApplicationTests {
    @Autowired
    private EmpMapper empMapper;
    @Test
    public void testUpdate(){
        //要修改的员工信息
        Emp emp = new Emp();
        emp.setId(23);
        emp.setUsername("songdaxia");
        emp.setPassword(null);
        emp.setName("令狐少侠");
        emp.setImage("2.jpg");
        emp.setGender((short)1);
        emp.setJob((short)2);
        emp.setEntrydate(LocalDate.of(2012,1,1));
        emp.setCreateTime(null);
        emp.setUpdateTime(LocalDateTime.now());
        emp.setDeptId(2);
        //调用方法，修改员工数据
        empMapper.update(emp);
    }
}
```
**实例化的Emp仅设置需要修改的数据即可**

#### 查询数据
##### 根据ID查询
###### SQL语句
```
select id, username, password, name, gender, image, job, entrydate, dept_id, create_time, update_time from emp;
```
###### 接口方法
```
@Mapper
public interface EmpMapper {
    @Select("select id, username, password, name, gender, image, job, entrydate, dept_id, create_time, update_time from emp where id=#{id}")
    public Emp getById(Integer id);
}
```
###### 测试类
```
@SpringBootTest
class SpringbootMybatisCrudApplicationTests {
    @Autowired
    private EmpMapper empMapper;
    @Test
    public void testGetById(){
        Emp emp = empMapper.getById(1);
        System.out.println(emp);
    }
}
```
##### 数据封装
直接进行查询，查询返回的结果中可能会出现字段是没有值的，而数据库中是有对应的字段值的

原因是
- 实体类属性名和数据库表查询返回的字段名一致，mybatis会自动封装
- 如果实体类属性名和数据库表查询返回的字段名不一致，不能自动封装


解决方案
###### 起别名
在SQL语句中，对不一样的列名起别名，别名和实体类属性名一样
```
@Select("select id, username, password, name, gender, image, job, entrydate, dept_id AS deptId, create_time AS createTime, update_time AS updateTime from emp where id=#{id}")
public Emp getById(Integer id);
```
###### 结果映射
通过 @Results及@Result 进行手动结果映射
```
@Results({@Result(column = "dept_id", property = "deptId"),
          @Result(column = "create_time", property = "createTime"),
          @Result(column = "update_time", property = "updateTime")})
@Select("select id, username, password, name, gender, image, job, entrydate, dept_id, create_time, update_time from emp where id=#{id}")
public Emp getById(Integer id);
```
###### 开启驼峰命名（首选方案）
如果字段名与属性名符合驼峰命名规则，mybatis会自动通过驼峰命名规则映射
- 驼峰命名规则： abc_xyz => abcXyz
  - 表中字段名：abc_xyz
  - 类中属性名：abcXyz
```
# 在application.properties中添加：
mybatis.configuration.map-underscore-to-camel-case=true
```
**要使用驼峰命名前提是 实体类的属性 与 数据库表中的字段名严格遵守驼峰命名**


##### 条件查询
根据条件查询员工信息，查询条件包括：姓名、性别、入职时间
###### 需求
要实现的查询：
- 姓名：要求支持模糊匹配
- 性别：要求精确匹配
- 入职时间：要求进行范围查询
- 根据最后修改时间进行降序排序

###### SQL语句
```
select id, username, password, name, gender, image, job, entrydate,
dept_id, create_time, update_time
from emp
where name like '%张%'
     and gender = 1
     and entrydate between '2010-01-01' and '2020-01-01 '
order by update_time desc;
```
###### 接口方法
- 方式1
```
@Mapper
public interface EmpMapper {
    @Select("select * from emp where name like '%${name}%' and gender = #{gender} and entrydate between #{begin} and #{end} order by update_time desc")
    public List<Emp> list(String name, Short gender, LocalDate begin,LocalDate end);
}
```
以上方式注意事项：
方法中的形参名和SQL语句中的参数占位符名保持一致
模糊查询使用${...}进行字符串拼接，这种方式由于是字符串拼接，并不是预编译的形式，所以效率不高，且存在sql注入风险



- 方式二（解决SQL注入风险）
使用MySQL提供的字符串拼接函数：concat('%' , '关键字' , '%')
```
@Mapper
public interface EmpMapper {
   @Select("select * from emp where name like concat('%',#{name},'%') and gender = #{gender} and entrydate between #{begin} and #{end} order by update_time desc")
   public List<Emp> list(String name, Short gender, LocalDate begin, LocalDate end);
}
```
执行结果：生成的SQL都是预编译的SQL语句（性能高、安全）

##### 参数名说明
在编写的条件查询功能中，需要保证接口中方法的形参名和SQL语句中的参数占位符名相同

- 当方法中的形参名和SQL语句中的占位符参数名不相同时，就会引发异常

参数名在不同的SpringBoot版本中，处理方案不同
- 在springBoot的2.x版本
  - 保证参数名一致
  - springBoot的父工程对compiler编译插件进行了默认的参数parameters配置，使得在编译时，会在生成的字节码文件中保留原方法形参的名称，所以#{…}里面可以直接通过形参名获取对应的值

- 在springBoot的1.x版本/单独使用mybatis
  - 使用@Param注解来指定SQL语句中的参数名
  - 在编译时，生成的字节码文件当中，不会保留Mapper接口中方法的形参名称，而是使用var1、var2、...这样的形参名字，此时要获取参数值时，就要通过@Param注解来指定SQL语句中的参数名


### Mybatis的XML配置文件
Mybatis的开发有两种方式：注解和XML
#### XML配置文件规范
使用Mybatis的注解方式，主要是来完成一些简单的增删改查功能。如果需要实现复杂的SQL功能，需要使用XML来配置映射语句，也就是将SQL语句写在XML配置文件中

##### 在Mybatis中使用XML映射文件方式开发，需要符合一定的规范
- XML映射文件的名称与Mapper接口名称一致，并且将XML映射文件和Mapper接口放置在相同包下（同包同名）
- XML映射文件的namespace属性为Mapper接口全限定名一致
- XML映射文件中sql语句的id与Mapper接口中的方法名一致，并保持返回类型一致


```<select>``` 标签：就是用于编写select查询语句的

resultType属性，指的是查询返回的单条记录所封装的类型

#### XML配置文件实现
##### 第1步
创建XML映射文件
- 第1-1步
在resources目录下，创建和接口一样的包名
*特别注意：包名之间用/分隔，否则多层包会合成一个包，例如:com/smiler/mapper*
- 第1-2步
新建文件Mapper.xml，注意文件名与Mapper接口名一致
##### 第2步
编写XML映射文件
xml映射文件中的dtd约束，直接从mybatis官网复制即可
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="">
</mapper>
```
- 配置：XML映射文件的namespace属性为Mapper接口全限定名
将Mapper接口右键Copy Path-->Copy Reference复制Mapper接口的全限定名

- 配置：XML映射文件中sql语句的id与Mapper接口中的方法名一致，并保持返回类型一致
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.smiler.mapper.EmpMapper">
    <!--查询操作-->
    <select id="select03" resultType="com.smiler.pojo.Employee">
        SELECT *
        FROM tb_emp
        WHERE name LIKE CONCAT('%',#{name},'%')
        AND gender = #{gender}
        AND entrydate BETWEEN #{begin} AND #{end}
    </select>
</mapper>
```
在项目中到底是使用注解方式开发还是使用XML方式开发？
- 使用注解来映射简单语句会使代码显得更加简洁，但对于稍微复杂一点的语句，Java 注解不仅力不从心，还会让本就复杂的 SQL 语句更加混乱不堪。因此，如果需要做一些很复杂的操作，最好用 XML 来映射语句
- 选择何种方式来配置映射，以及认为是否应该要统一映射语句定义的形式，完全取决于你和你的团队。换句话说，永远不要拘泥于一种方式，你可以很轻松的在基于注解和 XML 的语句映射方式间自由移植和切换

#### MybatisX
MybatisX是一款基于IDEA的快速开发Mybatis的插件，为效率而生
##### 安装
在IDEA的Settings-->Plugins中搜索安装


### Mybatis动态SQL
#### 动态SQL
- 在页面原型中，查询的条件是动态的，是可以不传递的，也可以只传递其中的1个或者2个或者全部
- 在非动态的SQL语句中，条件直接写死了。 如果页面只传递了参数姓名name 字段，其他两个字段 性别 和 入职时间没有传递，那么这两个参数的值就是null
- 此时查询结果是不正确的。正确的做法应该是：传递了参数，再组装这个查询条件；如果没有传递参数，就不应该组装这个查询条件

SQL语句会随着用户的输入或外部条件的变化而变化，我们称为：动态SQL
Mybatis中提供了很多实现动态SQL的标签

#### 动态SQL标签
##### ```<if>```
用于判断条件是否成立。使用test属性进行条件判断，如果条件为true，则拼接SQL
###### 语法
在XML文件中
```
<if test="条件表达式">
   要拼接的sql语句
</if>
```

##### ```<where>```
只会在子元素有内容的情况下才插入where子句，而且会自动去除子句的开头的AND或OR

如果有的属性为NULL或所有属性为NULL，拼接的SQL语句会多余WHERE或AND，此时需要使用 ```<where></where>``` 来包裹查询条件

###### 语法
在XML文件中
<where>
    <if test="条件表达式">
       要拼接的sql语句
    </if>
    <if test="条件表达式">
       要拼接的sql语句
    </if>
    <if test="条件表达式">
       要拼接的sql语句
    </if>
</where>

##### ```<set>```
动态的在SQL语句中插入set关键字，并会删掉额外的逗号（用于update语句中）
###### 语法
在XML文件中
```
<!--更新操作-->
<update id="update">
    update 表名
    <!-- 使用set标签，代替update语句中的set关键字 -->
    <set>
        <if test="条件表达式">
           要拼接的sql语句
        </if>
        <if test="条件表达式">
           要拼接的sql语句
        </if>
        <if test="条件表达式">
           要拼接的sql语句
        </if>
    </set>
```

##### ```<foreach>```
使用 ```<foreach>``` 遍历方法中传递的参数集合,主要用在批量操作中
###### 语法
```
<foreach collection="集合名称" item="集合遍历出来的元素/项" separator="每一次遍历使用的分隔符" open="遍历开始前拼接的片段" close="遍历结束后拼接的片段">
</foreach>
```

例如：
- SQL语句
```
DELETE FROM emp WHERE id IN (1,2,3);
```
- 接口方法
```
//批量删除
public void deleteByIds(List<Integer> ids);
```
- XML映射文件
```
<delete id="deleteByIds">
   delete from emp where id in
   <foreach collection="ids" item="id" separator="," open="(" close=")">
     #{id}
   </foreach>
</delete>
```
- 属性

| 名称         | 说明                          |
|:--------------|:-------------------------------|
| `collection`   | 集合名称                        |
| `item`         | 集合遍历出来的元素/项             |
| `separator`    | 每一次遍历时使用的分隔符           |
| `open`         | 遍历开始前拼接的片段               |
| `close`        | 遍历结束后拼接的片段               |


##### ```<sql>``` 和 ```<include>```
相当于函数和函数调用
在xml映射文件中配置的SQL，有时可能会存在很多重复的片段，此时就会存在很多冗余的代码

对重复的代码片段进行抽取，将其通过 ```<sql>``` 标签封装到一个SQL片段，然后再通过 ```<include>``` 标签进行引用
###### ```<sql>```
定义可重用的SQL片段
```
<sql id="commonSelect">
 select id, username, password, name, gender, image, job,
entrydate, dept_id, create_time, update_time from emp
</sql>
```
###### ```<include>```
通过属性refid，指定包含的SQL片段
```
<include refid="commonSelect"/>
```

## Web后端开发实际操作
### 环境搭建
#### 步骤
- 第1步：准备数据库表
- 第2步：创建springboot工程，引入对应的起步依赖（web、mybatis、mysql驱动、lombok）
- 第3步：配置文件application.properties中引入mybatis的配置信息，准备对应的实体类
- 第4步：准备对应的Mapper、Service(接口、实现类)、Controller基础结构

#### 项目工程目录结构

| 模块/目录     | 说明                           |
|:---------------|:--------------------------------|
| `controller`    | 控制层，存放控制器 `Controller` |
| `mapper`        | 持久层/数据访问层，存放 MyBatis 的 `Mapper` 接口 |
| `pojo`          | 存放实体类                       |
| `service`       | 业务层，存放业务代码               |


### 开发规范
#### REST
REST（Representational State Transfer），表述性状态转换，它是一种软件架构风格
基于当前最为主流的前后端分离模式进行开发
在前后端分离的开发模式中，前后端开发人员都需要根据提前定义好的接口文档，来进行前后端功能的开发
**后端开发人员必须严格遵守提供的接口文档进行后端功能开发（保障开发的功能可以和前端对接**
而在前后端进行交互的时候，我们需要基于当前主流的REST风格的API接口进行交互

##### 传统URL风格与REST风格对比
###### 传统URL风格
```
http://localhost:8080/user/getById?id=1 GET：查询id为1的用户
http://localhost:8080/user/saveUser POST：新增用户
http://localhost:8080/user/updateUser POST：修改用户
http://localhost:8080/user/deleteUser?id=1 GET：删除id为1的用户
```
原始的传统URL，定义比较复杂，且将资源的访问行为对外暴露出来了

###### 基于REST风格URL
```
http://localhost:8080/users/1 GET：查询id为1的用户
http://localhost:8080/users POST：新增用户
http://localhost:8080/users PUT：修改用户
http://localhost:8080/users/1 DELETE：删除id为1的用户
```
即通过URL定位要操作的资源，通过HTTP动词(请求方式)来描述具体的操作

##### REST中的请求方式
在REST风格的URL中，通过四种请求方式，来操作数据的增删改查

| 请求方式 | 说明   |
|:------------|:--------|
| `GET`        | 查询    |
| `POST`       | 新增    |
| `PUT`        | 修改    |
| `DELETE`     | 删除    |

基于REST风格定义URL，URL将会更加简洁、更加规范、更加优雅

注意事项：
- REST是风格，是约定方式，约定不是规定，可以打破
- 描述模块的功能通常使用复数，也就是加s的格式来描述，表示此类资源，而非单个资源。如：users、emps、books…

#### 统一响应结果
前后端工程在进行交互时，使用统一响应结果 Result
Result.class
```
package com.itheima.pojo;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Result {
    private Integer code;//响应码，1 代表成功; 0 代表失败
    private String msg; //响应信息 描述字符串
    private Object data; //返回的数据
    //增删改 成功响应
    public static Result success(){
        return new Result(1,"success",null);
    }
    //查询 成功响应
    public static Result success(Object data){
        return new Result(1,"success",data);
    }
    //失败响应
    public static Result error(String msg){
        return new Result(0,msg,null);
    }
}
```
### 开发流程
进行功能开发时，都是根据如下流程进行
##### 第1步：查看页面原型明确需求
根据页面原型和需求，进行表结构设计、编写接口文档(已提供)
##### 第2步：阅读接口文档
##### 第3步：思路分析
##### 第4步：功能接口开发
就是开发后台的业务功能，一个业务功能，我们称为一个接口
##### 第5步：功能接口测试
功能开发完毕后，先通过Postman进行功能接口测试，测试通过后，再和前端进行联调测试
##### 第6步：前后端联调测试
和前端开发人员开发好的前端工程一起测试


**在类上添加 ```@Slf4j``` 注解时，会自动生成Logger对象，对象名：log（```@Slf4j``` 可以记为酸辣粉4斤）**

### 常见问题
#### 怎么在controller中接收请求路径中的路径参数？
传入参数前加@PathVariable注解


#### 如何限定请求方式是delete？
在方法上加@DeleteMapping注解

#### 如何限定请求方式是POST？
使用@PostMapping注解

#### 怎么在controller中接收json格式的请求参数？
传入参数前加@RequestBody注解，即把前端传递的json数据填充到实体类中

**在Spring当中为了简化请求路径的定义，可以把公共的请求路径，直接抽取到类上，在类上加一个注解@RequestMapping，并指定请求路径，方法中的注解可以省略@RequestMapping指定的路径，直接补全后面的路径**

**注意事项：一个完整的请求路径，应该是类上@RequestMapping的value属性 + 方法上的@RequestMapping的value属性**


### 分页查询
#### 基础分页
##### 需求分析
- 之前做的查询功能，是将数据库中所有的数据查询出来并展示到页面上，如果数据库中的数据很多(假设有十几万条)，将数据全部展示出来肯定不现实，那如何解决这个问题呢？

可以使用分页解决这个问题。每次只展示一页的数据，比如：一页展示10条数据，如果还想看其他的数据，可以通过点击页码进行查询

- 从数据库中进行分页查询，我们要使用 LIMIT 关键字，格式为：limit 开始索引 每页显示的条数
- 开始索引的计算公式： 开始索引 = (当前页码 - 1) * 每页显示条数
##### 思路分析
###### EmpController
- 接收分页参数page、pageSize
- 调用service进行分页查询，获取PageBean
- 响应
###### EmpService
- 调用mapper接口查询总记录数total
- 调用mapper接口获取数据列表rows
- 封装PageBean对象，返回
###### EmpMapper
- ```SELECT COUNT(*) FROM emp;```
- ```SELECT * FROM emp LIMIT ?,?;```
###### 分页查询需要的数据，封装在PageBean对象中
```
@Data
public class PageBean {
    private Long total; //总记录数
    private List rows;  //当前页数据列表
}
```
#### 分页插件
##### 分页查询存在的问题
在Mapper接口中定义两个方法执行两条不同的SQL语句：
- 查询总记录数
- 指定页码的数据列表

在Service当中，调用Mapper接口的两个方法，分别获取：总记录数、查询结果列表，然后在将获取的数据结果封装到PageBean对象中

在未来开发其他项目，只要涉及到分页查询功能(例：订单、用户、支付、商品)，都必须按照以上操作完成功能开发

原始方式的分页查询，存在着"步骤固定"、"代码频繁"的问题
解决方案：可以使用一些现成的分页插件完成。对于Mybatis来讲现在最主流的就是PageHelper
##### PageHelper
PageHelper是Mybatis的一款功能强大、方便易用的分页插件，支持任何形式的单标、多表的分页查询
官网：https://pagehelper.github.io/
##### PageHelper功能
在执行 ```empMapper.list()``` 方法时，就是执行：```select * from emp``` 语句，怎么能够实现分页操作呢？
分页插件帮我们完成了以下操作：
- 先获取到要执行的SQL语句：
```
select * from emp
```
- 把SQL语句中的字段列表，变为：
```
count(*)
```
- 执行SQL语句：
```
select count(*) from emp //获取到总记录数
```
- 再对要执行的SQL语句：
```
select * from emp 进行改造，在末尾添加 limit ? ,?
```
- 执行改造后的SQL语句：
```
select * from emp limit ? , ?
```

##### 代码实现
当使用了PageHelper分页插件进行分页，就无需再Mapper中进行手动分页了。在Mapper中只需要进行正常的列表查询即可。在Service层中，调用Mapper的方法之前设置分页参数，在调用Mapper方法执行查询之后，解析分页结果，并将结果封装到PageBean对象中返回
###### 在pom.xml引入依赖
```
        <dependency>
            <groupId>com.github.pagehelper</groupId>
            <artifactId>pagehelper-spring-boot-starter</artifactId>
            <version>1.4.6</version>
        </dependency>
```
**JDK17版本只支持1.4.6以上版本的PageHelper**

###### EmpMapper
```
@Mapper
public interface EmpMapper {
   //获取当前页的结果列表
   @Select("select * from emp")
   public List<Emp> page(Integer start, Integer pageSize);
}
```
###### EmpServiceImpl
```
@Override
public PageBean page(Integer page, Integer pageSize) {
     // 设置分页参数
     PageHelper.startPage(page, pageSize);
     // 执行分页查询
     List<Emp> empList = empMapper.page();
     // 获取分页结果
     Page<Emp> p = (Page<Emp>) empList; 
     //封装PageBean
     PageBean pageBean = new PageBean(p.getTotal(), p.getResult());
     return pageBean;
}
```
### 文件上传
#### 概念
文件上传，是指将本地图片、视频、音频等文件上传到服务器，供其他用户浏览或下载的过程
文件上传在项目中应用非常广泛，我们经常发微博、发微信朋友圈都用到了文件上传功能

想要完成文件上传这个功能需要涉及到两个部分：
#### 前端程序
前端代码
```
<form action="/upload" method="post" enctype="multipart/form-data">
 姓名: <input type="text" name="username"><br>
 年龄: <input type="text" name="age"><br>
 头像: <input type="file" name="image"><br>
<input type="submit" value="提交">
</form>
```
上传文件页面三要素
- 表单必须有file域，用于选择要上传的文件
```
<input type="file" name="image"/> 1
```
- 表单提交方式必须为POST
通常上传的文件会比较大，所以需要使用 POST 提交方式
- 表单的编码类型enctype必须要设置为：multipart/form-data
普通默认的编码格式是不适合传输大型的二进制数据的，所以在文件上传时，表单的编码格式必须设置为multipart/form-data

**普通默认的编码格式仅会提交上传文件的名字**

#### 服务端程序
##### 首先在服务端定义这么一个controller，用来进行文件上传，然后在controller当中定义一个方法来处理 /upload 请求
##### 在定义的方法中接收提交过来的数据 （方法中的形参名和请求参数的名字保持一致）
- 用户名：String name
- 年龄： Integer age
- 文件： MultipartFile image

**Spring中提供了一个API：MultipartFile，使用这个API就可以来接收到上传的文件**

**如果表单项的名字和方法中形参名不一致，使用@RequestParam注解进行参数绑定**

UploadController代码
```
@Slf4j
@RestController
public class UploadController {
    @PostMapping("/upload")
    public Result upload(String username, Integer age, MultipartFile image) {
       log.info("文件上传：{},{},{}",username,age,image);
       return Result.success();
     }
}
```
#### 本地存储
文件上传时在服务端会产生一个临时文件，请求响应完成之后，这个临时文件被自动删除，并没有进行保存。需要将上传的文件保存在服务器的本地磁盘上
##### 代码实现
- 第1步：在服务器本地磁盘上创建images目录，用来存储上传的文件（例：E盘创建images目录）
- 第2步：使用MultipartFile类提供的API方法，把临时文件转存到本地磁盘目录下

MultipartFile 常见方法：
```
String getOriginalFilename(); //获取原始文件名
void transferTo(File dest); //将接收的文件转存到磁盘文件中
long getSize(); //获取文件的大小，单位：字节
byte[] getBytes(); //获取文件内容的字节数组
InputStream getInputStream(); //获取接收到的文件内容的输入流
```
##### UploadController代码
```
@Slf4j
@RestController
public class UploadController {
    @PostMapping("/upload")
    public Result upload(String username, Integer age, MultipartFile image) throws IOException {
       log.info("文件上传：{},{},{}",username,age,image);
       //获取原始文件名
       String originalFilename = image.getOriginalFilename();
       //将文件存储在服务器的磁盘目录
       image.transferTo(new File("E:/images/"+originalFilename));
       return Result.success();
    }
}
```
此时还存在一个问题，当前是使用原始文件名作为所上传文件的存储名字，当再次上传一个同名文件时，发现会把之前已经上传成功的文件覆盖掉

解决方案：保证每次上传文件时文件名都唯一的（使用UUID获取随机文件名）

##### 最终UploadController代码
```
@Slf4j
@RestController
public class UploadController {
    @PostMapping("/upload")
    public Result upload(String username, Integer age, MultipartFile image) throws IOException {
       log.info("文件上传：{},{},{}",username,age,image);
       //获取原始文件名
       String originalFilename = image.getOriginalFilename();
       //构建新的文件名
       String extname = originalFilename.substring(originalFilename.lastIndexOf("."));//文件扩展名
       String newFileName = UUID.randomUUID().toString()+extname;//随机名+文件扩展名
       //将文件存储在服务器的磁盘目录
       image.transferTo(new File("E:/images/"+newFileName));
       return Result.success();
    }
}
```
##### 上传文件大小限制
在SpringBoot中，文件上传时默认单个文件最大大小为1M
如果需要上传大文件，可以在application.properties进行如下配置
```
#配置单个文件最大上传大小
spring.servlet.multipart.max-file-size=10MB
#配置单个请求最大上传大小(一次请求可以上传多个文件)
spring.servlet.multipart.max-request-size=100MB
```
##### 本地存储的缺点
- 不安全：磁盘如果损坏，所有的文件就会丢失
- 容量有限：如果存储大量的图片，磁盘空间有限(磁盘不可能无限制扩容)
- 无法直接访问

##### 解决方案
- 自己搭建存储服务器，如：fastDFS 、MinIO
- 使用现成的云服务，如：阿里云，腾讯云，华为云

#### 阿里云OSS
##### 概念
###### 云服务
云服务指的就是通过互联网对外提供的各种各样的服务，比如像：语音服务、短信服务、邮件服务、视频直播服务、文字识别服务、对象存储服务等等
当我们在项目开发时需要用到某个或某些服务，就不需要自己来开发了，可以直接使用阿里云提供好的这些现成服务就可以了。比如：在项目开发当中，我们要实现一个短信发送的功能，如果我们项目组自己实现，将会非常繁琐，因为你需要和各个运营商进行对接。而此时阿里云完成了和三大运营商对接，并对外提供了一个短信服务。我们项目组只需要调用阿里云提供的短信服务，就可以很方便的来发送短信了。这样就降低了我们项目的开发难度，同时也提高了项目的开发效率。（大白话：别人帮我们实现好了功能，我们只要调用即可）云服务提供商给我们提供的软件服务通常是需要收取一部分费用的

###### 阿里云对象存储OSS
阿里云对象存储OSS（Object Storage Service），是一款海量、安全、低成本、高可靠的云存储服务。使用OSS，可以通过网络随时存储和调用包括文本、图片、音频和视频等在内的各种文件

在使用了阿里云OSS对象存储服务之后，项目当中如果涉及到文件上传这样的业务，在前端进行文件上传并请求到服务端时，在服务器本地磁盘当中就不需要再来存储文件了。可以直接将接收到的文件上传到oss，由oss帮存储和管理，同时阿里云的oss存储服务还保障了存储内容的安全可靠

##### 使用第三方服务的操作思路
- 准备工作
- 参照官方SDK编写入门程序
- 集成使用

##### SDK
SDK(Software Development Kit)，软件开发工具包，包括辅助软件开发的依赖（jar包）、代码示例等，都可以叫做SDK。简单说，sdk中包含了使用第三方云服务时所需要的依赖，以及一些示例代码。可以参照sdk所提供的示例代码就可以完成入门程序

##### 阿里云oss对象存储服务具体的使用步骤
- 注册阿里云（实名认证）
- 充值
- 开通对象存储服务（oss）
- 创建bucket
- 获取AccessKey（秘钥）
- 参照官方SDK编写入门程序
- 案例集成OSS

**Bucket：存储空间是用户用于存储对象（Object，就是文件）的容器，所有的对象都必须隶属于某个存储空间**

##### 集成
在新增员工的时候，上传员工的图像，而之所以需要上传员工的图像，是因为将来需要在系统页面当中访问并展示员工的图像。而要想完成这个操作，需要做两件事：
- 需要上传员工的图像，并把图像保存起来（存储到阿里云OSS）
- 访问员工图像（通过图像在阿里云OSS的存储地址访问图像）
OSS中的每一个文件都会分配一个访问的url，通过这个url就可以访问到存储在阿里云上的图片。所以需要把url返回给前端，这样前端就可以通过url获取到图像

#### 页面回显
##### 功能
修改信息时，首先先要根据ID查询信息用于页面回显展示，然后用户修改数据之后，点击保存按钮，就可以将修改的数据提交到服务端，保存到数据库
具体操作为：
- 根据ID查询信息
- 保存修改的信息

##### 实现思路
###### EmpController
- 接收路径参数id
- 调用service方法查询数据
- 响应
使用@GetMapping和@PathVariable两个注解
###### EmpService
- 调用mapper接口查询数据
###### EmpMapper
- ```SELECT * FROM emp WHERE id = ?;```

#### 修改数据
##### 实现思路
###### EmpController
- 接受请求参数并封装
- 调用service方法执行修改操作
- 响应
使用@PutMapping和@RequestBody两个注解
###### EmpService
- 补充基础数据
- 调用mapper接口修改数据
###### EmpMapper
```
UPDATE emp SET username=?,name=?,gender=?... WHERE id=?;
```
#### 配置文件
##### 当前项目存在问题
阿里云相关配置信息，直接写死在java代码中了(硬编码)。在做项目时每涉及到一个第三方技术服务，就将其参数硬编码，那么在Java程序中会存在两个问题：
- 如果这些参数发生变化了，就必须在源程序代码中改动这些参数，然后需要重新进行代码的编译，将Java代码编译成class字节码文件再重新运行程序。（比较繁琐）
- 如果开发的是一个真实的企业级项目， Java类可能会有很多，如果将这些参数分散的定义在各个Java类当中，修改一个参数值，就需要在众多的Java代码当中来定位到对应的位置，再来修改参数，修改完毕之后再重新编译再运行（参数配置过于分散，不方便集中的管理和维护）

##### 解决方法
为了解决以上分析的问题，可以将参数配置在配置文件application.properties中。如下：
```
aliyun.oos.endpoint=https://oss-cn-shanghai.aliyuncs.com
aliyun.oos.accessKeyId=
aliyun.oos.accessKeySecret=
aliyun.oos.bucketName=
```
##### @Value注解
在uploadController中使用@Value注解，用于外部配置的属性注入，
###### 语法
```
@Value("${配置文件中的key}")
```

#### yml配置文件
在springboot项目当中是支持多种配置方式的，除了支持properties配置文件以外，还支持yml格式的配置文件
##### 配置文件格式对比
###### application.properties
```
server.port=8080
server.address=127.0.0.1
```
###### application.yml
```
server:
 port: 8080
 address: 127.0.0.1
```
###### application.yaml
```
server:
 port: 8080
 address: 127.0.0.1
```
##### yml 格式的配置文件，后缀名有两种：
- yml （推荐）
- yaml


##### yml格式的数据特点
- 容易阅读
- 容易与脚本语言交互
- 以数据为核心，重数据轻格式

##### yml配置文件的基本语法
- 大小写敏感
- 数值前边必须有空格，作为分隔符
- 使用缩进表示层级关系，缩进时，不允许使用Tab键，只能用空格（idea中会自动将Tab转换为空格）
- 缩进的空格数目不重要，只要相同层级的元素左侧对齐即可
- ```#``` 表示注释，从这个字符一直到行尾，都会被解析器忽略

##### yml文件中常见的数据格式
最为常见的两类：
- 定义对象或Map集合
```
user:
 name: zhangsan
 age: 18
 password: 123456
```
- 定义数组、list或set集合
```
hobby:
 - java
 - game
 - sport
```

##### 使用方法
- 删除application.properties
- 创建新的配置文件： application.yml
```
#数据库配置
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/javawebcase1
    username: root
    password: 123456
  servlet:
    multipart:
      max-file-size: 10MB
      max-request-size: 100MB
#mybatis日志和驼峰命名
mybatis:
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl
    map-underscore-to-camel-case: true

#Ali oos url
aliyun:
  oos:
    endpoint: 
    accessKeyId: 
    accessKeySecret: 
    bucketName: 
```
#### @ConfigurationProperties注解
直接通过@Value注解来进行注入。这种方式本身没有什么问题问题，但是如果需要注入的属性较多(例：需要20多个参数数据)，写起来就会比较繁琐
在Spring中提供了一种简化方式，可以直接将配置文件中配置项的值自动的注入到对象的属性中

##### Spring提供的简化方式套路
- 需要创建一个实现类，且实体类中的属性名和配置文件当中key的名字必须要一致
例如：配置文件当中叫endpoints，实体类当中的属性也得叫endpoints，另外实体类当中的属性还需要提供 getter / setter方法
- 需要将实体类交给Spring的IOC容器管理，成为IOC容器当中的bean对象
- 在实体类上添加 @ConfigurationProperties 注解，并通过perfect属性来指定配置参数项的前缀

##### configuration依赖
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-configuration-processor</artifactId>
</dependency>
```
在pom.xml文件当中配置了configuration依赖之后，在properties或者是yml配置文件当中，就会提示阿里云 OSS 相关的配置项。所以这项依赖的作用就是会自动的识别被 @Configuration Properties 注解标识的bean对象

##### @ConfigurationProperties注解和@Value注解对比
- 相同点
都是用来注入外部配置的属性的
- 不同点
@Value注解只能一个一个的进行外部属性的注入
@ConfigurationProperties可以批量的将外部的属性配置注入到bean对象的属性中

如果要注入的属性非常的多，并且还想做到复用，就可以定义一个bean对象。通过configuration properties 批量将外部的属性配置直接注入到bean对象的属性当中。在其他的类当中，想获取到注入进来的属性，直接注入bean对象，调用 get 方法，就可以获取到对应的属性值了

### 登录认证
#### 登录功能
在登录界面中，可以输入用户的用户名以及密码，然后点击 "登录" 按钮就要请求服务器，服务端判断用户输入的用户名或者密码是否正确。如果正确，则返回成功结果，前端跳转至系统首页面

登录服务端的核心逻辑就是：接收前端请求传递的用户名和密码 ，然后再根据用户名和密码查询用户信息，如果用户信息存在，则说明用户输入的用户名和密码正确。如果查询到的用户不存在，则说明用户输入的用户名和密码错误

##### 实现思路
###### LoginController
- 接收并封装参数
- 调用service方法进行登录
- 响应
使用@PostMapping和@RequestBody两个注解
###### EmpService
- 调用mapper接口查询用户信息
###### EmpMapper
```
SELECT * FROM emp WHERE username = ? AND password = ?;
```
#### 登录校验
##### 当前登录存在问题
在浏览器中新的页面上输入地址： http://localhost:9528/#/system/dept ，发现没有登录仍然可以进入到后端管理系统页面

而真正的登录功能应该是：登陆后才能访问后端系统页面，不登陆则跳转登陆页面进行登陆

为什么会出现这个问题？因为针对于当前所开发的部门管理、员工管理以及文件上传等相关接口来说，在服务器端并没有去判断用户是否登录了。所以无论用户是否登录，都可以访问部门管理以及员工管理的相关数据。所以目前所开发的登录功能，只是徒有其表。而要想解决这个问题，就需要完成一步非常重要的操作：登录校验
##### 登录校验概念
登录校验，指的是在服务器端接收到浏览器发送过来的请求之后，首先要对请求进行校验。校验用户登录了没有，如果用户已经登录了，就直接执行对应的业务操作；如果用户没有登录，就不允许执行相关的业务操作，直接给前端响应一个错误的结果，最终跳转到登录页面，要求登录成功之后，再来访问对应的数据

##### 无状态协议
HTTP协议是无状态协议。所谓无状态，指的是每一次请求都是独立的，下一次请求并不会携带上一次请求的数据。而浏览器与服务器之间进行交互基于HTTP协议，也就意味着通过浏览器来访问登陆接口，实现了登陆的操作，接下来在执行其他业务操作时，服务器并不知道这个员工到底登陆了没有。因为HTTP协议是无状态的，两次请求之间是独立的

##### 登录校验实现思路
具体的实现思路可以分为两部分：
- 在员工登录成功后，需要将用户登录成功的信息存起来，记录用户已经登录成功的标记
- 在浏览器发起请求时，需要在服务端进行统一拦截，拦截后进行登录校验

##### 统一拦截技术
我们程序中所开发的查询功能、删除功能、添加功能、修改功能，都需要使用以上套路进行登录校验。此时就会出现：相同代码逻辑，每个功能都需要编写，就会造成代码非常繁琐

为了简化这块操作，可以使用一种技术：统一拦截技术
通过统一拦截的技术，可以拦截浏览器发送过来的所有的请求，拦截到这个请求之后，就可以通过请求来获取之前所存入的登录标记，在获取到登录标记且标记为登录成功，就说明员工已经登录了。如果已经登录，我们就直接放行(即可以访问正常的业务接口)

要完成以上操作，会涉及到web开发中的两个技术：
- 会话技术
- 统一拦截技术


统一拦截技术现实方案也有两种：
- Servlet规范中的Filter过滤器
- Spring提供的interceptor拦截器

#### 会话技术
##### 会话定义
什么是会话？
在我们日常生活当中，会话指的就是谈话、交谈
在web开发当中，浏览器与服务器之间的一次连接，就称为一次会话

在用户打开浏览器第一次访问服务器的时候，这个会话就建立了，直到有任何一方断开连接，此时会话就结束了。在一次会话当中，是可以包含多次请求和响应的
比如：打开了浏览器来访问web服务器上的资源（浏览器不能关闭、服务器不能断开）
- 第1次：访问的是登录的接口，完成登录操作
- 第2次：访问的是部门管理接口，查询所有部门数据
- 第3次：访问的是员工管理接口，查询员工数据

只要浏览器和服务器都没有关闭，以上3次请求都属于一次会话当中完成的

**需要注意的是：会话是和浏览器关联的，当有三个浏览器客户端和服务器建立了连接时，就会有三个会话。同一个浏览器在未关闭之前请求了多次服务器，这多次请求是属于同一个会话。当关闭浏览器之后，这次会话就结束了。而如果是直接把web服务器关了，那么所有的会话就都结束了**

##### 会话跟踪
一种维护浏览器状态的方法，服务器需要识别多次请求是否来自于同一浏览器，以便在同一次会话的多次请求间共享数据

服务器会接收很多的请求，但是服务器需要识别出这些请求是不是同一个浏览器发出来的。如果是同一个浏览器发出来的，就说明是同一个会话。如果是不同的浏览器发出来的，就说明是不同的会话。而识别多次请求是否来自于同一浏览器的过程，我们就称为会话跟踪

使用会话跟踪技术就是要完成在同一个会话中，多个请求之间进行共享数据

*为什么要共享数据呢？*
*由于HTTP是无状态协议，在后面请求中怎么拿到前一次请求生成的数据呢？此时就需要在一次会话的多次请求之间进行数据共享*

##### 会话跟踪方案
会话跟踪有3种方案
- Cookie（客户端会话跟踪技术）
数据存储在客户端浏览器当中
- Session（服务端会话跟踪技术）
数据存储在储在服务端
- 令牌技术

##### 方案1 -- Cookie
###### 概念
cookie 是客户端会话跟踪技术，它存储在客户端浏览器，使用 cookie 来跟踪会话，就可以在浏览器第一次向服务器发起请求的时候，在服务器端来设置一个cookie
###### 实现流程
- 第1次请求了登录接口，登录接口执行完成之后，可以设置一个cookie，在 cookie 当中可以存储用户相关的一些数据信息。例如：可以在 cookie 当中来存储当前登录用户的用户名，用户的ID

- 服务器端在给客户端在响应数据的时候，会自动将 cookie 响应给浏览器，浏览器接收到响应回来的 cookie 之后，会自动将 cookie 的值存储在浏览器本地。接下来在后续的每一次请求当中，都会将浏览器本地所存储的 cookie 自动携带到服务端

- 接下来在服务端就可以获取到 cookie 的值。可以判断一下这个 cookie 的值是否存在，如果不存在，就说明客户端之前没有访问登录接口；如果存在，就说明客户端之前已经登录完成了。这样就可以基于 cookie 在同一次会话的不同请求之间来共享数据

###### 3个自动
- 服务器会 自动 的将 cookie 响应给浏览器
- 浏览器接收到响应回来的数据之后，会 自动 的将 cookie 存储在浏览器本地
- 在后续的请求当中，浏览器会 自动 的将 cookie 携带到服务器端


###### 自动化进行的原因
因为 cookie 是 HTP 协议当中所支持的技术，而各大浏览器厂商都支持了这一标准。在 HTTP协议官方给我们提供了一个响应头和请求头：
- 响应头 Set-Cookie ：设置Cookie数据的
- 请求头 Cookie：携带Cookie数据的

###### Cookie的优点
HTTP协议中支持的技术（像Set-Cookie 响应头的解析以及 Cookie 请求头数据的携带，都是浏览器自动进行的，是无需我们手动操作的）
###### Cookie的缺点
- 移动端APP(Android、IOS)中无法使用Cookie
- 不安全，用户可以自己禁用Cookie
- Cookie不能跨域

**跨域**
现在的项目，大部分都是前后端分离的，前后端最终也会分开部署
- 例如：前端部署在服务器192.168.150.200 上，端口 80，后端部署在 192.168.150.100上，端口 8080
- 打开浏览器直接访问前端工程，访问url：http://192.168.150.200/login.html
- 然后在该页面发起请求到服务端，而服务端所在地址不再是localhost，而是服务器的IP地址192.168.150.100，假设访问接口地址为：http://192.168.150.100:8080/login
- 此时就存在跨域操作了，因为是在 http://192.168.150.200/login.html 这个页面上访问了http://192.168.150.100:8080/login 接口
- 此时如果服务器设置了一个Cookie，这个Cookie是不能使用的，因为Cookie无法跨域

- 区分跨域的维度
  - 协议
  - IP/协议
  - 端口
只要上述的三个维度有任何一个维度不同，那就是跨域操作


##### 方案2 -- Session
Session是服务器端会话跟踪技术，它是存储在服务器端的。而Session 的底层就是基于 Cookie 来实现的

###### 会话对象Session
基于 Session 来进行会话跟踪，浏览器在第一次请求服务器的时候，可以直接在服务器当中来获取到会话对象Session。如果是第一次请求Session ，会话对象是不存在的，这个时候服务器会自动的创建一个会话对象Session 。而每一个会话对象Session ，都有一个ID，称为 Session 的ID

###### 响应Cookie (JSESSIONID)
接下来，服务器端在给浏览器响应数据的时候，它会将 Session 的 ID 通过 Cookie 响应给浏览器。在响应头当中增加了一个 Set-Cookie 响应头。这个 Set-Cookie 响应头对应的值就是cookie 。 cookie 的名字是固定的，JSESSIONID 代表的服务器端会话对象Session 的 ID。浏览器会自动识别这个响应头，然后自动将Cookie存储在浏览器本地

###### 查找Session
接下来，在后续的每一次请求当中，都会将 Cookie 的数据获取出来，并且携带到服务端。接下来服务器拿到JSESSIONID这个 Cookie 的值，也就是 Session 的ID。拿到 ID 之后，就会从众多的 Session 当中来找到当前请求对应的会话对象Session

这样就可以通过 Session 会话对象在同一次会话的多次请求之间来共享数据了。这就是基于 Session 进行会话跟踪的流程

###### Session的优点
Session是存储在服务端的，安全

###### Session的缺点
- 服务器集群环境下无法直接使用Session
- 移动端APP(Android、IOS)中无法使用Cookie
- 用户可以自己禁用Cookie
- Cookie不能跨域

**Session 底层是基于Cookie实现的会话跟踪，如果Cookie不可用，则该方案，也就失效了**

**服务器集群环境为何无法使用Session**
- 我们现在所开发的项目，一般都不会只部署在一台服务器上，因为一台服务器会存在一个很大的问题，就是单点故障。单点故障指的是一旦这台服务器挂了，整个应用都没法访问了
- 所以现在的企业项目开发中，最终都是以集群的形式来进行部署，也就是同一个项目部署多份。例如：一个项目部署了 3 份。而用户在访问的时候，会访问一台前置的服务器，叫负载均衡服务器，它的作用就是将前端发起的请求均匀的分发给后面的这三台服务器
- 此时通过 session 来进行会话跟踪，可能会存在这样一个问题。用户打开浏览器要进行登录操作，此时会发起登录请求。登录请求到达负载均衡服务器，将这个请求转给了第一台 Tomcat 服务器

Tomcat 服务器接收到请求之后，要获取到会话对象session。获取到会话对象 session之后，要给浏览器响应数据，最终在给浏览器响应数据的时候，会携带一个 cookie的名字，就是 JSESSIONID ，下一次再请求的时候，又会将 Cookie 携带到服务端

此时假如又执行了一次查询操作，要查询部门的数据。这次请求到达负载均衡服务器之后，负载均衡服务器将这次请求转给了第二台 Tomcat 服务器，此时要到第二台Tomcat 服务器当中。根据JSESSIONID 也就是对应的 session 的 ID 值，要找对应的 session 会话对象。但是在第二台服务器当中没有这个ID的会话对象 Session 。此时就出现问题了

同一个浏览器发起了 2 次请求，结果获取到的不是同一个会话对象，这就是Session 会话跟踪方案的缺点，在服务器集群环境下无法直接使用Session

##### 方案三 - 令牌技术
为了解决前两个方案存在的问题，在现在的企业开发当中，基本上都会采用第三种方案，通过令牌技术来进行会话跟踪
###### 令牌
令牌，其实就是一个用户身份的标识，本质是一个字符串

###### 使用令牌跟踪会话的流程
- 在浏览器发起请求。在请求登录接口的时候，如果登录成功，可以生成一个令牌，令牌就是用户的合法身份凭证。接下来在响应数据的时候，就可以直接将令牌响应给前端
- 接下来，在前端程序当中接收到令牌之后，就需要将这个令牌存储起来。可以存储在cookie 当中，也可以存储在其他的存储空间(比如：localStorage)当中
- 接下来，在后续的每一次请求当中，都需要将令牌携带到服务端。携带到服务端之后，需要校验令牌的有效性。如果令牌是有效的，就说明用户已经执行了登录操作，如果令牌是无效的，就说明用户之前并未执行登录操作
- 此时，如果是在同一次会话的多次请求之间，想共享数据，就可以将共享的数据存储在令牌当中

###### 令牌的优点
- 支持PC端、移动端
- 解决集群环境下的认证问题
- 减轻服务器的存储压力（无需在服务器端存储）
###### 令牌的缺点
需要自己实现（包括令牌的生成、令牌的传递、令牌的校验）


现在企业开发当中使用的最多的就是第三种令牌技术进行会话跟踪。而前面的两种传统的方案，现在企业项目开发当中已经很少使用了


#### JWT令牌
##### 概念
- JWT全称：JSON Web Token （官网：https://jwt.io/）
- JWT定义了一种简洁的、自包含的格式，用于在通信双方以json数据格式安全的传输信息。由于数字签名的存在，这些信息是可靠的

  - 简洁：是指jwt就是一个简单的字符串。可以在请求参数或者是请求头当中直接传递
  - 自包含：指的是jwt令牌，看似是一个随机的字符串，但是可以根据自身的需求在jwt令牌中存储自定义的数据内容。如：可以直接在jwt令牌中存储用户的相关信息
  - 简单来讲，jwt就是将原始的json数据格式进行了安全的封装，这样就可以直接基于jwt在通信双方安全的进行信息传输了

##### JWT的组成
JWT令牌由三个部分组成，三个部分之间使用英文的点来分割
###### 第一部分：Header(头)
记录令牌类型、签名算法等。 例如：
```
{"alg":"HS256","type":"JWT"}
```
###### 第二部分：Payload(有效载荷)
携带一些自定义信息、默认信息等。 例如：
```
{"id":"1","username":"Tom"}
```
###### 第三部分：Signature(签名)
防止Token被篡改、确保安全性。将header、payload，并加入指定秘钥，通过指定签名算法计算而来

签名的目的就是为了防jwt令牌被篡改，而正是因为jwt令牌最后一个部分数字签名的存在，所以整个jwt 令牌是非常安全可靠的。一旦jwt令牌当中任何一个部分、任何一个字符被篡改了，整个令牌在校验的时候都会失败，所以它是非常安全可靠的

##### Base64
- 在生成JWT令牌时，会对JSON格式的数据进行一次编码：进行base64编码
- Base64是一种基于64个可打印的字符来表示二进制数据的编码方式。既然能编码，那也就意味着也能解码。所使用的64个字符分别是A到Z、a到z、 0- 9，一个加号，一个斜杠，加起来就是64个字符。任何数据经过base64编码之后，最终就会通过这64个字符来表示。还有等号是一个补位的符号。需要注意的是Base64是编码方式，而不是加密方式

##### 登录认证
JWT令牌最典型的应用场景就是登录认证
- 在浏览器发起请求来执行登录操作，此时会访问登录的接口，如果登录成功之后，需要生成一个jwt令牌，将生成的 jwt令牌返回给前端
- 前端拿到jwt令牌之后，会将jwt令牌存储起来。在后续的每一次请求中都会将jwt令牌携带到服务端
- 服务端统一拦截请求之后，先来判断一下这次请求有没有把令牌带过来，如果没有带过来，直接拒绝访问，如果带过来了，还要校验一下令牌是否是有效。如果有效，就直接放行进行请求的处理

##### JWT登录认证流程
在JWT登录认证的整个流程当中，涉及到两步操作：
- 在登录成功之后，要生成令牌
- 每一次请求当中，要接收令牌并对令牌进行校验

##### JWT令牌的生成
###### 要想使用JWT令牌，需要先引入JWT的依赖
```
<!-- JWT依赖-->
<dependency>
     <groupId>io.jsonwebtoken</groupId>
     <artifactId>jjwt</artifactId>
     <version>0.9.1</version>
</dependency>
```
在引入JWT依赖后，就可以调用工具包中提供的API来完成JWT令牌的生成和校验工具类：Jwts

###### 生成JWT代码实现
```
@Test
public void genJwt(){
    Map<String,Object> claims = new HashMap<>();
    claims.put("id",1);
    claims.put("username","Tom");
    String jwt = Jwts.builder()
        .setClaims(claims) //自定义内容(载荷) 
        .signWith(SignatureAlgorithm.HS256, "itheima") //签名算法
        .setExpiration(new Date(System.currentTimeMillis() +
24*3600*1000)) //有效期
        .compact();
    System.out.println(jwt);
}
```
###### 校验JWT令牌(解析生成的令牌)
```
@Test
public void parseJwt(){
    Claims claims = Jwts.parser()
        .setSigningKey("itheima")//指定签名密钥（必须保证和生成令牌时使用相同的签名密钥）
.parseClaimsJws("eyJhbGciOiJIUzI1NiJ9.eyJpZCI6MSwiZXhwIjoxNjcyNzI5NzMwfQ.fHi0Ub8npbyt71UqLXDdLyipptLgxBUg_mSuGJtXtBk")
        .getBody();
    System.out.println(claims);
}
```
篡改令牌中的任何一个字符，在对令牌进行解析时都会报错，所以JWT令牌是非常安全可靠的
JWT令牌过期后，令牌就失效了

###### 注意事项
- JWT校验时使用的签名秘钥，必须和生成JWT令牌时使用的秘钥是配套的
- 如果JWT令牌解析校验时报错，则说明JWT令牌被篡改或失效了，令牌非法


##### 登录下发令牌
###### 主要是两步操作
- 生成令牌
在登录成功之后来生成一个JWT令牌，并且把这个令牌直接返回给前端
- 校验令牌
拦截前端请求，从请求中获取到令牌，对令牌进行解析校验

用户登录成功后，系统会自动下发JWT令牌，然后在后续的每次请求中，都需要在请求头header中携带到服务端，请求头的名称为 token ，值为 登录时下发的JWT令牌

###### 令牌的生成和下发
实现步骤：
- 引入JWT工具类
在项目工程下创建com.itheima.utils包，并把提供JWT工具类复制到该包下
- 登录完成后，调用工具类生成JWT令牌并返回

###### JWT工具类
```
public class JwtUtils {

    private static String signKey = "smiler";
    private static Long expire = 43200000L;

    /**
     * 生成JWT令牌
     * @param claims JWT第二部分负载 payload 中存储的内容
     * @return
     */
    public static String generateJwt(Map<String, Object> claims){
        String jwt = Jwts.builder()
                .addClaims(claims)
                .signWith(SignatureAlgorithm.HS256, signKey)
                .setExpiration(new Date(System.currentTimeMillis() + expire))
                .compact();
        return jwt;
    }

    /**
     * 解析JWT令牌
     * @param jwt JWT令牌
     * @return JWT第二部分负载 payload 中存储的内容
     */
    public static Claims parseJWT(String jwt){
        Claims claims = Jwts.parser()
                .setSigningKey(signKey)
                .parseClaimsJws(jwt)
                .getBody();
        return claims;
    }
}
```
###### 登录成功，生成JWT令牌并返回
```
@Slf4j
@RestController
public class LoginController {
    //依赖业务层对象
    @Autowired
    EmpService empService;

    @PostMapping("/login")
    public Result login(@RequestBody Emp emp){
      //调用业务层：登录功能
      Emp loginEmp = empService.login(emp);

      //判断：登录用户是否存在
      if(loginEmp != null){
          //自定义信息
          Map<String,Object> claims = new HashMap<>();
          claims.put("id",loginEmp.getID());
          claims.put("username",loginEmp.getUsername());
          claims.put("name",loginEmp.getName());
          //使用JWT工具类，生成身份令牌
          String token = JwtUtils.generateJwt(claims);
          return Result.success(token);
      }
      return Result.error("用户名或密码错误");
    }
}
```
*服务器响应的JWT令牌存储在本地浏览器哪里了？*
- JWT令牌存储在浏览器的本地存储空间local storage中。local storage是浏览器的本地存储，在移动端也是支持的


通过浏览器的开发者工具，可以看到在后续的请求当中，都会在请求头中携带JWT令牌到服务端，而服务端需要统一拦截所有的请求，从而判断是否携带的有合法的JWT令牌。
如何来统一拦截到所有的请求校验令牌的有效性呢？有两种解决方案：
1. Filter过滤器
2. Interceptor拦截器


#### 过滤器Filter
##### 概念
- Filter表示过滤器，是 JavaWeb三大组件(Servlet、Filter、Listener)之一
- 过滤器可以把对资源的请求拦截下来，从而实现一些特殊的功能
  - 使用了过滤器之后，要想访问web服务器上的资源，必须先经过滤器，过滤器处理完毕之后，才可以访问对应的资源
- 过滤器一般完成一些通用的操作，比如：登录校验、统一编码处理、敏感字符处理等

##### 过滤器的基本使用操作
- 第1步，定义过滤器
定义一个类，实现 Filter 接口，并重写其所有方法
- 第2步，配置过滤器
Filter类上加 @WebFilter 注解，配置拦截资源的路径。引导类上加@ServletComponentScan 开启Servlet组件支持

##### Filter接口提供的方法
###### init方法
过滤器的初始化方法。在web服务器启动的时候会自动的创建Filter过滤器对象，在创建过滤器对象的时候会自动调用init初始化方法，这个方法只会被调用一次
###### doFilter方法
这个方法是在每一次拦截到请求之后都会被调用，所以这个方法是会被调用多次的，每拦截到一次请求就会调用一次doFilter()方法。
###### destroy方法
是销毁的方法。当我们关闭服务器的时候，它会自动的调用销毁方法destroy，而这个销毁方法也只会被调用一次

##### @WebFilter注解
在定义完Filter之后，Filter其实并不会生效，还需要完成Filter的配置，需要在Filter类上添加一个注解：@WebFilter，并指定属性urlPatterns，通过这个属性指定过滤器要拦截哪些请求


##### @ServletComponentScan注解
在Filter类上面加了@WebFilter注解之后，接下来还需要在启动类上面加上一个注解@ServletComponentScan，通过@ServletComponentScan注解来开启SpringBoot项目对于Servlet组件的支持

*注意事项：*
- 在过滤器Filter中，如果不执行放行操作，将无法访问后面的资源
- 放行操作：```chain.doFilter(request, response);```


##### 过滤器的执行流程
- 过滤器拦截到了请求之后，如果希望继续访问后面的web资源，就要执行放行操作，放行就是调用 FilterChain对象当中的doFilter()方法，在调用doFilter()这个方法之前所编写的代码属于放行之前的逻辑
- 在放行后访问完 web 资源之后还会回到过滤器当中，回到过滤器后，如有需求还可以执行放行之后的逻辑，放行之后的逻辑写在doFilter()这行代码之后


##### 过滤器的拦截路径配置
Filter可以根据需求，配置不同的拦截资源路径
- 拦截具体路径
/login ，只有访问 /login 路径时，才会被拦截
- 目录拦截
/emps/* ，访问/emps下的所有资源，都会被拦截
- 拦截所有
拦截所有 / ，访问所有资源，都会被拦截
##### 过滤器链
###### 定义
过滤器链指的是在一个web应用程序当中，可以配置多个过滤器，多个过滤器就形成了一个过滤器链
###### 执行顺序
链上的过滤器在执行的时候会一个一个的执行，先执行第一个Filter，放行之后再来执行第二个Filter，执行到最后一个过滤器放行之后，才会访问对应的web资源
访问完web资源之后，按照过滤器的执行流程，还会回到过滤器当中来执行过滤器放行后的逻辑，而在执行放行后的逻辑的时候，顺序是反着的。
先要执行最后一个过滤器放行之后的逻辑，再来执行前面的过滤器放行之后的逻辑，最后再给浏览器响应数据
###### 过滤器执行优先级
过滤器的执行优先级和过滤器的类名有关系。以注解方式配置的Filter过滤器，它的执行优先级是按时过滤器类名的
自动排序确定的，类名排名越靠前，优先级越高

##### 登录校验-Filter
###### 登录校验的基本流程
- 要进入到后台管理系统，必须先完成登录操作，此时就需要访问登录接口login
- 登录成功之后，会在服务端生成一个JWT令牌，并且把JWT令牌返回给前端，前端会将JWT令牌存储下来
- 在后续的每一次请求当中，都会将JWT令牌携带到服务端，请求到达服务端之后，要想去访问对应的业务功能，必须先要校验令牌的有效性
- 对于校验令牌的操作，使用登录校验的过滤器，在过滤器当中来校验令牌的有效性。如果令牌是无效的，就响应一个错误的信息，也不会再去放行访问对应的资源。如果令牌存在，并且是有效的，就会放行去访问对应的web资源，执行相应的业务操作

*Q: 所有的请求，拦截到了之后，都需要校验令牌吗？*
*A: 登录请求例外*
*Q: 拦截到请求后，什么情况下才可以放行，执行业务操作？*
*A: 有令牌，且令牌校验通过(合法)；否则都返回未登录错误结果*

###### 具体的操作步骤：
- 第1步：获取请求url
- 第2步：判断请求url中是否包含login，如果包含，说明是登录操作，放行
- 第3步：获取请求头中的令牌（token）
- 第4步：判断令牌是否存在，如果不存在，返回错误结果（未登录）
- 第5步：解析token，如果解析失败，返回错误结果（未登录）
- 第6步：放行

###### 代码实现
登录校验过滤器：LoginCheckFilter
```
@Slf4j
@WebFilter("/*")
public class LoginCheckFilter implements Filter {
    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        //前置：强制转换为http协议的请求对象、响应对象 （转换原因：要使用子类中特有方法）
        HttpServletRequest httpServletRequest = (HttpServletRequest) servletRequest;
        HttpServletResponse httpServletResponse = (HttpServletResponse) servletResponse;

        //1.获取请求url
        String url = httpServletRequest.getRequestURL().toString();
        log.info("请求路径：{}", url);

        //2.判断请求url中是否包含login，如果包含，说明是登录操作，放行
        if(url.contains("/login")){
            filterChain.doFilter(servletRequest,servletResponse);
            return;
        }

        //3.获取请求头中的令牌（token）
        String token = httpServletRequest.getHeader("token");

        //4.判断令牌是否存在，如果不存在，返回错误结果（未登录）
        if(!StringUtils.hasLength(token)){
            log.info("token不存在");
            Result responceResult = Result.error("NOT_LOGIN");

            //把Result对象转换为JSON格式字符串 (fastjson是阿里巴巴提供的用于实现对象和json的转换工具类)
            String json = JSONObject.toJSONString(responceResult);
            httpServletResponse.setContentType("application/json;charset=utf-8");

            //响应
            httpServletResponse.getWriter().write(json);
            return;
        }

        //5.解析token，如果解析失败，返回错误结果（未登录）

        try {
            JwtUtils.parseJWT(token);

        } catch (Exception e) {
            log.info("解析令牌失败");
            Result responceResult = Result.error("NOT_LOGIN");
            //把Result对象转换为JSON格式字符串 (fastjson是阿里巴巴提供的用于实现对象和json的转换工具类)
            String json = JSONObject.toJSONString(responceResult);
            httpServletResponse.setContentType("application/json;charset=utf-8");

            //响应
            httpServletResponse.getWriter().write(json);
            return;
        }
        //6.放行
        filterChain.doFilter(servletRequest,servletResponse);
    }
}
```


**在上述过滤器的功能实现中，使用到了一个第三方json处理的工具包fastjson。需要引入如下依赖**
```
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.76</version>
</dependency>
```

#### 拦截器Interceptor
##### 概念
###### 什么是拦截器？
- 是一种动态拦截方法调用的机制，类似于过滤器
- 拦截器是Spring框架中提供的，用来动态拦截控制器方法的执行
###### 拦截器的作用
拦截请求，在指定方法调用前后，根据业务需要执行预先设定的代码

在拦截器当中，通常是做一些通用性的操作，比如：可以通过拦截器来拦截前端发起的请求，将登录校验的逻辑全部编写在拦截器当中。在校验的过程当中，如发现用户登录了(携带JWT令牌且是合法令牌)，就可以直接放行，去访问spring当中的资源。如果校验时发现并没有登录或是非法令牌，就可以直接给前端响应未登录的错误信息


##### 拦截器的使用步骤分为两步：
###### 第1步：自定义拦截器
实现HandlerInterceptor接口，并重写其所有方法
- preHandle方法
目标资源方法执行前执行。 返回true：放行 返回false：不放行
- postHandle方法
目标资源方法执行后执行
- afterCompletion方法
视图渲染完毕后执行，最后执行

###### 第2步：注册配置拦截器
实现WebMvcConfigurer接口，并重写addInterceptors方法

##### 拦截器的拦截路径配置
###### 在注册配置拦截器的时候，要指定拦截器的拦截路径，通过 addPathPatterns("要拦截路径") 方法，就可以指定要拦截哪些资源
###### 在配置拦截器时，不仅可以指定要拦截哪些资源，还可以指定不拦截哪些资源，只需要调用 excludePathPatterns("不拦截路径") 方法，指定哪些资源不需要拦截

###### 常见拦截路径设置

| 匹配规则       | 说明                     | 示例匹配情况                                      |
|:----------------|:--------------------------|:--------------------------------------------------|
| `/*`             | 一级路径                   | 能匹配 `/depts`、`/emps`、`/login`，不能匹配 `/depts/1` |
| `/**`            | 任意级路径                 | 能匹配 `/depts`、`/depts/1`、`/depts/1/2`         |
| `/depts/*`       | `/depts` 下的一级路径       | 能匹配 `/depts/1`，不能匹配 `/depts/1/2`、`/depts` |
| `/depts/**`      | `/depts` 下的任意级路径     | 能匹配 `/depts`、`/depts/1`、`/depts/1/2`，不能匹配 `/emps/1` |


##### 拦截器的执行流程
- 当打开浏览器来访问部署在web服务器当中的web应用时，此时定义的过滤器会拦截到这次请求。拦截到这次请求之后，它会先执行放行前的逻辑，然后再执行放行操作。而由于当前是基于springboot开发的，所以放行之后进入到spring的环境当中，也就是要来访问定义的controller当中的接口方法
- Tomcat并不识别编写的Controller程序，但是它识别Servlet程序，所以在Spring的Web环境中提供了一个非常核心的Servlet：DispatcherServlet（前端控制器），所有请求都会先进行到DispatcherServlet，再将请求转给Controller
- 定义了拦截器后，在执行Controller的方法之前，请求会被拦截器拦截住。执行preHandle() 方法，这个方法执行完成后需要返回一个布尔类型的值，如果返回true，就表示放行本次操作，会继续访问controller中的方法；如果返回false，则不会放行（controller中的方法也不会执行）
- 在controller中的方法执行完毕之后，再回过来执行 postHandle() 方法以及afterCompletion() 方法，然后再返回给DispatcherServlet，最终再来执行过滤器当中放行后的逻辑。执行完毕之后，最终给浏览器响应数据

##### 过滤器和拦截器的区别
- 接口规范不同
过滤器需要实现Filter接口，而拦截器需要实现HandlerInterceptor接口
- 拦截范围不同
过滤器Filter会拦截所有的资源，而Interceptor只会拦截Spring环境中的资源


##### 登录校验- Interceptor
登录校验的业务逻辑以及操作步和登录校验Filter过滤器当中的逻辑是完全一致的
###### 登录校验拦截器
```
@Slf4j
@Component
public class LoginCheckInterceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        //1.获取请求url
        //2.判断请求url中是否包含login，如果包含，说明是登录操作，放行

        //3.获取请求头中的令牌（token）
        String token = request.getHeader("token");

        //4.判断令牌是否存在，如果不存在，返回错误结果（未登录）
        if (!StringUtils.hasLength(token)) {
            log.info("token不存在");
            Result responceResult = Result.error("NOT_LOGIN");
            //把Result对象转换为JSON格式字符串 (fastjson是阿里巴巴提供的用于实现对象和json的转换工具类)
            String json = JSONObject.toJSONString(responceResult);
            response.setContentType("application/json;charset=utf-8");
            //响应
            response.getWriter().write(json);
            return false;
        }
        //5.解析token，如果解析失败，返回错误结果（未登录）
        try {
            JwtUtils.parseJWT(token);
        } catch (Exception e) {
            log.info("解析令牌失败");
            Result responceResult = Result.error("NOT_LOGIN");
            //把Result对象转换为JSON格式字符串 (fastjson是阿里巴巴提供的用于实现对象和json的转换工具类)
            String json = JSONObject.toJSONString(responceResult);
            response.setContentType("application/json;charset=utf-8");
            //响应
            response.getWriter().write(json);
            return false;
        }
        //6.放行
        return true;
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
        log.info("放行后");
        HandlerInterceptor.super.postHandle(request, response, handler, modelAndView);
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        log.info("最后执行");
        HandlerInterceptor.super.afterCompletion(request, response, handler, ex);
    }
}
```
###### 注册配置拦截器
```
@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Autowired
    LoginCheckInterceptor loginCheckInterceptor;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(loginCheckInterceptor).addPathPatterns("/**").excludePathPatterns("/login");
    }
}
```
### 异常处理
#### 不进行异常处理时存在的问题
如果不做异常处理，出现异常之后，服务器返回的数据是一个JSON格式的数据。但这种JSON格式的数据不是开发规范中的统一响应结果Result。由于返回的数据不符合开发规范，所以前端并不能解析出响应的JSON数据

##### 当没有做任何的异常处理时，三层架构处理异常的方案是：
- Mapper接口在操作数据库的时候出错，此时异常会往上抛(谁调用Mapper就抛给谁)，即抛给service
- service 中存在异常，会抛给controller
- 在controller当中，没有做任何的异常处理，所以异常会再往上抛。最终抛给框架，框架就会返回一个JSON格式的数据，里面封装的就是错误的信息，但是框架返回的JSON格式的数据并不符合我们的开发规范

#### 解决方案
在三层构架项目中，出现了异常，该如何处理
##### 方案一
在所有Controller的所有方法中进行try…catch处理
- 缺点
代码臃肿（不推荐）
##### 方案二
全局异常处理器
- 优点
简单、优雅（推荐）

#### 全局异常处理器
##### 定义全局异常处理器
- 定义全局异常处理器，就是定义一个类，在类上加上一个注解@RestControllerAdvice，加上这个注解就代表定义了一个全局异常处理器
- 在全局异常处理器当中，需要定义一个方法来捕获异常，在这个方法上需要加上注解@ExceptionHandler。通过@ExceptionHandler注解当中的value属性来指定要捕获的是哪一类型的异常

#### 代码实现
```
@RestControllerAdvice
public class GlobalExceptionHandler {
    //处理异常
    @ExceptionHandler(Exception.class) //指定能够处理的异常类型
    public Result ex(Exception e){
        e.printStackTrace();//打印堆栈中的异常信息
        //捕获到异常之后，响应一个标准的Result
        return Result.error("对不起,操作失败,请联系管理员");
    }
}
```
* ```@RestControllerAdvice = @ControllerAdvice + @ResponseBody``` ，处理异常的方法返回值会转换为json后再响应给前端*

#### 全局异常处理器的使用，主要涉及到两个注解
##### @RestControllerAdvice
表示当前类为全局异常处理器
##### @ExceptionHandler
指定可以捕获哪种类型的异常进行处理


## 事务
### 事务管理
#### 事务
##### 概念
事务是一组操作的集合，它是一个不可分割的工作单位。事务会把所有的操作作为一个整体，一起向数据库提交或者是撤销操作请求。所以这组操作要么同时成功，要么同时失败
##### 事务的操作主要有三步
- 开启事务（一组操作开始前，开启事务）
```
start transaction / begin ;
```
- 提交事务（这组操作全部成功后，提交事务）
```
commit ;
```
- 回滚事务（中间任何一个操作出现异常，回滚事务）
```
rollback ;
```

#### Spring事务管理
##### @Transactional注解
###### @Transactional作用
在当前这个方法执行开始之前来开启事务，方法执行完毕之后提交事务。如果在这个方法执行的过程当中出现了异常，就会进行事务的回滚操作
###### @Transactional注解
一般在业务层当中来控制事务，因为在业务层当中，一个业务功能可能会包含多个数据访问的操作。在业务层来控制事务，就可以将多个数据访问操作控制在一个事务范围内

###### @Transactional注解书写位置
- 方法
当前方法交给spring进行事务管理
- 类
当前类中所有的方法都交由spring进行事务管理
- 接口
接口下所有的实现类当中所有的方法都交给spring 进行事务管理

*可以在application.yml配置文件中开启事务管理日志，就可以在控制看到和事务相关的日志信息*
```
#spring事务管理日志
logging:
  level:
    org.springframework.jdbc.support.JdbcTransactionManager: debug
```
##### @Transactional注解当中的两个常见属性
- 异常回滚属性：rollbackFor
- 事务传播行为：propagation

##### 异常回滚属性：rollbackFor
- 默认情况下，只有出现RuntimeException(运行时异常)才会回滚事务
- 要想让所有的异常都回滚，需要配置@Transactional注解当中的rollbackFor属性，指定出现何种异常类型回滚事务
```
@Transactional(rollbackFor = Exception.class)
```

##### 事务传播行为：propagation
###### 事务的传播行为
事务的传播行为就是当一个事务方法被另一个事务方法调用时，这个事务方法应该如何进行事务控制
###### 常见的事务传播行为
在@Transactional注解的后面指定一个属性propagation，通过propagation 属性来指定传播行为

| 事务传播行为       | 说明                                                           |
|:--------------------|:----------------------------------------------------------------|
| `REQUIRED`            | 【默认值】需要事务，有则加入，无则创建新事务                      |
| `REQUIRES_NEW`        | 需要新事务，无论当前是否存在，总是创建新事务                        |
| `SUPPORTS`            | 支持事务，有则加入，无则在无事务状态下运行                          |
| `NOT_SUPPORTED`       | 不支持事务，在无事务状态下运行，若存在事务，则挂起当前事务              |
| `MANDATORY`           | 必须有事务，否则抛出异常                                           |
| `NEVER`               | 必须没有事务，否则抛出异常                                          |


事务的传播行为最常用的只有两个：REQUIRED、REQUIRES_NEW。
- REQUIRED ：大部分情况下都是用该传播行为即可
- REQUIRES_NEW ：当不希望事务之间相互影响时，可以使用该传播行为。比如：下订单前需要记录日志，不论订单保存成功与否，都需要保证日志记录能够记录成功


## AOP
AOP也是spring框架的第二大核心
### AOP概述
#### AOP概念
AOP英文全称：Aspect Oriented Programming（面向切面编程、面向方面编程），面向切面编程就是面向特定方法编程

#### AOP的作用
在程序运行期间在不修改源代码的基础上对已有方法进行增强（无侵入性: 解耦）

### AOP使用步骤
#### 导入依赖
在pom.xml中导入AOP的依赖
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```
#### 编写AOP程序
针对于特定方法根据业务需要进行编程


### AOP应用场景
#### 记录系统的操作日志
#### 权限控制
#### 事务管理
Spring事务管理，底层其实是通过AOP来实现的，只要添加@Transactional注解之后，AOP程序自动会在原始方法运行前先来开启事务，在原始方法运行完毕之后提交或回滚事务


### AOP面向切面编程的优势
- 代码无侵入
没有修改原始的业务方法，就已经对原始的业务方法进行了功能的增强或者是功能的改变
- 减少了重复代码
- 提高开发效率
- 维护方便

### AOP核心概念
#### 连接点 -- JoinPoint
可以被AOP控制的方法（暗含方法执行时的相关信息）
- 连接点指的是可以被aop控制的方法。例如：入门程序当中所有的业务方法都是可以被aop控制的方法
- 在SpringAOP提供的JoinPoint当中，封装了连接点方法在执行时的相关信息

#### 通知 -- Advice
指哪些重复的逻辑，也就是共性功能（最终体现为一个方法）
**在AOP面向切面编程当中，只需要将重复的代码逻辑抽取出来单独定义。抽取出来的这一部分重复的逻辑，就是共性的功能**

#### 切入点 -- PointCut
匹配连接点的条件，通知仅会在切入点方法执行时被应用
**在通知当中，定义的共性功能到底要应用在哪些方法上？此时就涉及到了切入点pointcut概念。切入点指的是匹配连接点的条件。通知仅会在切入点方法运行时才会被应用。在aop的开发当中，通常会通过切入点表达式来描述切入点**

#### 切面 -- Aspect
描述通知与切入点的对应关系（通知+切入点）
- 当通知和切入点结合在一起，就形成了一个切面。通过切面就能够描述当前aop程序需要针对于哪个原始方法，在什么时候执行什么样的操作
- 切面所在的类，称为切面类（被@Aspect注解标识的类）

#### 目标对象 -- Target
通知所应用的对象
**目标对象指的就是通知所应用的对象**


*Spring的AOP底层是基于动态代理技术来实现的，也就是说在程序运行的时候，会自动的基于动态代理技术为目标对象生成一个对应的代理对象。在代理对象当中就会对目标对象当中的原始方法进行功能的增强*


### AOP通知类型
#### @Around
环绕通知，此注解标注的通知方法在目标方法前、后都被执行
#### @Before
前置通知，此注解标注的通知方法在目标方法前被执行
#### @After
后置通知，此注解标注的通知方法在目标方法后被执行，无论是否有异常都会执行
#### @AfterReturning
返回后通知，此注解标注的通知方法在目标方法后被执行，有异常不会执行
#### @AfterThrowing
异常后通知，此注解标注的通知方法发生异常后执行。没有发生异常的情况下不会执行

### 在使用通知时的注意事项
- @Around环绕通知需要自己调用 ProceedingJoinPoint.proceed() 来让原始方法执行，其他通知不需要考虑目标方法执行
- @Around环绕通知方法的返回值，必须指定为Object，来接收原始方法的返回值，否则原始方法执行完毕，是获取不到返回值的

### @PointCut注解
Spring提供了@PointCut注解，该注解的作用是将公共的切入点表达式抽取出来，需要用到时引用该切入点表达式即可

当切入点方法使用private修饰时，仅能在当前切面类中引用该表达式， 当外部其他切面类中也要引用当前类中的切入点表达式，就需要把private改为public

#### 语法
全类名.方法名()，具体形式如下：
```
@Slf4j
@Component
@Aspect
public class MyAspect2 {
    //引用MyAspect1切面类中的切入点表达式
    @Before("com.itheima.aspect.MyAspect1.pt()")
    public void before(){
       log.info("MyAspect2 -> before ...");
    }
}
```

##### 代码实现
```
@Slf4j
@Component
@Aspect
public class MyAspect {
    //切入点方法（公共的切入点表达式）
    @Pointcut("execution(* com.smiler.service.*.*(..))")
    public void pt(){}

    //前置通知（引用切入点）
    @Before("pt()")
    public void before(JoinPoint joinPoint){
        log.info("Run before");
    }

    //环绕通知
    @Around("pt()")
    public Object Around(ProceedingJoinPoint proceedingJoinPoint) throws Throwable {
        log.info("Run before Around");
        Object object = proceedingJoinPoint.proceed();
        log.info("Run after Around");
        return object;
    }

    //后置通知
    @After("pt()")
    public void after(JoinPoint joinPoint){
        log.info("Run after");
    }

    //返回后通知（程序在正常执行的情况下，会执行的后置通知）
    @AfterReturning("pt()")
    public void afterReturning(JoinPoint joinPoint){
        log.info("run afterReturning");
    }

    //异常通知（程序在出现异常的情况下，执行的后置通知）
    @AfterThrowing("pt()")
    public void afterThrowing(JoinPoint joinPoint){
        log.info("run afterThrowing");
    }
}
```

### 通知顺序
当在项目开发当中，我们定义了多个切面类，而多个切面类中多个切入点都匹配到了同一个目标方法。此时当目标方法在运行的时候，这多个切面类当中的这些通知方法都会运行

#### 在不同切面类中，默认按照切面类的类名字母排序
##### 目标方法前的通知方法
字母排名靠前的先执行
##### 目标方法后的通知方法
字母排名靠前的后执行

#### 如果想控制通知的执行顺序，有两种方式
- 修改切面类的类名（这种方式非常繁琐、而且不便管理）
- 使用Spring提供的@Order注解，在切面类上面加上@Order注解，来控制不同的切面类通知的执行顺序

@Order注解的执行顺序（前置通知：数字越小先执行; 后置通知：数字越小越后执行）

### 切入点表达式
#### 概念
##### 定义
描述切入点方法的一种表达式
##### 作用
主要用来决定项目中的哪些方法需要加入通知
##### 常见形式
- ```execution(……)```
根据方法的签名来匹配
- ```@annotation(……)```
根据注解匹配

#### execution
execution主要根据方法的返回值、包名、类名、方法名、方法参数等信息来匹配
##### 语法
```
execution(访问修饰符? 返回值 包名.类名.?方法名(方法参数) throws 异常?)
```
其中带 ? 的表示可以省略的部分
- 访问修饰符：可省略（比如: public、protected），一般都省略
- 包名.类名： 可省略，一般不省略上
- throws 异常：可省略（注意是方法上声明抛出的异常，不是实际抛出的异常），一般都省略

##### 可以使用通配符描述切入点
###### ```*```
单个独立的任意符号，可以通配任意返回值、包名、类名、方法名、任意类型的一个参数，也可以通配包、类、方法名的一部分
###### ```..```
多个连续的任意符号，可以通配任意层级的包，或任意类型、任意个数的参数

##### 切入点表达式的语法规则
- 方法的访问修饰符可以省略
- 返回值可以使用 * 号代替（任意返回值类型）
- 包名可以使用 * 号代替，代表任意包（一层包使用一个 * ）
- 使用 .. 配置包名，标识此包以及此包下的所有子包
- 类名可以使用 * 号代替，标识任意类
- 方法名可以使用 * 号代替，表示任意方法
- 可以使用 * 配置参数，一个任意类型的参数
- 可以使用 .. 配置参数，任意个任意类型的参数
- 可以使用 且（&&）、或（||）、非（!） 来组合比较复杂的切入点表达式

##### 切入点表达式的书写建议
- 所有业务方法名在命名时尽量规范，方便切入点表达式快速匹配。如：查询类方法都是 find 开头，更新类方法都是update开头
- 描述切入点方法通常基于接口描述，而不是直接描述实现类，增强拓展性
- 在满足业务需要的前提下，尽量缩小切入点的匹配范围。如：包名匹配尽量不使用 ..，使用 * 匹配单个包

#### @annotation
如果要匹配多个无规则的方法，比如：list()和 delete()这两个方法。这个时候基于execution这种切入点表达式来描述就不是很方便了
此时，可以借助于另一种切入点表达式@annotation来描述这一类的切入点，从而来简化切入点表达式的书写

##### 实现步骤
- 第1步：编写自定义注解
- 第2步：在业务类要作为连接点的方法上添加自定义注解

##### 自定义注解：MyLog
```
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface MyLog {
}
```
##### 业务类
在对应的方法上添加@MyLog注解

##### 切面类
```
@Slf4j
@Component
@Aspect
public class MyAspect {
    //针对list方法、delete方法进行前置通知和后置通知
    //前置通知
    @Before("@annotation(com.itheima.anno.MyLog)")
    public void before(){
       log.info("MyAspect -> before ...");
    }
    //后置通知
    @After("@annotation(com.itheima.anno.MyLog)")
    public void after(){
       log.info("MyAspect -> after ...");
    }
}
```
#### execution与annotation对比
##### execution切入点表达式
- 根据指定的方法的描述信息来匹配切入点方法，这种方式也是最为常用的一种方式
- 如果要匹配的切入点方法的方法名不规则，或者有一些比较特殊的需求，通过execution切入点表达式描述比较繁琐
##### annotation 切入点表达式
基于注解的方式来匹配切入点方法。这种方式虽然多一步操作，需要自定义一个注解，但是相对来比较灵活。需要匹配哪个方法，就在方法上加上对应的注解就可以了

### 连接点
#### 概念
- 连接点可以简单理解为可以被AOP控制的方法
- 在SpringAOP当中，连接点又特指方法的执行

#### 使用方法
在Spring中用JoinPoint抽象了连接点，用它可以获得方法执行时的相关信息，如目标类名、方法名、方法参数等
- 对于@Around通知，获取连接点信息只能使用ProceedingJoinPoint类型
- 对于其他四种通知，获取连接点信息只能使用JoinPoint，它是ProceedingJoinPoint的父类型

#### 代码实现
##### 获取目标对象的类名
```
        String className = proceedingJoinPoint.getTarget().getClass().getName();
        log.info("类名是" + className);
```
##### 获取目标方法的方法名
```
        String methodName = proceedingJoinPoint.getSignature().getName();
        log.info("方法名是" + methodName);
```
##### 获取目标方法运行时传入的参数
```
        Object[] args = proceedingJoinPoint.getArgs();
        log.info("传入参数是" + Arrays.toString(args));
```
##### 放行目标方法执行
```
        Object result = proceedingJoinPoint.proceed();
```
##### 获取目标方法运行的返回值
```
        log.info("返回值是" + result);
```

## SpingBoot原理
### 配置优先级
#### 配置文件优先级排名（从高到低）：
1. properties配置文件
2. yml配置文件
3. yaml配置文件

**虽然springboot支持多种格式配置文件，但是在项目开发时，推荐统一使用一种格式的配置（yml是主流）**

#### 其他配置方式
SpringBoot为了增强程序的扩展性，除了支持配置文件的配置方式以外，还支持另外两种常见的配置方式
##### Java系统属性配置 （格式： ```-Dkey=value```）
例如：```-Dserver.port=9000```
##### 命令行参数 （格式：```--key=value```）
例如：```--server.port=10010```


#### 在idea当中运行程序时，指定Java系统属性和命令行参数的方式
##### 编辑启动程序的配置信息
在配置信息中的VM options中配置系统属性参数
在配置信息中的Program arguments中配置命令行参数

#### 打包程序运行时指定Java系统属性和命令行参数
- 第1步：执行maven打包指令package，把项目打成jar文件
- 第2步：使用命令：java -jar 方式运行jar文件程序


**注意事项：Springboot项目进行打包时，需要引入插件 spring-boot-maven-plugin (基于官网骨架创建项目，会自动添加该插件)**

#### SpringBoot项目属性配置方式
在SpringBoot项目当中，常见的属性配置方式有5种， 3种配置文件，加上2种外部属性的配置(Java系统属性、命令行参数)。它们的优先级(从低到高)：
1. application.yaml
2. application.yml
3. application.properties
4. java系统属性（-Dxxx=xxx）
5. 命令行参数（--xxx=xxx）

### Bean管理
可以通过Spring当中提供的注解@Component以及它的三个衍生注解（@Controller、@Service、@Repository）来声明IOC容器中的bean对象，也可以为应用程序注入运行时所需要依赖的bean对象，也就是依赖注入DI
#### 从IOC容器中获取bean对象
默认情况下，SpringBoot项目在启动的时候会自动创建IOC容器(也称为Spring容器)，并且在启动过程中会自动将bean对象都创建好，存放在IOC容器当中。应用程序在运行时需要依赖什么bean对象，就直接进行依赖注入

而在Spring容器中提供了一些方法，可以主动从IOC容器中获取到bean对象，主要有3种方式：
##### 根据name获取bean
```
Object getBean(String name)
```
##### 根据类型获取bean
```
<T> T getBean(Class<T> requiredType)
```
##### 根据name获取bean（带类型转换）
```
<T> T getBean(String name, Class<T> requiredType)
```

要从IOC容器中获取到bean对象，需要先拿到IOC容器对象。想获取到IOC容器，直接将IOC容器对象注入进来就可以了
```
@Autowired
private ApplicationContext applicationContext; //IOC容器对象
```

**相同的bean对象在IOC容器当中只有一个（默认情况下，IOC中的bean对象是单例）**
**要想将bean对象设置为非单例(每次获取的bean都是一个新对象)，需要运用bean作用域**

**注意事项：**
**【Spring项目启动时，会把其中的bean都创建好】还会受到作用域及延迟初始化影响，这里主要针对于默认的单例非延迟加载的bean而言**

#### Bean作用域
##### 在Spring中支持五种作用域，后三种在web环境才生效
- singleton
容器内同名称的bean只有一个实例（单例）（默认）
- prototype
每次使用该bean时会创建新的实例（非单例）
- request
每个请求范围内会创建新的实例（web环境中，了解）
- session
每个会话范围内会创建新的实例（web环境中，了解）
- application
每个应用范围内会创建新的实例（web环境中，了解）

##### 如何设置一个bean的作用域
使用Spring中的@Scope注解来进行配置作用域
例如：
```
@Scope("prototype") //bean作用域为非单例
@Lazy //延迟加载
@RestController
@RequestMapping("/depts")
public class DeptController {
}
```

注意事项：
- IOC容器中的bean默认使用的作用域：singleton (单例)
- 默认singleton的bean，在容器启动时被创建，可以使用@Lazy注解来延迟初始化(延迟到第一次使用时)
- prototype的bean，每一次使用该bean的时候都会创建一个新的实例
- 实际开发当中，绝大部分的Bean是单例的，也就是说绝大部分Bean不需要配置scope属性

#### 第三方Bean
之前我们所配置的bean，像controller、service，dao三层体系下编写的类，这些类都是在项目当中自己定义的类(自定义类)。当需要声明这些bean对象时，只需要在类上加上@Component以及它的三个衍生注解（@Controller、@Service、@Repository）

但是在项目开发中，还有一种情况就是这个类不是自己编写的，而是引入的第三方依赖当中提供的

例如：dom4j就是第三方组织提供的。 dom4j中的SAXReader类就是第三方编写的

**第三方提供的类是只读的。无法在第三方类上添加@Component注解或衍生注解**

**如果要管理的bean对象来自于第三方（不是自定义的），需要用到@Bean注解**

##### 解决方案1：在启动类中添加@Bean标识的方法
```
//声明第三方bean
@Bean //将当前方法的返回值对象交给IOC容器管理, 成为IOC容器bean
public SAXReader saxReader(){
     return new SAXReader();
 }
```
**项目中要保证启动类的纯粹性，一般不应该在启动类中声明第三方Bean**

##### 解决方案2：在配置类中定义@Bean标识的方法
需要定义第三方Bean时， 通常会单独定义一个配置类
```
@Configuration //配置类 (在配置类当中对第三方bean进行集中的配置管理)
public class CommonConfig {
    //声明第三方bean
    @Bean //将当前方法的返回值对象交给IOC容器管理, 成为IOC容器bean
          //通过@Bean注解的name/value属性指定bean名称, 如果未指定, 默认是方法名
    public SAXReader reader(DeptService deptService){
        System.out.println(deptService);
        return new SAXReader();
    }
}
```
注意事项：
- 通过@Bean注解的name或value属性可以声明bean的名称，如果不指定，默认bean的名称就是方法名
- 如果第三方bean需要依赖其它bean对象，直接在bean定义方法中设置形参即可，容器会根据类型自动装配

##### 关于Bean需要保持的原则
- 如果是在项目当中程序员自己定义的类，想将这些类交给IOC容器管理，直接使用@Component以及它的衍生注解来声明
- 如果这个类不是程序员自己定义的，而是引入的第三方依赖当中提供的类，要想将这个类交给IOC容器管理，需要在配置类中定义一个方法，在方法上加上一个@Bean注解来声明第三方的bean对象

### SpringBoot原理
SpringBoot使程序员能够集中精力地去关注业务功能的开发，而不用过多地关注框架本身的配置使用
#### Spring家族的框架
Spring是目前世界上最流行的Java框架，它可以帮助程序员更加快速、更加容易的来构建Java项目。在Spring家族当中提供了很多优秀的框架，所有的框架都是基于一个基础框架的SpringFramework(也就是Spring框架)。如果直接基于Spring框架进行项目的开发，会比较繁琐


这个繁琐主要体现在两个地方
- 在pom.xml中依赖配置比较繁琐，在项目开发时，需要自己去找到对应的依赖，还需要找到依赖它所配套的依赖以及对应版本，否则就会出现版本冲突问题
- 在使用Spring框架进行项目开发时，需要在Spring的配置文件中做大量的配置，这就造成Spring框架入门难度较大，学习成本较高

基于Spring存在的问题，官方在Spring框架4.0版本之后，又推出了一个全新的框架：SpringBoot
- 通过SpringBoot来简化Spring框架的开发(是简化不是替代)。直接基于SpringBoot来构建Java项目，会让项目开发更加简单，更加快捷

SpringBoot框架之所以使用起来更简单更快捷，是因为SpringBoot框架底层提供了两个非常重要的功能
- 起步依赖
通过SpringBoot所提供的起步依赖，就可以大大的简化pom文件当中依赖的配置，从而解决了Spring框架当中依赖配置繁琐的问题
- 自动配置
通过自动配置的功能就可以大大的简化框架在使用时bean的声明以及bean的配置。程序员只需要引入程序开发时所需要的起步依赖，项目开发时所用到常见的配置都已经有了，可以直接使用

#### 起步依赖
如果没有使用SpringBoot，而用的是Spring框架进行web程序的开发，就需要引入web程序开发所需要的一些依赖
- spring-webmvc依赖：这是Spring框架进行web程序开发所需要的依赖
- servlet-api依赖：Servlet基础依赖
- jackson-databind依赖：JSON处理工具包
- 如果要使用AOP，还需要引入aop依赖、aspect依赖
- 项目中所引入的这些依赖，还需要保证版本匹配，否则就可能会出现版本冲突问题

如果使用了SpringBoot，就不需要像上面这么繁琐的引入依赖了。只需要引入一个依赖就可以了，那就是web开发的起步依赖：
```
springboot-starter-web
```

**起步依赖的原理是Maven的依赖传递**

*在SpringBoot提供的起步依赖当中，已提供了当前程序开发所需要的所有的常见依赖(官网地址：https://docs.spring.io/spring-boot/docs/2.7.7/reference/htmlsingle/#using.build-systems.starters )*
- 例如：springboot-starter-web，是web开发的起步依赖，集成了web开发中常见的依赖：json、web、webmvc、tomcat等。只需要引入这一个起步依赖，其他的依赖都会自动的通过Maven的依赖传递进来

#### 自动配置
##### 概念
- SpringBoot的自动配置就是当Spring容器启动后，一些配置类、bean对象就自动存入到了IOC容器中，不需要我们手动去声明，从而简化了开发，省去了繁琐的配置操作
- 例如：我们要进行事务管理、要进行AOP程序的开发，此时就不需要再去手动的声明这些bean对象了，直接使用就可以，从而大大简化程序的开发，省去了繁琐的配置操作
- 在IOC容器中除了自己定义的bean以外，还有很多配置类，这些配置类都是SpringBoot在启动的时候加载进来的。这些配置类加载进来之后，它也会生成很多的bean对象

**配置类最终也是SpringIOC容器当中的一个bean对象**

例如：配置类GsonAutoConfiguration里面有一个bean，bean的名字叫gson，它的类型是Gson
com.google.gson.Gson是谷歌包中提供的用来处理JSON格式数据的

**当我们想要使用这些配置类中生成的bean对象时，可以使用@Autowired就自动注入了**

*在当前项目中我们并没有声明谷歌提供的Gson这么一个bean对象，然而却可以通过@Autowired从Spring容器中注入bean对象，是因为SpringBoot项目在启动时通过自动配置完成了bean对象的创建*



##### 第三方依赖当中的bean以及配置类不生效问题
在引入依赖之后如何将依赖jar包当中所定义的配置类以及bean加载到SpringIOC容器

自己引入进来的第三方依赖当中的bean以及配置类不生效
- 原因是，在类上添加@Component注解来声明bean对象时，还需要保证@Component注解能被Spring的组件扫描到
- SpringBoot项目中的@SpringBootApplication注解，具有包扫描的作用，但是它只会扫描启动类所在的当前包以及子包
- 当前包：com.smiler， 第三方依赖中提供的包：com.example（扫描不到）


##### 解决方案1--@ComponentScan组件扫描
语法：
```
@ComponentScan({"com.smiler","com.example"}) //指定要扫描的包
```
如果采用这种方式来完成自动配置，进行项目开发时，如果需要引入大量的第三方依赖，就需要在启动类上配置非常多要扫描的包，这种方式会很繁琐。而且这种大面积的扫描性能也比较低
缺点：
1. 使用繁琐
2. 性能低
结论：SpringBoot中并没有采用以上这种方案

##### 解决方案2--@Import导入
导入形式主要有以下几种：
- 导入普通类
```
@Import(TokenParser.class) //导入的类会被Spring加载到IOC容器中
```
- 导入配置类
```
@Import(HeaderConfig.class) //导入配置类
```
- 导入ImportSelector接口实现类
```
@Import(MyImportSelector.class) //导入ImportSelector接口实现类
需要在ImportSelector接口实现类的字符串数组中类的全限定名称
```
缺点：当要引入一个第三方依赖时，需要知道第三方依赖中有哪些配置类和哪些Bean对象

##### 解决方案3
- 不用指定要导入哪些bean对象和配置类，让第三方依赖来指定
- 比较常见的方案就是第三方依赖提供一个注解，这个注解一般都以@EnableXxxx开头的注解，注解中封装的就是@Import注解
- 在使用时只需在启动类上加上@EnableXxxxx注解即可

这种方式会更方便更优雅，而这种方式也是SpringBoot当中所采用的方式


#### 源码跟踪
##### 源码跟踪技巧
在跟踪框架源码的时候，一定要抓住关键点，找到核心流程。一定不要从头到尾一行代码去看，一个方法的去研究，一定要找到关键流程，抓住关键点，先在宏观上对整个流程或者整个原理有一个认识，有精力再去研究其中的细节

##### 核心注解@SpringBootApplication
要搞清楚SpringBoot的自动配置原理，要从SpringBoot启动类上使用的核心注解@SpringBootApplication开始分析

在@SpringBootApplication注解中包含了：
###### 元注解
###### @SpringBootConfiguration
- @SpringBootConfiguration注解上使用了@Configuration，表明SpringBoot启动类就是一个配置类
- @Indexed注解，是用来加速应用启动的
###### @EnableAutoConfiguration
自动配置核心注解
- 使用`@Import`注解，导入了实现`ImportSelector`接口的实现类
- `AutoConfigurationImportSelector`类是`ImportSelector`接口的实现类
- `AutoConfigurationImportSelector`类中重写了`ImportSelector`接口的`selectImports()`方法
- `selectImports()`方法底层调用`getAutoConfigurationEntry()`方法，获取可自动配置的配置类信息集合
- `getAutoConfigurationEntry()`方法通过调用
  ```getCandidateConfigurations(annotationMetadata, attributes)```方法获取在配置文件中配置的所有自动配置类的集合
- `getCandidateConfigurations`方法的功能是获取所有基于`META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports`文件、`META-INF/spring.factories`文件中配置类的集合
- 通常在引入的起步依赖中，都有包含`META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports`文件和`META-INF/spring.factories`文件这两个文件

##### ComponentScan
- @ComponentScan注解是用来进行组件扫描的，扫描启动类所在的包及其子包下所有被
- @Component及其衍生注解声明的类。
SpringBoot启动类，之所以具备扫描包功能，就是因为包含了@ComponentScan注解

- 在配置类中定义一个@Bean标识的方法，而Spring会自动调用配置类中使用@Bean标识的方法，并把方法的返回值注册到IOC容器中

###### 自动配置的原理
自动配置原理源码入口就是@SpringBootApplication注解，在这个注解中封装了3个注解，分别是：
- @SpringBootConfiguration
声明当前类是一个配置类
- ComponentScan
进行组件扫描（SpringBoot中默认扫描的是启动类所在的当前包及其子包）
- @EnableAutoConfiguration
封装了@Import注解（Import注解中指定了一个ImportSelector接口的实现类）
在实现类重写的selectImports()方法，读取当前项目下所有依赖jar包中```META INF/spring.factories、META INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports``` 两个文件里面定义的配置类（配置类中定义了@Bean注解标识的方法）

当SpringBoot程序启动时，就会加载配置文件当中所定义的配置类，并将这些配置类信息(类的全限定名)封装到String类型的数组中，最终通过@Import注解将这些配置类全部加载到Spring的IOC容器中，交给IOC容器管理

*Q: 在 ```META INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports``` 文件中定义的配置类非常多，而且每个配置类中又可以定义很多的bean，那这些bean都会注册到Spring的IOC容器中吗？*
*A: 并不是。 在声明bean对象时，上面有加一个以@Conditional开头的注解，这种注解的作用就是按照条件进行装配，只有满足条件之后，才会将bean注册到Spring的IOC容器中*

##### @Conditional注解
在自动配置类声明bean的时候，除了在方法上加了一个@Bean注解以外，还会经常用到一个注解，就是以Conditional开头的这一类的注解。以Conditional开头的这些注解都是条件装配的注解
###### 作用
按照一定的条件进行判断，在满足给定条件后才会注册对应的bean对象到Spring的IOC容器中
###### 位置
方法、类
###### @Conditional本身是一个父注解，派生出大量的子注解
- @ConditionalOnClass
判断环境中有对应字节码文件，才注册bean到IOC容器
语法：
```
@ConditionalOnClass({Gson.class}) //当前SpringBoot环境中有Gson.class文件时，才会创建当前配置类对象
```
- @ConditionalOnMissingBean
判断环境中没有对应的bean(类型或名称)，才注册bean到IOC容器
语法：
```
@ConditionalOnMissingBean //当前GsonBuilder对象不存在时，创建该对象并注册到IOC容器中
```
- @ConditionalOnProperty
判断配置文件中有对应属性和值，才注册bean到IOC容器
语法：
```
@ConditionalOnProperty(name ="name",havingValue = "itheima")//配置文件中存在指定属性名与值，才会将bean加入IOC容器
```
###### 自动配置的核心
自动配置的核心就在@SpringBootApplication注解上，SpringBootApplication这个注解底层包含了3个注解，分别是：
- @SpringBootConfiguration
- @ComponentScan
- @EnableAutoConfiguration

###### @EnableAutoConfiguration
@EnableAutoConfiguration这个注解是自动配置的核心
- 它封装了一个@Import注解，Import注解里面指定了一个ImportSelector接口的实现类
- 在这个实现类中，重写了ImportSelector接口中的selectImports()方法
- 而selectImports()方法中会去读取两份配置文件，并将配置文件中定义的配置类做为selectImports()方法的返回值返回，返回值代表的就是需要将哪些类交给Spring的IOC容器进行管理
- 那么所有自动配置类的中声明的bean都会加载到Spring的IOC容器中吗? 其实并不会，因为这些配置类中在声明bean时，通常都会添加@Conditional开头的注解，这个注解就是进行条件装配。而Spring会根据Conditional注解有选择性的进行bean的创建
- @Enable 开头的注解底层，它就封装了一个注解 import 注解，它里面指定了一个类，是ImportSelector 接口的实现类。在实现类当中，我们需要去实现 ImportSelector 接口当中的一个方法 selectImports 这个方法。这个方法的返回值代表的就是程序员需要将哪些类交给 spring 的 IOC容器进行管理
- 此时它会去读取两份配置文件，一份是 spring.factories，另外一份是autoConfiguration.imports。而在 autoConfiguration.imports 这份文件当中，它就会去配置大量的自动配置的类
- 所有的自动配置类当中，所有的 bean并不会都会加载到 spring 的IOC 容器当中，因为这些配置类当中，在声明 bean 的时候，通常会加上@Conditional 开头的注解。这个注解就是进行条件装配。所以SpringBoot非常智能，它会根据 @Conditional 注解来进行条件装配。只有条件成立，它才会声明这个bean，才会将这个 bean 交给 IOC 容器管理


## Maven高级
### 分模块设计与开发
#### 概念
分模块设计，就是在设计 Java 项目的时候，将项目拆分成多个模块进行开发

##### 未分模块设计的问题
如果项目不分模块，所有的业务代码都写在一个 Java 项目当中。随着这个项目的业务扩张，项目当中的业务功能可能会越来越多
- 不方便项目的维护和管理
- 项目中的通用组件难以复用

##### 分模块设计
- 在进行项目设计阶段，就可以将一个大的项目拆分成若干个模块，每一个模块都是独立的
- 分模块设计就是将项目按照功能/结构拆分成若干个子模块，方便项目的管理维护、拓展，也方便模块键的相互调用、资源共享

**注意：分模块开发需要先针对模块功能进行设计，再进行编码。不会先将工程开发完毕后再进行拆分**

### 继承与聚合
如果是做大型项目，模块当中重复的依赖可能会很多很多。如果每一个 Maven 模块里，都单独的配置一次，功能虽然能实现，但是配置是比较繁琐的
#### 继承
##### 概念
继承描述的是两个工程间的关系，与java中的继承相似，子工程可以继承父工程中的配置信息，常见于依赖关系的继承。
##### 作用
简化依赖配置、统一管理依赖
##### 语法
```
<parent>
    <groupId>...</groupId>
    <artifactId>...</artifactId>
    <version>...</version>
    <relativePath>....</relativePath>
</parent>
```
##### 实现
- Maven中不支持多继承，但是支持多层继承
- 可以创建一个父工程，例如：tlias-parent，让父工程继承默认的根父工程spring-boot-starter-parent，其他子工程继承父工程，父工程打包方式需要设为pom
##### 代码
###### 父工程的pom.xml文件配置
```
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.7.5</version>
    <relativePath/> <!-- lookup parent from repository -->
</parent>
<groupId>com.smiler</groupId>
<artifactId>tlias-parent</artifactId>
<version>1.0-SNAPSHOT</version>
<packaging>pom</packaging>
```

*Maven打包方式：*
- *jar：普通模块打包，springboot项目基本都是jar包（内嵌tomcat运行）*
- *war：普通web程序打包，需要部署在外部的tomcat服务器中运行*
- *pom：父工程或聚合工程，该模块不写代码，仅进行依赖管理*

###### 子工程的pom.xml文件中，配置继承关系
```
<parent>
   <groupId>com.smiler</groupId>
   <artifactId>tlias-parent</artifactId>
   <version>1.0-SNAPSHOT</version>
   <relativePath>../tlias-parent/pom.xml</relativePath>
</parent>
<artifactId>tlias-utils</artifactId>
<version>1.0-SNAPSHOT</version>
```
注意事项
- 在子工程中，配置了继承关系之后，坐标中的groupId是可以省略的，因为会自动继承父工程的groupId
- relativePath指定父工程的pom文件的相对位置（如果不指定，将从本地仓库/远程仓库查找该工程）
-  ```../``` 代表的上一级目录


###### 在父工程中配置各个工程共有的依赖，子工程会自动继承父工程的依赖

在真实的企业开发中，都是先设计好模块之后，再开始创建模块，开发项目。一般都会先创建父工程 tlias-parent，然后将创建的各个子模块，都放在父工程parent下面。 这样层级结构会更加清晰一些

#### 版本锁定
##### 场景
- 如果项目中各个模块中都公共的这部分依赖，可以直接定义在父工程中，从而简化子工程的配置。然而在项目开发中，还有一部分依赖，并不是各个模块都共有的，可能只是其中的一小部分模块中使用到了这个依赖
- 例如：在tlias-web-management、tlias-web-system、tlias-web-report这三个子工程中，都使用到了jwt的依赖。 但是 tlias-pojo、tlias-utils中并不需要这个依赖，那此时，这个依赖不会直接配置在父工程 tlias-parent中，而是哪个模块需要，就在哪个模块中配置
- 一个项目中的多个模块，要使用的同一个依赖的版本要一致，这样便于项目依赖的统一管理

如果项目拆分的模块比较多，每一次更换版本，都需要找到这个项目中的每一个模块，一个一个的更改。 很容易会出现，遗漏掉一个模块，忘记更换版本的情况
解决这个问题，统一管理各个依赖的版本需要用到Maven的版本锁定功能

##### 使用
在maven中，可以在父工程的pom文件中通过 ```<dependencyManagement>``` 来统一管理依赖版本
- 在父工程中所配置的 ```<dependencyManagement>``` 只能统一管理依赖版本，并不会将这个依赖直接引入进来。 这点和 ```<dependencies>``` 是不同的
- 子工程要使用这个依赖，还是需要引入的，只是此时就无需指定 ```<version>``` 版本号了，父工程统一管理。变更依赖版本，只需在父工程中统一变更

*在springboot项目中，很多时候引入依赖坐标，都不需要指定依赖的版本```<version>``` ，是因为在父工程 ```spring-boot-starter-parent``` 中已经通过```<dependencyManagement>``` 对依赖的版本进行了统一的管理维护*

##### 属性配置
可以通过自定义属性及属性引用的形式，在父工程中将依赖的版本号进行集中管理维护
###### 语法
- 自定义属性
```
<properties>
     <lombok.version>1.18.24</lombok.version>
</properties>
```
- 引用属性
```
<dependency>
     <groupId>org.projectlombok</groupId>
     <artifactId>lombok</artifactId>
     <version>${lombok.version}</version>
</dependency>
```
版本集中管理之后，要想修改依赖的版本，就只需要在父工程中自定义属性的位置，修改对应的属性值即可

*面试题： ```<dependencyManagement>``` 与 ```<dependencies>``` 的区别是什么?*
- *```<dependencies>``` 是直接依赖，在父工程配置了依赖，子工程会直接继承下来*
- *```<dependencyManagement>``` 是统一管理依赖版本，不会直接依赖，还需要在子工程中引入所需依赖(无需指定版本)*

#### 聚合
分模块设计与开发之后，项目被拆分为多个模块，而模块之间的关系，可能错综复杂
##### 概念
###### 聚合
将多个模块组织成一个整体，同时进行项目的构建
###### 聚合工程
一个不具有业务功能的“空”工程（有且仅有一个pom文件） 【一般来说，继承关系中的父工程与聚合关系中的聚合工程是同一个】
##### 作用
快速构建项目（无需根据依赖关系手动构建，直接在聚合工程上构建即可）
##### 实现
在maven中，可以在聚合工程中通过 ```<moudules>``` 设置当前聚合工程所包含的子模块的名称

例如：
```
<!--聚合其他模块-->
<modules>
    <module>../tlias-pojo</module>
    <module>../tlias-utils</module>
    <module>../tlias-web-management</module>
</modules>
```
此时，进行编译、打包、安装操作，就无需在每一个模块上操作了。只需要在聚合工程上统一进行操作


#### 继承与聚合对比
##### 作用
- 聚合用于快速构建项目
- 继承用于简化依赖配置、统一管理依赖
##### 相同点
- 聚合与继承的pom.xml文件打包方式均为pom，通常将两种关系制作到同一个pom文件中
- 聚合与继承均属于设计型模块，并无实际的模块内容
##### 不同点
- 聚合是在聚合工程中配置关系，聚合可以感知到参与聚合的模块有哪些
- 继承是在子模块中配置关系，父模块无法感知哪些子模块继承了自己

### 私服
多模块开发的时候，拆分的模块是可以在同一个公司各个项目组之间进行资源共享的。这个模块的资源共享，就需要通过 Maven 的私服来实现
#### 概念
##### 私服
是一种特殊的远程仓库，它是架设在局域网内的仓库服务，用来代理位于外部的中央仓库，用于解决团队内部的资源共享与资源同步问题
##### 依赖查找顺序
- 本地仓库
- 私服仓库
- 中央仓库
##### 注意事项
私服在企业项目开发中，一个项目/公司，只需要一台即可（无需我们自己搭建，会使用即可）
#### 资源上传与下载
##### 配置
资源上传与下载，我们需要做三步配置，执行一条指令
- 第一步配置
在maven的配置文件中配置访问私服的用户名、密码
- 第二步配置
在maven的配置文件中配置连接私服的地址(url地址)
- 第三步配置
在项目的pom.xml文件中配置上传资源的位置(url地址)

配置好了上述三步之后，要上传资源到私服仓库，就执行执行maven生命周期：deploy

##### 私服仓库说明
###### RELEASE
存储自己开发的RELEASE发布版本的资源
###### SNAPSHOT
存储自己开发的SNAPSHOT发布版本的资源
###### Central
存储的是从中央仓库下载下来的依赖

##### 项目版本说明
###### RELEASE(发布版本)
功能趋于稳定、当前更新停止，可以用于发行的版本，存储在私服中的RELEASE仓库中
###### SNAPSHOT(快照版本)
功能不稳定、尚处于开发中的版本，即快照版本，存储在私服的SNAPSHOT仓库中


# 商业项目开发
## 软件开发
### 软件开发
#### 软件开发流程
##### 需求分析
完成需求规格说明书、产品原型编写
###### 需求规格说明书
一般来说就是使用 Word 文档来描述当前项目的各个组成部分，如：系统定义、应用环境、功能规格、性能需求等，都会在文档中描述
###### 产品原型
一般是通过网页(html)的形式展示当前的页面展示什么样的数据, 页面的布局是什么样子的，点击某个菜单，打开什么页面，点击某个按钮，出现什么效果，都可以通过产品原型看到
##### 设计
设计的内容包含 UI设计、数据库设计、接口设计
###### UI设计
用户界面的设计，主要设计项目的页面效果，小到一个按钮，大到一个页面布局，还有人机交互逻辑的体现
###### 数据库设计
需要设计当前项目中涉及到哪些数据库，每一个数据库里面包含哪些表，这些表结构之间的关系是什么样的，表结构中包含哪些字段
###### 接口设计
通过分析原型图，首先，粗粒度地分析每个页面有多少接口，然后，再细粒度地分析每个接口的传入参数，返回值参数，同时明确接口路径及请求方式
##### 编码
编写项目代码、并完成单元测试
###### 项目代码编写
软件开发工程师需要对项目的模块功能分析后，进行编码实现
###### 单元测试
编码实现完毕后，进行单元测试，单元测试通过后再进入到下一阶段
##### 测试
主要由测试人员, 对部署在测试环境的项目进行功能测试, 并出具测试报告
##### 上线运维
在项目上线之前， 会由运维人员准备服务器上的软件环境安装、配置， 配置完毕后， 再将开发好的项目，部署在服务器上运行

#### 角色分工
##### 项目经理
全阶段，对整个项目负责，任务分配、把控进度
##### 产品经理
需求分析，进行需求调研，输出需求调研文档、产品原型等
##### UI设计师
设计，根据产品原型输出界面效果图
##### 架构师
设计，项目整体架构设计、技术选型等
##### 开发工程师
编码，功能代码实现
##### 测试工程师
测试，编写测试用例，输出测试报告
##### 运维工程师
上线运维，软件环境搭建、项目上线

*在实际的项目中, 有一些项目组由于人员配置紧张, 可能并没有专门的架构师或测试人员, 这个时候可能需要有项目经理或者程序员兼任*

#### 软件环境
作为软件开发工程师，在编码的过程中就不可避免地会接触多种软件环境，在工作中经常遇到的三套环境， 分别是: 开发环境、测试环境、生产环境
##### 开发环境(development)
软件开发人员，在开发阶段使用的环境，就是开发环境，一般外部用户无法访问

例如，在开发中使用的MySQL数据库和其他的一些常用软件，可以安装在本地，也可以安装在一台专门的服务器中， 这些应用软件仅仅在软件开发过程中使用，项目测试、上线时，就不会再使用这套环境了，这个环境就是开发环境

##### 测试环境(testing)
当软件开发工程师，将项目的功能模块开发完毕，并且单元测试通过后，就需要将项目部署到测试服务器上，让测试人员对项目进行测试。那这台测试服务器就是专门给测试人员使用的环境，也就是测试环境，用于项目测试，一般外部用户无法访问

##### 生产环境(production)
当项目开发完毕，并且由测试人员测试通过之后，就可以上线项目，将项目部署到线上环境，并正式对外提供服务，这个线上环境也称之为生产环境

首先，会在开发环境中进行项目开发，往往开发环境大多数都是本地的电脑环境和局域网内的环境，当开发完毕后，然后会把项目部署到测试环境，测试环境一般是一台独立测试服务器的环境，项目测试通过后，最终把项目部署到生产环境，生产环境可以是机房或者云服务器等线上环境















