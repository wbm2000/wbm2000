# 一 B/S 软件的结构

javaSE 是  ==C/S 结构==  Client(客户端) Server(服务器)

==B/S==   Browser(浏览器)  Server(服务器)

![image-20220222133314476](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222133314476.png)





# 二 前端的开发流程

![image-20220222133954338](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222133954338.png)



# 三 网页的组成部分

页面由三部分内容组成 !

分别是内容(结构), 表现, 行为.

- 内容(结构), 是我吗在页面中可以看到的数据. 我吗称之为内容. 一般内容, 我们使用 html 技术来实现

- 表现, 指的是执行内容在页面上的展示形式. 比如说, 布局, 颜色, 大小等等, 一般使用CSS技术实现
- 行为, 指的是页面中元素与输入设备交互的响应, 一般使用 javaScript 技术实现



# 四 HTML 简介

==H==yper ==T==ext ==M==arkup ==L==anguage (超文本标记语言)  简写 HTML

HTML通过标签来标记要显示的网页中的各个部分. 页面文件本身是一种文本文件, 通过在文本文件中添加标记符, 可以告诉浏览器如何显示其中的内容 (如: 文字如何处理, 画面如何安排, 图片如何显示等)



# 五 创建 HTML 文件

1. 创建一个web 工程 (静态的web工程)

   ![image-20220222135809282](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222135809282.png)

   

2. 在工程下创建html页面

   ![image-20220222140309138](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222140309138.png)



3. 编写html

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>标题</title>
   </head>
   <body>
       hello
   </body>
   </html>
   ```

   

4. 选择浏览器运行页面

![image-20220222140552844](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222140552844.png)



5. 执行结果

   ![image-20220222140741532](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222140741532.png)

==注 : java 文件是需要编译, 再由 java 虚拟机跑起来, 但Html 文件它不需要编译, 直接由浏览器进行解析执行==



# 六 HTML 文件的书写规范 

```html
<!DOCTYPE html>   <!--约束, 声明这是一个html-->
<html lang="zh_CN">  <!--html 标签表示html的开始  lang="zh_CN"表示中文 html标签中一般分为两部分, 分别是 : head 和 boby-->
<head> <!--表示头部信息, 一般包含三部分内容, title标签, css样式, js脚本代码-->
    <meta charset="UTF-8">  <!--表示当前页面使用 utf-8字符集-->
    <title>标题</title>   <!--表示标题-->
</head>
<body>  <!--boby标签是整个html页面显示的主体内容--> </body>
</html>  <!--表示整个html页面的结束-->
```

==Html 的代码注释== : <!-- 这是html 注释, 可以页面右键源代码中看到 -->



# 七 HTML 标签介绍

1. 标签的格式 :

   ==<标签名> 封装的数据 </标签名>==

2. 标签名大小写不敏感

3. 标签拥有自己的属性

   - 分为基本属性 : ==bgcolor="red"==     可以修改简单的样式  ==bgcolor是毕竟颜色==

   在body标签写

   ![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222142947304.png)

   - 事件属 : ==onclick="alert('你好 !')"==

4. 标签又分为 , 单标签和双标签

   - 单标签格式  : ==<标签名/>==             br 换行  hr水平线
   - 双标签格式  :==<标签名> 封装的数据 </标签名>==

```html
<!DOCTYPE html>
<html lang="zh_CN">
<head>
    <meta charset="UTF-8">
    <title>标题</title>
</head>
<!--
    bgcolor是背景颜色属性
    onclick表示单击(点击)事件
    alert() 是javascript语言提供的一个警告框函数
    它可以接收任意参数, 参数就是警告框的函数信息
-->
<body bgcolor="red">
<button onclick="alert('wbm好帅')">按钮</button> <!-- 按钮标签 button-->
<h1>hello</h1>
</body>
</html>
```



注意 : ==html 代码不是很严谨, 有时候标签不闭合, 也不会报错==





# 八 常用标签介绍

## 8.1 font 字体标签

需求1 : 在网页上显示, 我是字体标签, 并修改字体为 宋体, 颜色为红色

```html
<!DOCTYPE html>
<html lang="zh_CN">
<head>
    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body >
 <!--需求1 : 在网页上显示, 我是字体标签, 并修改字体为 宋体, 颜色为红色
   font标签是字体标签, 它可以用来修改字体 颜色 大小(尺寸)
   color属性修改颜色 
   face属性修改字体
   size属性修改文字大小
 -->
 <font color="red" face="宋体" size="5">我是字体标题</font>
</body>
</html>
```

运行结果:

![image-20220222154204864](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222154204864.png)





## 8.2 特殊字符

需求2 : 把 < br>  换行标签 变成文本 转换成字符显示在页面上

```html
<!DOCTYPE html>
<html lang="zh_CN">
<head>
    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body >
      <!--需求2 : 把 < br>  换行标签 变成文本 转换成字符显示在页面上
          常用的特殊字符:
          < ====> &lt;
          > ====> &gt;
          空格 ===> &nbsp;
      -->
      我是换行标签<br> <!--按需求是应该在浏览器看到  我是换行标签<br>, 但是这样写的话<br>是换行标签-->
      我是&lt;br&gt;标签 <!--这样就变成了 我是<br>标签-->
      w &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      w
</body>
</html>
```

运行:

![image-20220222155309924](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222155309924.png)







## 8.3 标题标签

​    ==标题标签是h1到h6==

需求1 : 演示标题1 到标题6 

```html
<!DOCTYPE html>
<html lang="zh_CN">
<head>
    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body >
      <!--需求1 : 演示标题1 到标题6
      align 对齐函数
      left  左
      center 中
      right 右
      -->
    <h1 align="left">w</h1>
    <h2 align="center">w</h2>
    <h3 align="right">w</h3>
    <h4>w</h4>
    <h5>w</h5>
    <h6>w</h6>
</body>
</html>
```

运行:

![image-20220222160126879](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222160126879.png)







## 8.4 超链接 (重点)

在网页中所有点击之后可以跳转的内容都是==超链接==

需求1 : 普通的 超链接 

```html
<!DOCTYPE html>
<html lang="zh_CN">
<head>
    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body >
      <!--需求1 : 普通的 超链接
      href属性设置连接的地址
      target 属性设置目标进行跳转
             _self 表示跳转到当前页面 默认的效果
             _blank 表示打开新页面来进行跳转
      -->
   <a href="http://www.baidu.com">百度的链接</a>
   <a href="http://www.baidu.com" target="_self">百度的链接不跳窗口</a>
   <a href="http://www.baidu.com" target="_blank">百度的链接跳窗口</a>
</body>
</html>
```

运行:

![image-20220222170735220](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222170735220.png)

点击:

![image-20220222170753449](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222170753449.png)



## 8.5 列表标签

列表标签一般分为 3种

- 有序列表

- 无序列表 
- 定义列表(几乎不怎么用)

==需求1: 使用无序, 列表方式, 把 怪盗基德 工藤新一 折木奉太郎 比企谷八幡,展示出来==

```html
<!DOCTYPE html>
<html lang="zh_CN">
<head>
    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body >
      <!--需求1: 使用无序, 列表方式, 把 怪盗基德 工藤新一 折木奉太郎 比企谷八幡,展示出来
      <ul> <li></li>  </ul> 无序列表 里面可以有多个li列表
         type属性可以修改列表项前面的符号
      li 是列表项 
      -->
    <ul>
        <li>怪盗基德</li>
        <li>工藤新一</li>
        <li>折木奉太郎</li>
        <li>比企谷八幡</li>
    </ul>

       <!--有序列表 ol标签-->
     <ol>
         <li>怪盗基德</li>
         <li>工藤新一</li>
         <li>折木奉太郎</li>
         <li>比企谷八幡</li>
     </ol>

</body>
</html>
```

运行:

![image-20220222172756760](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222172756760.png)



## 8.6 img 标签 

img标签可以在html页面上显示图片.

==需求1 : 使用ing标签显示一张呆毛王的照片, 并修改宽高, 和边框属性==

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>img标签</title>
</head>
<body>
<!--
    需求1 : 使用ing标签显示一张呆毛王的照片, 并修改宽高, 和边框属性
    img标签是图片标签, 用来显示图片
      src属性可以设置图片的路径
      width属性设置属性的宽度
      height属性设置属性的高度
      border属性设置属性的边框
      alt属性当指定路径找不到图片时, 用来代替显示的文本内容

      在javaSE中路径也分为相对路径和绝对路径.
         相对路径 : 从工程名开始算
         绝对路径 : 从盘符开始算

      在web中路径分为相对路径和绝对路径 两种
            相对路径 :
               .       表示当前文件所在目录
               ..      表示 当前文件所在的目录的 上级目录
               文件名   表示当前文件所在目录的文件, 相当于 ./文件名  只不过是省略了./

            绝对路径 : 格式是: http://ip:port/工程名/资源路径

-->
    <!--可以设置多个图片-->
   <img src="../img/img.png" width="200" height="200" border="20">  <!--表示当前文件的上级目录,的img目录的 img.png 文件-->
   <img src="../img/img_1.png" width="200" height="200" border="30">
   <img src="../img/i55mg_1.png" width="200" height="400" border="10" alt="当前图片不存在">



</body>
</html>
```

运行:

![image-20220222175759169](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222175759169.png)



## 8.7 表格标签 (重点)

==需求1 : 做一个 带表头的, 三行, 三列的表格, 并显示边框
      需求2 : 修改表格的宽度, 高度的对齐方式, 单元格的间距==

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表格标签</title>
</head>
<body>
     <!--
      需求1 : 做一个 带表头的, 三行, 三列的表格, 并显示边框
      需求2 : 修改表格的宽度, 高度的对齐方式, 单元格的间距

      table 标签是表格标签
          border 设置表格边框
          width 设置表格宽度
          height 设置表格高度
          align 设置表格相当于页面的对齐方式
          cellspacing设置单元格间距

      tr 是行标签
      th 是表头标签
      td 是单元格标签
         align 设置单元格文本对齐方式
      b标签是加粗标签

     -->
   <table align="center"  border="2" width="300" height="300" cellspacing="0">
     <tr>
        <th>1.1</th>
        <th>1.2</th>
        <th>1.3</th>
     </tr>

     <tr>
       <td>2.1</td>
       <td>2.2</td>
       <td>2.3</td>
     </tr>

     <tr>
       <td>3.1</td>
       <td>3.2</td>
       <td>3.3</td>
     </tr>
   </table>

</body>
</html>
```

运行:

![image-20220222182512851](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222182512851.png)





## 8.8 跨行跨列表格 (次重点)

需求1: 新建一个五行, 五列的表格, 第一列的单元格要夸两列, 第二行第一列的单元格夸两行, 第四行第四列的单元行夸两行两列

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <!--需求1: 新建一个五行, 五列的表格,
              第一行,第一列的单元格要夸两列,
              第二行第一列的单元格夸两行,
              第四行第四列的单元行夸两行两列
            colspan 属性设置跨列
            rowspan 属性设置跨行

-->

     <table border="1" width="100" height="100" cellspacing="0">
         <tr>
             <td colspan="2">1</td>
             <td>3</td>
             <td>4</td>
             <td>5</td>
         </tr>

         <tr>
             <td rowspan="2">1.1</td>
             <td>1.2</td>
             <td>1.3</td>
             <td>1.4</td>
             <td>1.5</td>
         </tr>

         <tr>

             <td>2.2</td>
             <td>2.3</td>
             <td>2.4</td>
             <td>2.5</td>
         </tr>

         <tr>
             <td>3.1</td>
             <td>3.2</td>
             <td>3.3</td>
             <td rowspan="2" colspan="2">3.4</td>

         </tr>

         <tr>
             <td>4.1</td>
             <td>4.2</td>
             <td>4.3</td>
         </tr>
     </table>
</body>
</html>
```

运行:

![image-20220222190217745](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222190217745.png)



## 8.9 了解 iframe 框架标签 (内嵌窗口)

iframe 标签它可以在一个html页面上, 打开一个小窗口,去加载一个单独的页面.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>iframe</title>
</head>
<body>
    <!--iframe标签可以在页面上开辟一个小区域显示一个单独的页面
       iframe和a标签组合使用的步骤:
           1. 在iframe中使用name属性定义一个名称
           2. 在a标签的target属性上设置iframe的name的属性值
    -->
   我是一个单独的完整的页面<br/>
   <iframe name="wbm" src="2img标签.html" height="400" width="400"></iframe>
   <ul>
       <li><a href="1有序列表和无序.html" target="wbm">有序列表和无序</a></li>
       <li><a href="2img标签.html" target="wbm">img标签</a></li>
       <li><a href="3.表格标签.html" target="wbm">表格标签</a></li>
       <li><a href="http://yhdm04.com/acg/3569/1.html" target="wbm">高木同学</a></li>
   </ul>
</body>
</html>
```

运行:

![image-20220222204550929](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222204550929.png)



## 8.10 表单标签 (重点)

什么是表单?

表单就是html 页面中, 用来收集用户信息的所有元素集合, 然后把这些信息发送给服务器

需求1 : 创建一个个人信息注册的表单界面. 包含用户名, 密码, 确认密码. 性别(单选), 兴趣爱好(多选), 国籍(下拉框),隐藏域,自我评价(多行文本域) 重置, 提交

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单标签</title>
</head>
<body>
<!--需求1 : 创建一个个人信息注册的表单界面. 包含用户名, 密码, 确认密码. 性别(单选), 兴趣爱好(多选), 国籍(下拉框),隐藏域,自我评价(多行文本域)
 重置, 提交
 -->
<!--
  form标签就是表单
  input type="text" 是文本框    value 默认值
        type="password" 是密码框
        type="radio" 是单选框  name 属性可以对其进行分组  checked="checked"设置默认选择
        input type="checkbox" 是多选框
        <input type="reset"> 是重置键    reset:重置   value 属性可以修改默认值
        input type="submit"  是提交键    submit: 提交

  select 标签是下拉列表框
       option 标签是下拉列表框中的选项   selected="selected" 设置默认选中 如果没有它默认选中第一个

  textarea 标签表示多行文本输入框 (起始标签和结束标签中的内容是默认值)
        rows 属性设置可以显示几行的高度
        cols 属性设置每行可以显示几个字符宽度
<input type="button" value="按键"> 普通按钮 如果没有设置 value那就是空白的按键
<input type="file"> 这个是文件上传域
当我们要发送某些信息, 而这信息, 不需要用户参与, 就可以使用隐藏域 提交的时候同时发送给服务器
<input type="hidden" name="abc" value="abcValue">
-->
<form>
    <h3 align="center">用户注册</h3>
    <table align="center">
        <tr>
            <td>用户名称:</td>
            <td><input type="text" value="root"/></td>
        </tr>

        <tr>
            <td>用户密码:</td>
            <td><input type="password" value="123456"/></td>
        </tr>

        <tr>
            <td>确认密码:</td>
            <td><input type="password" value="123456"/></td>
        </tr>

        <tr>
            <td>性别:</td>
            <td><input type="radio" name="sex" checked="checked">男
                <input type="radio" name="sex">女
            </td>
        </tr>

        <tr>
            <td>兴趣:</td>
            <td><input type="checkbox">学习java
                <input type="checkbox">学习web
                <input type="checkbox">看动漫
            </td>
        </tr>

        <tr>
            <td>国籍:</td>
            <td><select>
                <option selected="selected">----请选择国籍----</option>
                <option>中国</option>
                <option>美国</option>
                <option>日本</option>
                <option>澳大利亚</option>
                <option>非洲</option>
            </select></td>
        </tr>

        <tr>
            <td>自我评价:</td>
            <td><textarea rows="10" cols="20">自我评价</textarea></td>
        </tr>

        <tr>
            <td><input type="reset"></td>
            <td align="center"><input type="submit"></td>
        </tr>

    </table>
</form>
</body>
</html>
```

运行:

![image-20220222215939450](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222215939450.png)

表单提交的细节

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单标签</title>
</head>
<body>
<!--
    form标签是表单标签
       action属性设置提交的服务器地址
       method属性设置提交的方式 GET(默认值)或POST

    表单提交的时候, 数据没有发送给服务器的三种情况
         1. 表单项没有name属性值
         2. 单选, 复选, (下拉框列表中的option标签) 都需要加上value属性
         3. 表单项不在提交的form标签中
         
      GET请求的特点是:
         1. 浏览器地址栏中的地址是: action属性[+?+请求参数]
             请求参数的格式是: name=value&name=value
         2. 不安全
         3. 它有数据长度的限制
         
         
      POST请求的特点是:
          1. 浏览器地址栏中只有action属性值
          2. 相对于GET请求要安全多
          3. 理论上没有数据长度的限制
-->
<form action="http://www.baidu.com" method="get">
    <input type="hidden" name="action" value="login">
    <h3 align="center">用户注册</h3>
    <table align="center">
        <tr>
            <td>用户名称:</td>
            <td><input type="text" name="name" value="root"/></td>
        </tr>

        <tr>
            <td>用户密码:</td>
            <td><input type="password" name="pwd" value="123456"/></td>
        </tr>

        <tr>
            <td>性别:</td>
            <td><input type="radio" name="sex" checked="checked" value="boy">男
                <input type="radio" name="sex" value="girl">女
            </td>
        </tr>

        <tr>
            <td>兴趣:</td>
            <td><input name="h" value="学习java" type="checkbox">学习java
                <input name="h" value="学习web" type="checkbox">学习web
                <input name="h" value="看动漫" type="checkbox">看动漫
            </td>
        </tr>

        <tr>
            <td>国籍:</td>
            <td><select name="country">
                <option value="null" selected="selected">----请选择国籍----</option>
                <option value="ch">中国</option>
                <option value="mg">美国</option>
                <option value="rb">日本</option>
                <option value="adly">澳大利亚</option>
                <option value="fz">非洲</option>
            </select></td>
        </tr>

        <tr>
            <td>自我评价:</td>
            <td><textarea rows="10" cols="20" name="zwpj">自我评价</textarea></td>
        </tr>

        <tr>
            <td><input type="reset"></td>
            <td align="center"><input type="submit"></td>
        </tr>

    </table>
</form>
</body>
</html>
```

运行:

![image-20220222232210966](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222232210966.png)

https://www.baidu.com/?action=login&name=root&pwd=123456&sex=boy&h=%E5%AD%A6%E4%B9%A0java&country=ch&zwpj=%E8%87%AA%E6%88%91%E8%AF%84%E4%BB%B7888 提交的表单因为转码问题,中文被转码了





## 8.11 其他标签

需求1: div span p标签的演示

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>其他标签</title>
</head>
<body>
     <!--需求1: div span p标签的演示
         div标签 默认独占一行
         span标签 特点长度是封账数据的长度
         p段落标签 默认会在段落的上方或下方空出一行来
     -->
     <div>div标签1</div>
     <div>div标签2</div>
     <span>span标签3</span>
     <span>span标签4</span>
     <p>p标签5</p>
     <p>p标签6</p>1
</body>
</html>
```

运行:

![image-20220222233218512](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222233218512.png)



HTML 最后的练习: 创建登录的表单,包含用户名, 密码框输入. 并结合table标签排版. 让他看上去整齐点

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
  <!--HTML 最后的练习: 创建登录的表单,包含用户名, 密码框输入. 并结合table标签排版. 让他看上去整齐点

-->
     <form action="http://www.baidu.com" method="get">
         <input type="hidden" name="ycy" value="ycy">
     <table align="center">   <!--表单居中-->
       <tr>
         <td>用户名:</td>
         <td><input type="text" name="name"></td>
       </tr>

       <tr>
         <td>登录密码:</td>
         <td><input type="password" name="pwd"></td>
       </tr>

       <tr>
         <td><input type="reset"></td><!--重置按钮-->
         <td align="center"><input type="submit"></td><!--提交按钮-->
       </tr>

     </table>
     </form>

</body>
</html>
```

运行:

![image-20220222234404623](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220222234404623.png)



# 9.CSS技术

## 9.1 CSS 技术介绍

CSS 是 [层叠样式表单] .是用于(增强)控制网页样式并允许将样式信息与网页内容分离的一种标记性语言



## 9.2. CSS 语法规则

**选择器**：浏览器根据==选择器==决定受 CSS 样式影响的HYML元素(标签)

**属性 (property)**:是你要改变的样式名, 并且每个属性都有一个值. 属性和值被冒号分开,并且由花括号包围, 这样就组成了一个完整的样式声明 (declaration) , 比如: p(color: blue)

**多个声明**: 如果要定义不止一个声明, 则需要用分号将每个声明分开, 最后一条声明的可以不加分号(但尽量在每条声明的末尾都加上分号)

**例如**:

 p{

  color:red;

  font-size:30px; 

}  意思是所有p标签的颜色变成red色, 文字大小为30px

==注:一般每行只描述一个属性==



CSS注释:  `/*注释内容*/`



## 9.3 CSS和HTML的结合方式

### 9.3.1 第一种

  在标签的style 属性上设置 "key: value value;", 修改标签样式

需求1: 分别定义两个 div , span标签, 分别修改每个 div 标签的样式为: 边框1个像素, 实线, 红色

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
  <!--需求1: 分别定义两个 div , span标签, 分别修改每个 div 标签的样式为: 边框1个像素, 实线, 红色-->
  <div style="color: red;border: 1px solid">第一个div标签</div>
  <div style="color: red;border: 1px solid">第二个div标签</div>
  <span>第一个span标签</span>
  <span>第二个span标签</span>

</body>
</html>
```

运行结果:

![image-20220223194653991](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220223194653991.png)



**问题: 这种方式的缺点 ?**

1. 如果标签多了, 样式多了, 代码量非常庞大
2. 可读性非常差
3. CSS代码没什么复用性可言



### 9.3.2 第二种

在head标签中, 使用style标签来定义自己需要的css样式

格式如下:

​     xxx{

​       Key : value value;...

​      }



需求1: 分组定义两个 div span 标签, 分别修改每个 div 标签的样式为 : 边框一个像素, 实线, 红色

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!-- style标签专门用来定义样式代码-->
    <style>
        div{ 
            color: red;
            border: red 1px solid;
        }
    </style>
</head>
<body>
  <!--需求1: 分别定义两个 div , span标签, 分别修改每个 div 标签的样式为: 边框1个像素, 实线, 红色-->
  <div>第一个div标签</div>
  <div>第二个div标签</div>
  <span>第一个span标签</span>
  <span>第二个span标签</span>

</body>
</html>
```

运行:

![image-20220223195658032](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220223195658032.png)



这种方法的缺点.

1. 只能在同一页面内复用代码, 不能在多个页面中复用css代码
2. 维护起来不方便, 实际的项目中会有成千上万的页面, 要到每个页面中去修改, 工作量太大了





### 9.3.3 第三种

把css样式写出一个单独的css文件, 在通过like标签导入 css样式文件, 这样可以实现复用

使用html的`<link rel="stylesheet" type="text/css" href="1.css">`标签 导入css样式文件.



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!--like标签专门用来引用css样式代码-->
  <link rel="stylesheet" type="text/css" href="1.css">
</head>
<body>
  <!--需求1: 分组定义两个 div span 标签, 分别修改每个 div 标签的样式为 : 边框一个像素, 实线, 红色-->
  <div>第一个div标签</div>
  <div>第二个div标签</div>
  <span>第一个span标签</span>
  <span>第二个span标签</span>
</body>
</html>
```



```css
div{
    color: red;
    border: red 1px solid;
}
```

运行:

![image-20220223200849795](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220223200849795.png)

## 9.4 css 选择器

### 9.4.1 标签名选择器

标签名选择器的格式是:

​       标签名{

​         属性: 值;

​     }

标签名选择器, 可以指定那些标签被动的使用这个样式



需求1: 在所有 biv 标签上修改字体颜色为蓝色, 字体大小30个像素,. 边框为1 像素 黄色实线. 并且修改所有span 标签的字体颜色为黄色, 字体大小20个像素, 边框为5像素蓝色虚线



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
  <link rel="stylesheet" type="text/css" href="css/2.css">
</head>
<body>
  <!--需求1: 在所有 biv 标签上修改字体颜色为蓝色, 字体大小30个像素,. 边框为1 像素 黄色实线. 并且修改所有span 标签的字体颜色为黄色, 字体大小20个像素,
      边框为5像素蓝色虚线-->
  <div>第一个div标签</div>
  <div>第二个div标签</div>
  <span>第一个span标签</span>
  <span>第二个span标签</span>
</body>
</html>
```



```css
/*需求1: 在所有 biv 标签上修改字体颜色为蓝色, 字体大小30个像素,. 边框为1 像素 黄色实线.
  并且修改所有span 标签的字体颜色为黄色, 字体大小20个像素, 边框为5像素蓝色虚线*/
div{
    color: blue;  /*字体蓝色*/
    font-size: 30px; /*字体 30像素*/
    border: yellow 1px solid; /*边框颜色为黄色  边框像素为1 实线*/
}
span{
    color: yellow;
    font-size: 20px;
    border: blue 5px dashed;
}
```



运行:

![image-20220223203312004](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220223203312004.png)

### 9.4.2 id 选择器

id 选择器的格式是:

`#id{`

   属性: 值

`}`

id 选择器. 可以让我们通过id属性选择性的去使用这个样式



​      需求1: 分别定义两个标签

​                第一个div 标签定义 id 为 id001 , 然后根据id 属性定义 css 样式修改字体颜色为蓝色, 字体大小 30 个像素.边框为1像素 黄色实线

​                第二个 div 标签定义 id 为 id002 , 然后根据id 属性定义 css 样式, 修改的字体颜色为红色, 字体大小 20 个像素, 边框为5 像素蓝色点线.



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
  <link rel="stylesheet" type="text/css" href="css/3.css">
</head>
<body>
  <!--
  第一个div 标签定义 id 为 id001 , 然后根据id 属性定义 css 样式修改字体颜色为蓝色, 字体大小 30 个像素.边框为1像素 黄色实线
  第二个 div 标签定义 id 为 id002 , 然后根据id 属性定义 css 样式, 修改的字体颜色为红色, 字体大小 20 个像素, 边框为5 像素蓝色点线.-->
  <div id="id001">第一个div标签</div>
  <div id="id002">第二个div标签</div>
</body>
</html>
```



```css
/*第一个div 标签定义 id 为 id001 , 然后根据id 属性定义 css 样式修改字体颜色为蓝色, 字体大小 30 个像素.边框为1像素 黄色实线
  第二个 div 标签定义 id 为 id002 , 然后根据id 属性定义 css 样式, 修改的字体颜色为红色, 字体大小 20 个像素, 边框为5 像素蓝色点线*/
#id001{
    color: blue;
    font-size: 30px;
    border: yellow 1px solid;
}

#id002{
    color: red;
    font-size: 20px;
    border: blue 5px dotted;
}
```

运行:

![image-20220223205033686](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220223205033686.png)



### 9.4.3 class选择器

class 类型选择器的格式是

​      .class{

​       属性 : 值

​       }

class类型选择器, 可以通过class属性有效的选择性地去使用这个样式



需求1: 修改 class 属性值 为 class01 的span  或 div, 标签, 字体为蓝色, 字体大小 30 个像素, 边框为 1 像素黄色实线

需求2: 修改 class 属性值 为 class02 的 div 标签, 字体颜色为灰色, 字体大小26个像素, 边框为 1 像素红色实线

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
  <link rel="stylesheet" type="text/css" href="css/4.css">
</head>
<body>
  <!--
  需求1: 修改 class 属性值 为 class01 的span  或 div, 标签, 字体为蓝色, 字体大小 30 个像素, 边框为 1 像素黄色实线
  需求2: 修改 class 属性值 为 class02 的 div 标签, 字体颜色为灰色, 字体大小26个像素, 边框为 1 像素红色实线-->
  <div class="class01">01 div标签</div>
  <span class="class01">01 span标签</span>
  <div class="class02">02 div标签</div>
</body>
</html>
```

```css
/*需求1: 修改 class 属性值 为 class01 的span  或 div, 标签, 字体为蓝色, 字体大小 30 个像素, 边框为 1 像素黄色实线
需求2: 修改 class 属性值 为 class02 的 div 标签, 字体颜色为灰色, 字体大小26个像素, 边框为 1 像素红色实线*/
.class01{
    color: blue;
    font-size: 30px;
    border: yellow 1px solid;
}

.class02{
    color: gray;
    font-size: 26px;
    border: red 1px solid;
}
```

运行:

![image-20220223214305724](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220223214305724.png)





### 9.4.4 组合选择器

  组合选择器的格式是:

  选择器1,选择器2,选择器3{

​        属性:值    

  }

 组合选择器可以让多个选择器共用一个css样式代码

需求1: 修改 class类型=class01 的div标签, 和id=id001 的span标签, 字体颜色为蓝色, 字体大小20个像素, 边框为 1像素黄色实线



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
  <link rel="stylesheet" type="text/css" href="css/5.css">
</head>
<body>
  <!--
  需求1: 修改 class类型=class01 的div标签, 和id=id001 的span标签, 字体颜色为蓝色, 字体大小20个像素, 边框为 1像素黄色实线
-->
  <div class="class01">class div</div>
  <span id="id001">id div</span>
</body>
</html>
```

 

```css
/*需求1: 修改 class类型=class01 的div标签, 和id=id001 的span标签, 字体颜色为蓝色, 字体大小20个像素, 边框为 1像素黄色实线
*/
.class01,#id001{
    color: blue;
    font-size: 20px;
    border: yellow 1px solid;
}
```

运行:

![image-20220223215419079](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220223215419079.png)



## 9.5 常用样式

1. 颜色

   ==color: red;==

   颜色可以写其他颜色如: black blue red green 等

   颜色也可以写 rgb 值和十六进制表示值, 如rgb(255,0,0), #00f6de, 如果写十六进制必须加 #

2. 宽度

   ==width: 19px==

   宽度可以写像素值: 19px;

   也可以写百分百值: 20%;

3. 高度

   ==height:20px;==

   宽度可以写像素值: 19px;

   也可以写百分百值: 20%;

4. 背景颜色

   ==background-color:red==

5. 字体样式

   ==color:red;  字体颜色红色==

   ==font-size: 20px; 字体大小==

6. 红色1像素实线边框

   ==border: 1px solid red==

7. DV居中

   ==margin-left: auto==

   ==margin-right: auto==















































































































































































































































































































