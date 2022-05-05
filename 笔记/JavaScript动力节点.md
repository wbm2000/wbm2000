

# `ECMAScript`篇

## 1 . 什么是JavaScript, 有什么用 ?

JavaScript是运行在浏览器上的脚本语言. 简称`JS` , `js`是网景公司 (`NetScape`) 的  布兰登艾奇(==JavaScript之父==)开发的, 最初叫做`LiveScript`,`LiveScript`的出现让浏览器更加生动了, 不再是单纯的静态页面了. 页面更具有交互性.

在历史的某个阶段, sun公司和网景公司他们之间有合作关系, sun公司吧`LiveScript`的名字改为JavaScript, `JavaScript`这个名字中虽然带有`java`但是和`java`没有任何关系, 只是语法上有点类似. 他们运行的位置不同

Java运行在`JVM`当中, JavaScript运行在浏览器的内存当中

JavaScript程序不需要程序员手动编译, 编译完源代码之后, 浏览器直接打开解释执行

JavaScript的`目标程序`以普通文本形式保存, 这种语言都叫做`脚本语言`

网景公司1998被美国`在线`收购

网景公司最著名的就是领航者浏览器 : Navigation浏览器量身定制一门语言, 不支持其他浏览器

当Navigation浏览器使用非常广泛的时候, 微软害怕了, 于是微软在最短的时间组建了一个团队, 开始研发只支持IE浏览器的脚本语言, 叫做`JScript`

JavaScript和`JScript`并存的年代, 程序员是很痛苦的, 因为程序员要写两套查询, 在这种情况下, 有一个非营利性组织站出来了, 叫做`ECMA`(欧洲计算机协会)组织, `ECMA`根据JavaScript定制了 `ECMA-262`号标准, 叫做`ECNA-Script`

现代的JavaScript 和 `JScript `都实现了`ECMA-Script`规范. (JavaScript和`JScript`统一了)

以后会学习一个叫做`JSP`的技术, `JSP`和`JS`有什么区别?

​    `JSP` : JavaScript Pages (隶属于Java语言的, 运行在`JVM`当中)

​    `JS`   :  JavaScript (运行在浏览器上. )



## 2 . 在HTML中怎么嵌入JavaScript代码 ?(三种方法)

### 第一种方法 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML中嵌入JavaScript代码 第一种方法.</title>

</head>
<body>
     <!--
        1. 实现的功能 :
            用户点击以下按钮, 弹出信息框

        2. JS 是一门事件驱动性的编程语言, 依靠事件去驱动, 然后执行对应的程序, 在JS中有很多事件, 其中有一个事件叫做,
           鼠标单击事件, 单词: click. 并且任何事件都会对应一个事件句柄叫做: onclick. [注意: 事件和事件句柄的区别
           是事件句柄是在事件单词前添加一个 on], 而事件句柄是以HTML标签的属性存在的

        3. onclick="js代码", 执行原理是什么?
           页面打开的时候, js代码并不会执行, 只是把这段JS代码注册到按钮的onclick事件上了
           等这个按钮方式点击(click)事件之后, 注册在onclick后面的js代码会被浏览器自动调用

        4. 怎么使用js代码弹出消息框
           在js中有一个内置的对象叫做window, 可以直接拿来使用, window代表的是浏览器对象
           window对象有一个函数叫做:alert, 用法是: window.alert("消息"),这样就可以弹窗了

        5. JS中的字符串可以使用双引号, 也可以使用单引号

        6. JS中的一条语句之后可以使用分号";", 也可以不用
     -->
     <input type="button" value="hello" onclick="window.alert('Hello Word')"><!--外面单引号,里面要双引号-->
     <input type="button" value="hello" onclick='window.alert("Hello Word")'><!--外面双引号,里面要单引号-->
     <!--一个点击事件可以放多个弹窗-->
     <input type="button" value="hello" onclick='window.alert("Hello Word")
                                                 window.alert("Hello wbm")
                                                 window.alert("Hello 555")'>

     <!--window可以省略-->
     <input type="button" value="hello" onclick='alert("Hello Word")'>

</body>
</html>
```

运行:

![image-20220314230305283](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220314230305283.png)







### 第二种

```html
<script type="text/javascript">
    alert("www2")   // 可以出现在任何地方
    // js的注释和java一样
    //这是单行注释
    /*这是多行注释*/
</script>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML中嵌入JavaScript代码 第二种方法</title>
</head>
<body>
      <input type="button" value="我是一个按钮">
       <!--
           JavaScript的脚本块在一个页面当中可以出现多次, 没有要求
           JavaScript的脚本块出现位置也没有要求, 随意
       -->
        <!--第二种方式: 脚本块的方式-->
        <script type="text/javascript">
          /**
           * 暴露在脚本块中的程序, 在页面打开的时候执行
           * 并且遵守自上而下的顺序逐行执行. (这个代码块执行不需要事件)
           */
          window.alert('Hello Word') // alert函数会阻塞整个HTML页面的加载,会阻挡当前页面加载的作用, 直到用户点击确定按钮
          window.alert('Hello JavaScript')
        </script>

        <input type="button" value="我是一个按钮">
</body>
</html>
<script type="text/javascript">
    alert("www")
</script>
```



### 第三种方式

定义一个`js`文件, 然后导入到HTML中

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML中嵌入JavaScript代码 第三种方法</title>
    <!--在需要的位置引入js脚本文件
        引入外部独立的js文件的时候, js文件中的代码会遵守自上而下的顺序依次执行
        注入结束的script必须有 
    -->
    <script type="text/javascript" src="js/003.js">
        /*这里写的代码不会被执行*/
        alert("aaa")
    </script>
    
    <!--同一个js文件可以被引入多次, 但在实际开发这种需求很少-->
    <!--<script type="text/javascript" src="js/003.js"></script>-->
    
    <!--导入js文件后, 这里还是可以写其他的脚本块的-->
    <script type="text/javascript">
        alert("www")
    </script>    
</head>
<body>

</body>
</html>
```

```javascript
alert("hello word")
alert("hello wbm")
alert("hello 520")
```





## 3 . 变量

### 变量的声明与赋值

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>关于js中的变量</title>
</head>
<body>
        <script type="text/javascript">
            /**
             * 回顾java中的变量:
             *      1. java中怎么定义/声明变量
             *         数据类型 变量名;
             *         例如:
             *              int i;
             *              double d;
             *              boolean flag;
             *
             *      2. java中的变量怎么赋值
             *         使用'='运算符进行赋值运算. ('=' 运算符右边先执行, 将右边执行的结果赋值给左边的变量)
             *         变量名=值;
             *         例如:
             *             i=10;
             *             d=3.14;
             *             flag = false;
             *
             *      3. java语言是一种强类型语言, 强类型怎么理解?
             *         java语言在编译阶段, 假设有代码:  int i;
             *         那么在java中有一个特点是, java程序编译阶段就已经确定了
             *         i变量的数据类型, 该i变量的数据类型在编译阶段是int类型,
             *         那么这个变量到最终内存释放, 一直都是int类型, 不可能变成其他类型.
             *            int i =10;
             *            double d =i;
             *            这行代码是说声明一个新的变量d, double类型, 把i变量中保存的值传给d.
             *            i还是int类型, 在double中 正整数是true, 负整数是false
             *
             *            i="abc"; 这行代码编译的时候会报错, 因为i变量的数据类型是int类型, 不能将字符串赋值给i
             *
             *            java中要求变量声明的时候是什么类型, 以后永远都是这种类型,不可变. 编译期强行固定变量的数据类型
             *            称为强类型语言
             *
             * JavaScript当中的变量
             *        怎么声明变量?
             *            var 变量名;
             *        怎么给变量赋值?
             *            变量名 = 值;
             *        JavaScript是一种弱类型语言, 没有编译阶段, 一个变量可以随便赋值, 赋什么类型的值都行
             *             var i =100;
             *             i=false;
             *             i="abc";
             *             i= new Object();
             *             i=3.14;
             *
             *        重点 : JavaScript是一种弱类型编程语言
             *
             */
            // 在js当中, 当一个变量没有手动赋值的时候, 系统默认赋值undefined
            /*var i;
            alert("i="+ i)// i=undefined
            alert(undefined)
            var  k = undefined;
            alert("k="+k);*/

            // 一个变量没有声明/定义, 直接访问会是什么?
           // alert(age) // 语法错误  age is not defined

            var a, b, c=200; // 表示ab=undefined  c=200

            alert(a)
            alert(b)
            alert(c)

        </script>
</body>
</html>
```



### 函数的定义与调用

在`java`中函数叫方法

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS函数</title>
</head>
<body>
   <script type="text/javascript">
     /**
      * 1. js中的函数:
      *       等同于java语言中的方法, 函数也是一段可以被重复利用的代码片断
      *       函数一般都是可以完成某个特定功能的
      *
      * 2. 回顾java中的方法
      *       [修饰符列表] 返回值类型 方法名(形式参数列表){
      *           方法体;
      *       }
      *    例如:
      *     public static boolean login(String username, String password){
      *         ...
      *         return true;
      *     }
      *
      *    boolean loginSuccess = login("admin","123456")
      *
      *
      * 3. JS中的变量是一种弱类型的, 那么函数应该怎么定义呢?
      *     语法格式:
      *       第一种方式:
      *        function 函数名(形式参数列表){
      *             函数体;
      *        }
      *
      *       第二种方式:
      *         函数名 = function(形式参数列表){
      *                       函数体
      *                 }
      */
      function sum(a,b) {
         // a和b都是局部变量, 他们都是形参(a和b都是变量名, 变量名随意)
         alert(a+b);
      }

      // 函数必须调用才能执行的
     // sum(10,10);

      // 定义函数sayHello
       sayHello = function (a){
         alert(a);
       }

       // 调用sayHello方法
       // sayHello("hello word")
   </script>

   <input type="button" value="点击" onclick="sayHello('hello word')">

</body>
</html>
```



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>js函数</title>
</head>
<body>
      <script type="text/javascript" >
         /*
             java中的方法有重载机制, js中的函数能重载吗?
                js当中的函数在调用的时候, 参数的类型没有限制, 并且参数的个数也没有限制, js就是这么随意. (弱类型)

             重载的含义:
                方法名或者函数名一样, 形参不同(个数, 类型, 顺序)
                

          */
         function sum(a,b) {
            return a+b;
         }

         // 调用函数
         var sum1 = sum(5,5);
         alert(sum1);// 10

         sum1=sum("55");// 55赋值给a变量, b变量没有赋值系统默认赋值undefined  当两个变量其中一个变量不是数值型 +号就会变成拼接符 55undefined
         alert(sum1); // 55undefined

         sum1=sum();
         alert(sum1);// NAN (NAN是一个具体存在的值, 该值表示表示数字, Not a Number)

         sum1=sum(5,5,2);
         alert(sum1) // 10

         // 在js当中, 函数的名字不能重名, 当函数重名的时候, 后声明的函数将之前的同名函数覆盖

         function f(username) {
             alert(username)
         }
         
         function f() {
             alert("f")
         }
         

         // 调用 
         f("wbm");//f 这个调用的是第二个f函数 


      </script>
</body>
</html>
```









### 全局变量和局部变量

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
   <script type="text/javascript">
     /*
         全局变量:
             在函数体之外声明的变量属于全局变量, 全局变量的声明周期是:
                  浏览器打开时声明, 浏览器关闭是销毁, 尽量少用, 因为全局变量会一直在浏览器的内存当中, 耗费内存空间.
                  能使用局部变量尽量使用局部变量
         局部变量:
             在函数体当中的变量, 包括一个函数的形参都属于局部变量
             局部变量的生命周期是, 函数开始执行时局部变量的内存空间开辟, 函数执行结束,局部变量的内存空间会释放
             局部变量生命周期较短
      */

     /*测试1*/
     //全局变量
     var i =100;
     function accessI() {
         // 访问的是全局变量
         alert("i="+i)
     }
     accessI();//100


     /*测试2*/
     //全局变量
     var username = "jack";
     function accessUsername() {
         //局部变量
         var username = "lisi";
         alert("username="+username); // 就近原则, 这里输出的是 局部变量
     }
     accessUsername();//lisi

     // 访问全局变量
     alert("username="+username);//jack 因为局部变量的生命周期在函数体中, 这里不在函数体内


     /*测试3*/
     function accessAge() {
         var age = 20;
         alert("年龄"+age);
     }
     accessAge();

     //alert("age"+age);//语法错误  age is not defined


     /*测试4*/
     function f() {
         // 当一个变量声明的时候没有使用var关键字, 那么不管这个变量是在哪里声明的,都是全局变量
         myname="wbm"
     }
     // 访问函数
     f();

     alert("myname="+myname)// myname=wbm

   </script>

</body>
</html>
```



## 4.  数据类型

### typeof运算符

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>js中的数据类型</title>
</head>
<body>
   <script type="text/javascript">
       /*
           1. 虽然js中的变量在声明的时候不需要指定数据类型, 但是在赋值, 每一个数据还是有类型的
                 js中的数据类型有: 原始类型, 引用类型
                 原始类型: Undefined, Number, String, Boolean, Null
                 引用类型: Object以及Object的子类

           2. ES规范(ECMAScript规范), 在ES6之后, 又基于以上的6种类型之外添加了一种新的类型, Symbol

           3. js中有一个运算符叫做typeof, 这个运算符可以在程序的运行阶段动态的获取变量的数据类型
              typeof运算符的语法格式
                   typeof 变量名;
              typeof运算符的运算结果是以下6个字符串之一, 注意字符串的都是全部小写
                   "undefined"
                   "number"
                   "string"
                   "boolean"
                   "object"
                   "function"
           4. 在js当中比较字符串是否相等使用"=="完成, 没有equals
        */

       // 求和, 要求a变量和b变量将来的数据类型必须是数字, 不能是其他类型
       // 因为以下定义的这个sum函数是为了完成两个数字的求和
      /* function sum(a,b) {
           if (typeof a == "number" && typeof b == "number") {
               return a+b;
           }
           alert(a+","+b+","+"必须都为数字!")
       }

       // 调用sum方法
       var sum1 = sum(false,"abc");
       alert(sum1)// false,abc,必须都为数字!  和 undefined

       var sum2 = sum(1,2);
       alert(sum2); // 3*/


       //  typeof运算符的运算结果
       var i;
       alert(typeof i) // undefined

       var k=10;
       alert(typeof k) // number

        k="abc";
       alert(typeof k) // string

        k=false;
       alert(typeof k) // boolean

        k=null;
       alert(typeof k) // object    null属于Null类型, 但是typeof运算符的结果是 object

        k=3.47;
       alert(typeof k) // number

        k=new Object();
       alert(typeof k) // object

        k=function () {

        }
       alert(typeof k) // function



   </script>

</body>
</html>
```



### Undefined类型

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Undefined类型</title>
</head>
<body>
     <script type="text/javascript">
       /*
          Undefined类型只有一个值, 这个值就是 undefined
          当一个变量没有手动赋值, 系统默认赋值undefined
          或者也可以手动给一个变量手动赋值undefined
        */
       var i;  // 系统默认赋值undefined
       var k=undefined; // 手动赋值undefined
       alert(i == k);// true

       var y="undefined"; // String类型
       alert(k==y) // false

     </script>

</body>
</html>
```





### Number类型

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Number类型</title>
</head>
<body>
     <script type="text/javascript">
       /*
          1. Number类型包括那些值 ?
             -1 0 1 3.14 10000 ... NaN Infinity(无穷)
             整数 小数 正数 负数 不是数字 无穷大都属于 Number类型

          2. isNaN() : 结果是true表示不是一个数字, 结果是false表示是一个数字

          3. parseInt()函数 可以将字符串转换成数字, 并且取整数位

          4. parseFloat()函数 可以将字符串自动转换成数字

          5. Math.ceil()函数 (Math是数学类, 数学类当中有一个函数叫做ceil(), 作用是向上取整)
        */

       var v = 1;
       alert(typeof v); // number

       v=3.14;
       alert(typeof v); // number

       v=-100;
       alert(typeof v); // number

       v=NaN;
       alert(typeof v); // number

       v=Infinity;
       alert(typeof v); // number

      /*
           关于NaN (表示Not a Number, 不是一个数字, 但属于Number类型)
           什么情况下结果是一个NaN呢?
           运算结果本来应该是一个数字, 最后算完不是一个数字的时候, 结果就是NaN
        */
       // 除号显然最后结果应该是一个数字, 但是运算的过程中导致最后不是一个数字, 那么最后的结果就是NaN
    var a = 100;
       var b = "中国人";
       alert(a / b);  // NaN

       // 加号 当两边里有一个是字符串类型, 那么加号就会当成 拼接的效果
       var c = "abc";
       var d =10;
       alert(c+d);// abc10

       // Infinity (当除数为0的时候, 结果为无穷大)
       alert(10 / 0); // Infinity

       // 思考, 在JS中 10 / 3 = ?
       alert(10 / 3); // 3.3333333333333335


       /*
          关于isNaN的函数
          用法: isNaN(数据), 结果是true表示不是个数字, 结果是false表示是一个数字
          isNaN : is Not a Number
       */
       function sum(a,b) {
         if (! isNaN(a) && ! isNaN(b)) { // 如果a和b是数字, 就返回两个数字的和
             return a + b;
         }
         alert(a+","+b+","+"其中有一个或者多个不是数字")
       }

       // 调用 sum 函数
       var sum1 = sum(1,"abc");
       alert(sum1); // 1,abc,其中有一个或者多个不是数字

       var sum2 = sum(1,2);
       alert(sum2) // 3


       // parseInt()函数 : 可以将字符串转换成数字, 并且取整数位
       alert( parseInt("3.9999"));
       alert(parseInt(3.9999));

       // parseFloat()函数, 可以将字符串自动转换成数字
       alert(parseFloat("11.11")); // 11.11

       // Math.ceil()函数
       alert(Math.ceil(3.14)); // 4

     </script>
</body>
</html>
```



### Boolean类型

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Boolean类型</title>
</head>
<body>
    <script type="text/javascript">
      /*
           1. js中的布尔玛类型永远都只有两个值, true和false (这一点和java相同)
           2. 在Boolean类型中有一个函数叫做, Boolean();
              语法格式:
                  Boolean(数据)
              Boolean()函数的作用是将非布尔类型转换成布尔类型

           3. Null类型只有一个值, null 它的 typeof类型是 object

       */
     /* var username="";

      if (Boolean(username)) {
        alert("欢迎你"+name)
      }else{
        alert("用户名不能为空!")
      }*/

      var username="";
      if (username) {// 就算不写它也会自动生成 boolean()
        alert("欢迎你"+name)
      }else{
        alert("用户名不能为空!")
      }


      // 规律: 有就转换成true, 没有就转换成false
      alert(Boolean(1));//true
      alert(Boolean(0));//false
      alert(Boolean("www")); // true
      alert(Boolean("")); // false

      alert(Boolean(undefined)); // false
      alert(Boolean(NaN)); // false
      alert(Boolean(null)); // false
      alert(Boolean(Infinity)); // true


      // while的作用跟java差不多, 只要为true就一直执行
      while (10 / 3){// 10 / 3 是有数的, 所以为true 这样的话就会无限循环
        //alert("hello")
      }

      // for循环也跟java差不多
      for (var i = 0; i <10 ; i++) {
          alert("i="+ i);
      }


    </script>
</body>
</html>
```



### String 类型

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>String类型</title>
</head>
<body>
     <script type="text/javascript">
          /*
             String类型:
                 1. 在js当中字符串可以使用单引号, 也可以使用双引号
                     var str1 = '123';
                     var str2 = "123";

                 2. 在js当中, 怎么创建字符串对象呢?
                    两种方式:
                        第一种: var s = "abc";
                        第二种(使用js内置的支持类String): var s2 = new String("abc);
                    需要注意的是: String是一个内置的类, 可以直接用, String的父类是Object

                 3. 无论小string还是大String, 他们的属性和函数都是通用的.

                 4. 关于String类型的常用属性和函数
                    常用属性:
                        length  获取字符串长度
                    常用函数:
                        indexOf     获取指定字符串在当前字符串中第一次出现处的索引
                        lastIndexOf  获取指定字符串在当前字符串中最后一次出现处的索引
                        replace   替换
                        substr   截取子字符串
                        substring  截取子字符串
                        toLowerCase 把字符串转换小写
                        toUpperCase 将字符串转换成大写
                        split 拆分字符串


           */


          // 小string(属于原始类型String)
         /* var x = "abc";
          alert(typeof x); // string

          // 大String(属于原始Object类型)
          var y = new String("abc");
          alert(typeof y); // object

          // 获取字符串的长度
          alert(x.length);// 3
          alert(y.length);// 3*/

          // indexOf    检索字符串
          alert("http//www.baidu.com".indexOf("http"))//0
          alert("http//www.baidu.com".indexOf("https"))// -1 因为不存在https

          // 判断一个字符串中是否包含某个子字符串?
          alert("http//www.baidu.com".indexOf("https")>= 0 ?"包含" : "不包含");// 不包含

          // replace 注意:只替换一个, 如果需要全部替换第一种方法就是写多个这种的方法替换到都替换为止
          // 想全部替换需要使用正则表达式
          alert("name=value%name=value%name=value%".replace("%",","));// name=value,name=value%name=value%
          alert("name=value%name=value%name=value%".replace("%",",").replace("%",","));// name=value,name=value,name=value%


          // 考点: 经常问, substr和substring的区别?
          //substr(startIndex(开始索引),length(长度))
          alert("wbmsygzno".substr(2,4)); // msyg
          //substring(startIndex(开始索引),endIndex(结束索引)): 注意: 不包含endIndex
          alert("wbmsygzno".substring(2,4));// ms



     </script>



</body>
</html>
```





### Object数据类型

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Object类型</title>
</head>
<body>
         <script type="text/javascript">
             /*
                      Object类型:
                           1. Object类型是所有类型的超类, 自定义的任何类型, 默认继承Object

                           2. Object类型包括那些属性
                                   prototype属性(常用的, 主要的是这个), 作用是给类动态的扩展属性和函数
                                   constructor属性

                           3. Object类包括那些函数
                                   toString()
                                   valueOf()
                                   toLocaleString()

                           4. 在JS当中定义的类默认继承Object, 会继承Object类中所有的属性以及函数
                              换句话说, 自己定义的类中也有prototype属性.

                           5. JS当中怎么定义类? 怎么new对象?
                                      定义类的语法:
                                         第一种方式:
                                             function 类名(形参){

                                             }
                                         第二种方式:
                                             类名 = function(形参){

                                             }
                                       创建对象的语法:
                                            new 构造方法名(实参); // 构造方法和类名一致
              */
             function sayHello() {

             }

             // 把sayHello当做一个普通的函数来调用
             sayHello();

             // 这种方法就表示把sayHello当成一个类来创建对象
             var obj = new sayHello();// obj是一个引用, 保存内存地址指向堆中的对像

             //定义一个学生类
             function Student(){
                 alert("Student......")
             }

             // 当做普通函数调用
             Student();

             // 当做类来创建对象
             var student = new Student();
             alert(student); // [object Object]

             // JS中的类的定义, 同时又是一个改造函数的定义
             // 在JS中类的定义和构造函数的定义是放在一起来完成的
             function User(a,b,c) { // abc 是形参, 属于局部变量
                 // 声明属性 (this表示当前对象)
                 // User类中有三个属性: sno  sname  sage
                 this.sno=a;
                 this.sname=b;
                 this.sage=c;
             }

             // 创建对象
             var u1 = new User(111,"张三",30);
             // 访问对象的属性
             alert(u1.sno); // 111
             alert(u1.sname); // 张三
             alert(u1.sage); // 30

             var u2 = new User(112,"wbm",301);
             // 访问对象的属性
             alert(u2.sno); // 112
             alert(u2.sname); // wbm
             alert(u2.sage); // 301

             // 访问一个对象的属性, 还可以使用这种语法
             alert(u2["sno"]); // 112
             alert(u2["sname"]); // wbm
             alert(u2["sage"]); // 301

             // 定义类的另一种语法
             Emp = function (ename,sal) { // 工资类
                 this.ename=ename; // 员工名字
                 this.sal=sal; // 工资
             }

             var emp = new Emp("wbm",800); // 创建工资类
             alert(emp.ename);// wbm
             alert(emp.sal); // 800


             Product = function (pno,pname,price) { // 产品类
                 // 属性
                 this.pno=pno; // 商品编号
                 this.pname=pname; // 商品名字
                 this.price=price; // 商品单价

                 // 函数
                 this.getPrice = function (){
                     return this.price; // 返回当前对象的price属性值
                 }
             }

             var product = new Product(111,"西瓜",12); // 赋值
             var price1 = product.getPrice(); // 调用getPrice方法
             alert(price1); // 12

             // 可以通过 prototype 这个属性来给类动态扩展属性以及函数
             Product.prototype.getPname= function () {
                 return this.pname;
             }

             // 调用后期扩展的getPname()函数
             var pname1 = product.getPname();
             alert(pname1); // 西瓜
             
             
             // 给String扩展一个函数
             String.prototype.suiyi=function () {
                  alert("这是给String类型扩展的一个函数, 叫做suiyi")
             }
             
             "abc".suiyi(); // 这是给String类型扩展的一个函数, 叫做suiyi
         </script>
</body>
</html>
<!--
    java语言怎么定义类, 怎么创建对象?  (强类型)
    public class User(){
      private String username;
      private String password;
      public user()
      public user(String username,String password){
           this.username = username;
           this.password = password;
      }
    }
    User user = new User();
    User user2 = new User("wbm",123456);
    
    
    JS语言怎么定义类, 怎么创建对象?  (弱类型)
     User = function(username,password){
         this.username = username;
         this.password = password;
     }
     // 相当于写了三个构造函数 一个无惨, 一个有参, 一个有一个参
     var user = new User();
     var user = new User("wbm");
     var user = new User("wbm",123456);

-->
```



### null `NaN` undefined 这三个值有什么区别 ?

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>null-NaN-undefined这三个值有什么区别.html</title>
</head>
<body>
   <script type="text/javascript">
       // == 是等同运算符
       alert(1 == true); //true
       // === 是全等运算符
       alert(1 === true); //false


       // 使用 typeof 判断这三个是什么数据类型
       // null NaN undefined 数据类型不一样
       alert(typeof null); // object
       alert(typ
             eof NaN); // number
       alert(typeof undefined); // undefined

       // null 和 undefined 可以等同
       alert(null == NaN); // false
       alert(null == undefined); // true
       alert(NaN == undefined); // false

       /*
         在JS当中有两个比较特殊的运算符
         ==(等同运算符,只判断值是否相等)
         ===(全同运算符, 既判断值是否相等, 又判断数据类型是否相等)
       */

       alert(null === NaN); // false
       alert(null === undefined); // false
       alert(NaN === undefined); // false
   </script>

</body>
</html>
```





## 5. `JS`中的事件

### `js`中常用事件

```javascript
JS中的事件:
// 有两个文本框 当第一个文本框, 跳到第二个文本框输入, 第一个文本框就叫失去焦点, 而第二个文本框就叫获得焦点
blur 失去焦点
focus 获得焦点

// 鼠标点击
click 鼠标单击
dblclick 鼠标双击

// 键盘相关
keydown 键盘按下
keyup 键盘弹起

// 鼠标相关的
mousedown 鼠标按下
mouseover 鼠标经过
mousemove 鼠标移动
mouseout 鼠标离开
mouseup 鼠标弹起

// 表单相关的
reset 表单重置
submit 表单提交

change 下拉框表选中项改变, 或文本框内容改变
load 页面加载完毕(整个HTML页面中的元素全部加载完毕之后发生)
select 文本被选定

任何一个事件都会对应一个事件句柄, 事件句柄是在事件前添加on.
onXXX整个事件句柄出现在一个标签的属性位置上. (事件句柄以属性的形式存在.)
```



### 第一种注册事件的方法之回调函数

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS的常用事件</title>
</head>
<body>
   <script type="text/javascript">
       // 对于当前查询来说, sayHello函数被称为回调函数(callback函数)
       // 回调函数的特点: 自己把这个函数代码写出来, 但是这个函数不是自己负责调用, 由其他程序负责调用该函数
       function sayHello() {
           alert("hello wbm!")
       }
   </script>
    <!--注册事件的第一种方式, 直接在标签中使用事件句柄-->
    <!--以下代码的含义是, 将sayHello函数注册到按钮上, 等待click事件发生之后, 该函数被浏览器调用, 我们称这个函数为回调函数-->
    <input type="button" value="hello" onclick="sayHello()">
</body>
</html>
```



### Java中的回调函数

```java
// java中也有回调函数机制
public class MyClass{

public static void main(String[] args){
   // 主动调用run方法, 站在这个角度看run方法叫做正向调用
}

  // 站在run方法的编写者角度来看这个方法, 把run方法叫做回调函数
  public void run(){
    System.out.println("run....");
  }
}
```



### 第二种注册事件方式, 是使用纯`JS`代码完成事件的注册

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS的常用事件</title>

</head>
<body>
   <input type="button" value="按钮" id="myBtn">
   <input type="button" value="按钮1" id="myBtn1">
   <input type="button" value="按钮2" id="myBtn2">

   <script type="text/javascript">
       /*
         第二种注册事件方式, 是使用纯JS代码完成事件的注册
         这种写法 js代码必须放在 调用html id属性代码的后面 要不然调用不到
        */
       // 第一步: 先获取这个按钮对象(document是全部小写, 内置对象, 可以直接使用, document就代表整个HTML页面)
       // getElementById(按 ID 获取元素)函数 , 通过id去获取这个元素
       var btnObj = document.getElementById("myBtn");
       // 第二步:给按钮对象的onclick属性赋值
       function hello() {
           alert("wbmssb");
       }
       btnObj.onclick = hello; // 注意: 千万不要写小括号, btnObj.onclick = hello(); 这是错误的写法
                               // 这行代码的含义是, 将回调函数hello注册到click事件上

       var elementById = document.getElementById("myBtn1");
       elementById.onclick = function () { // 这个函数没有名字, 叫做匿名函数, 这个匿名函数也是一个回调函数
           alert("wwww") // 这个函数在页面打开的时候只是注册上, 不会被调用, 在click事件发生之后才会调用
       }

       // 一行代码写出注册事件
       document.getElementById("myBtn2").onclick=function () {
             alert("222222222");
       }

   </script>
</body>
</html>
```



## 6.关于`JS`代码的执行顺序

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS的常用事件</title>
</head>
<body>
   <script type="text/javascript">
       // 对于当前查询来说, sayHello函数被称为回调函数(callback函数)
       // 回调函数的特点: 自己把这个函数代码写出来, 但是这个函数不是自己负责调用, 由其他程序负责调用该函数
       function sayHello() {
           alert("hello wbm!")
       }
   </script>

    <!--注册事件的第一种方式, 直接在标签中使用事件句柄-->
    <!--以下代码的含义是, 将sayHello函数注册到按钮上, 等待click事件发生之后, 该函数被浏览器调用, 我们称这个函数为回调函数-->
    <input type="button" value="hello" onclick="sayHello()">
</body>
</html>
```



```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JS代码的执行顺序</title>
</head>
<body >
<script type="text/javascript">

  // 页面加载的过程中, 将a的数注册给了load(页面加载完成)事件
  // 页面加载完毕之后, load事件方式了,此时执行回调函数a
  // 回调数a执行的过程中, 把b函数注册给了id="btn"的click事件
  // 当id="btn"的节点方式click事件之后, b函数被调用, 并执行了
  window.onload = function(){ // 这个回调函数叫做a
    var btn = document.getElementById("btn");
    btn.onclick=function () {  // 这个回调函数叫做b
      alert("hello js");
    }
  }

</script>
<input type="button" value="hello" id="btn">
</body>
</html>
```





## 7. `JS`代码设置节点的属性

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS代码设置节点的属性</title>
</head>
<body>
       <script type="text/javascript">
           window.onload = function () {
                document.getElementById("btn").onclick = function () {
                    var mytext = document.getElementById("mytext");
                    // 一个节点对象中只要有的属性都可以修改
                    mytext.type="checkbox";
                }
               
           }

       </script>
   <input type="text" id="mytext">
   <input type="button" value="将文本框修改为复选框" id="btn">

</body>
</html>
```



## 8.`JS`代码捕捉回车键

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS代码捕捉回车键</title>
</head>
<body>
            <script type="text/javascript">
                 window.onload=function () {
                     var usernameElt = document.getElementById("username");
                     // 回车键的键值是13
                     // ESC键的值是27
                     // event 局部变量, 或者说是参数, 在onkeydown只会传递一个参数, 变量名是可以随便写的
                     usernameElt.onkeydown = function (event,a,b) {
                        // 获取键值
                       // alert(event); //  object KeyboardEvent
                       //  alert(b) // undefined
                         //对于键盘事件对象来说, 都有keyCode属性用来获取键值
                         var keyCode = event.keyCode; // 获取键值
                        // alert(keyCode);
                         if (keyCode === 13) { // 如果键值是13就表示是回车键, 这样就可以不用手点登录, 使用回车键就可以登录了
                             alert("正在进行验证")
                         }
                     }
                 }

            </script>
            <input type="text" id="username">
</body>
</html>
```



## 9.`JS`运算符之void

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>运算符之void</title>
</head>
<body>
      <!--
         void运算符的语法, void(表达式)
         运算原理, 执行表达式, 但不返回任何结果
         如果在 a标签的href中使用, 必须声明void是js中的代码
         就需要这样表示 href="javascript:void(0)", 也可以js:void(0)
         其中JavaScript:作用是告诉平浏览器后面的是一段js代码
         以下程序

      -->
      页面顶部<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
       <a href="javascript:void(0)" onclick="window.alert('test code')">既保留住超链接的样式, 同时用户点击该超链接的时候执行一段js代码, 但页面不能跳转</a> <br>
       <a href="javascript:void(100)" onclick="window.alert('test code')">既保留住超链接的样式, 同时用户点击该超链接的时候执行一段js代码, 但页面不能跳转</a> <br> <!--可以是void(100)-->
       <!--<a href="javascript:void()" onclick="window.alert('test code')">既保留住超链接的样式, 同时用户点击该超链接的时候执行一段js代码, 但页面不能跳转</a> 但是不能为空 <br>-->
      <br><br><br><br><br><br>


</body>
</html>
```



## 10.`JS`的控制语句

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>的控制语句</title>
</head>
<body>
     <script type="text/javascript">
       /*
           1. if
           2. switch

           3. while
           4. do .. while..
           5. for循环

           6. break
           7. continue

           8. for..in语句 (了解)
           9. with语句
        */
/*

       // 创建JS数组, js数组中元素的类型随意, 元素的个数随意
       var arr = [false,true,1,2,"abc",3.14];

       // 遍历数组

      // for i 循环
       for (let i = 0; i < arr.length; i++) {
           alert(arr[i])
       }

       // 增强for循环
       for (let arrElement of arr) {
            alert(arrElement)
       }

       // for in  相当于 for i
       for (var i in arr) {
         // alert(i) // 返回的是数字的下标
         alert(arr[i]) // 因为返回的是下标, 那么就可以跟 for i 一样的执行操作
       }
*/

       // for..in语句可以遍历对象的属性
       User = function (username,password) {
            this.username=username;
            this.password=password;
       }

       var u = new User("wbm","123456");
       // 访问对象属性
       alert(u["username"]+ "," +u["password"]);
       alert("username="+u.username+ ","+"password="+u.password);

       // 使用 for in 遍历对象的属性
       for (let uKey in u) {
           alert(uKey); // 第一次为username , 第二次为password
           alert(typeof uKey); // 类型为string
           alert(u[uKey])
       }
       
       // with
       with (u) {
           /**
            * 相当于 u.username+","+u.password, 他会自动拼接u.
            */
          alert(username+","+password);
       }
     </script>
</body>
</html>

<!--
    public class Test{
      public static void main(String[] args){
            int[] arr={1,2,3,4,5};
            int[] arr2=new int[5]; // 等同于, int[] arr2 = {0,0,0,0,0};

            String[] str ={"a","b","c"}
            String[] str2 =new String[3]; // 等同于,String[] str ={"","",""}
      }
    }

-->
```



# DOM篇

```text
1. JavaScript包括三大块
   ECMAScript: JS的核心语法(ES规范 / ECMA-262标准)

   DOM: Document Object Model (文档对象模型, 对页面当中的节点进行增删改的过程.) HTML文档被当做一棵DOM树来看待
        document.getElementById("id");

   BOM: Browser Object Model (浏览器对象模型)
        关闭浏览器窗口, 打开一个新的浏览器窗口, 后退, 前进, 浏览器地址栏上的地址等, 都是BOM编程

2. DOM和BOM的区别和联系
   BOM的顶级对象是: window
   DOM的顶级对象是: document
   实际上BOM是包括DOM的!
   
     案例 :
           window.onload = function () {
           // var elementById = window.document.getElementById("btn"); // window是可以省略的
           var elementById = document.getElementById("btn"); // window是可以省略的
           alert(elementById)// object HTMLInputElement

           <input type="button" id="btn" value="hello">
```

![关系图](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fwenwen.soso.com%2Fp%2F20180911%2F20180911044237-968812432_png_580_344_59790.jpg&refer=http%3A%2F%2Fwenwen.soso.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1651741125&t=345ba036ea50fbe2b96cf15b08c7422a)



## `JS`设置和获取文本框的value

案例:

![image-20220405173949316](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220405173949316.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM编程-获取文本框的value</title>
</head>
<body>
   <script type="text/javascript">
       window.onload=function () {
           var elementById = document.getElementById("btn");
           elementById.onclick=function () {
            /*   // 获取id为 username的文本框
               var usernameElt = document.getElementById("username");
               // 在获取文本框的 value
               var username = usernameElt.value;
              */
               // 连起来一块写
               var username = document.getElementById("username").value;
               alert(username)
           }
       }
   </script>
    <input type="text" id="username">
     <input type="button" value="获取文本框的value" id="btn">
</body>
</html>
```



案例:

![image-20220405175223209](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220405175223209.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM编程-获取文本框的value</title>
</head>
<body>
   <script type="text/javascript">
       window.onload=function () {
           var elementById = document.getElementById("btn");
           elementById.onclick = function () {
              var text1Value = document.getElementById("text1").value;
               document.getElementById("text2").value = text1Value;
               document.getElementById("text1").value="";

           }
       }
   </script>
    <input type="text" id="text1"><br/>
    <input type="text" id="text2"><br/>
     <input type="button" value="把第一个文本框中的值放到文本框2中" id="btn">
</body>
</html>
```

```html
<!--blur事件, 当这个文本框失去焦点, 就会弹出写下的东西, this表示的是这个文本框
    以下代码中的this代表的是当前input节点对象, thisvalue就是这个节点对象的value属性    -->
<input type="text" onblur="alert(this.value)">
```



## inner HTML和 inner Text操作div和span

```text
innerText和innerHTMl属性有什么区别?
    相同点: 都是设置元素内部的内容
    不同点: innerHTML会把后面的"字符串"当做一段HTML代码解释并执行
           innerText, 即使后面是一段HTML代码也只是将其当做普通的字符串来看待
```



案例:

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220405231023623.png" alt="image-20220405231023623" style="zoom:50%;" />

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM编程-innerHTML和innerText</title>
    <style type="text/css">
        #div1{
            background-color: saddlebrown;
            width: 300px;
            height: 300px;
            border:  1px black solid;
            position: absolute;
            top: 100px;
            left: 100px;
        }
    </style>
</head>
<body>
      <script type="text/javascript">
          window.onload = function () {
               var btnById = document.getElementById("btn");
               btnById.onclick = function () {
                   // 设置div的内容
                   // 第一步: 获取div对象
                   var div1 = document.getElementById("div1");
                   // 第二步: 使用innerHTML这个属性来设置元素内部的内容
                   //  div1.innerHTML="<h1>wbm</h1>";
                   div1.innerText="<h1>wbm</h1>";
               }
          }
      </script>
      <input type="button" value="设置div中的内容" id="btn">
      <div id="div1">

      </div>

</body>
</html>
```

使用`innerHTML`的效果

![image-20220405230756747](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220405230756747.png)

使用innerText的效果

![image-20220405230853271](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220405230853271.png)



## 关于正则表达式

```text
 1. 什么是正则表达式, 有什么用?
       正则表达式: Regular Expression
       正则表达式主要用在字符串格式匹配方面.

  2. 正则表达式实际上是一门独立的学科, 在java语言中支持, c语言中也支持, JavaScript中也支持.
     大部分编程语言都支持正则表达式, 正则表达式最初使用在医学方面, 用来表示神经符号等. 目前使用最多的是计算机编程领域,
     用作字符串格式匹配, 包括搜索方面等

  3. 正则表达式, 对于我们JavaScript编程来说, 掌握那些内容呢?
     第一, 常见的正则表达式符号要认识
     第二, 简单的正则表达式要会写
     第三, 他人编写的正则表达式要能看懂
     第四, 在javascript当中, 怎么创建正则表达式对象 ! (new 对象)
     第五, 在javascript当中, 正则表达式对象有那些方法 ! (调方法)
     第六, 要能够快速的从网络上找到自己需要的正则表达式, 并且测试其有效性


  4. 常见的正则表达式符号
      .  小数点可以匹配除了换行符（\n）以外的任意一个字符
      \w  可以匹配任何一个字母或者数字或者下划线
      \s  可以匹配空格、制表符、换页符等空白字符的其中任意一个
      \d  匹配数字
      \b  匹配单词的开始或结束
      ^   匹配字符串的开始
      $   匹配字符串的结束

      *  重复零次或更多次
      +  重复一次或更多次
      ?  重复零次或一次
      {n} 重复n次
      {n,} 重复n次或更多次
      {n,m} 重复n到m次

      \W W大写，可以匹配任何一个字母或者数字或者下划线以外的字符
      \S S大写，可以匹配任何一个空白字符以外的字符
      \D D大写，可以匹配任何一个非数字字符
      \B B大写, 可以匹配表示单词开头或结束的位置
      [^x] 匹配除了x以外的任意字符
      [^wbm] 匹配除了wbm这几个字母以外的任意字符

      正则表达式当中的小括号()优先级比较高
      [1-9] 表示1到9的任意一个数字 (次数是1次)
      [A-Za-z0-9] 表示A到Z, a到z, 0到9中的任意一个字符
      [A-Za-z0-9-] 表示A到Z, a到z, 0到9, - 中的任意一个字符
      | 表示或

5. 觉得的表达式要会写
   QQ的正则表达式: ^[1-9][0-9](4,)$

6. 他人编写的表达式要能看懂
   邮箱表达式:^([0-9a-zA-Z]([-.\\w]*[0-9a-zA-Z])*@(([0-9a-zA-Z])+([-\\w]*[0-9a-zA-Z])*\\.)+[a-zA-Z]{2,9})$

7. 怎么创建正则表达式对象, 怎么调用正则表达式对象的方法
    第一种创建方式:
         var regExp = /正则表达式/flags;

    第二种创建方式, 使用内置支持类RegExp
         var regExp = new RegExp("正则表达式","flags");

    关于flags:
       g: 全局匹配
       i: 忽略大小写
       m: 多行搜索(ES规范指定之后才支持m), 当前面是正则表达式的时候, m不能用, 只有前面是普通字符串的时候, m才可以使用
```



案例

![image-20220406184219377](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220406184219377.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>DOM编程-关于正则表达式</title>
</head>
<body>
    <script type="text/javascript">
      /*
             正则表达式对象的test()方法
                 返回的值为true/false
                 正则表达式.test("用户写的字符串");
                 true : 字符串格式匹配成功
                 false : 字符串格式匹配失败
       */

      window.onload = function () {
          
          // 先得到 id为btn的按钮 在设置点击事件
           document.getElementById("btn").onclick =function () {
                var emailValue =  document.getElementById("email").value;// 获取文本框中的value
                var regExp = new RegExp("^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\\.[a-zA-Z0-9-]+)*\\.[a-zA-Z0-9]{2,6}$"); // 邮箱的正则表达式
                var b = regExp.test(emailValue); // 判断emailValue是否是邮箱格式
                if (b) {
                  document.getElementById("emailError").innerText="邮箱格式合法";
                }else {
                   document.getElementById("emailError").innerText="邮箱格式错误";
                }
            }

          // 当文本框失去焦点的时候, id为emailError 的span的文字会被清空
          document.getElementById("email").onblur = function () {
              document.getElementById("emailError").innerText="";
          }
          
      }
    </script>
    <input type="text" id="email">
    <span id="emailError" style="color: red; font-size: 12px;"></span><br>
    <input type="button" value="验证邮箱" id="btn">
</body>
</html>
```



## 扩展字符串的trim函数(去除前后空白)

 案例

![image-20220406190027379](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220406190027379.png)



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>扩展字符串的trim函数</title>
</head>
<body>
  <script type="text/javascript">
     window.onclick = function () {
          // 获取按钮的点击事件
           document.getElementById("btn").onclick = function () {
             // 获取用户名
               var usernameValue = document.getElementById("username").value;
               // 去除前后空白
               usernameValue = usernameValue.trim()
               //测试
               alert("--->"+usernameValue+"<---");
           }
     }
  </script>
  <input type="text" id="username">
  <input type="button" id="btn" value="获取用户名">
</body>
</html>
```



### 在低版本的IE浏览器不支持字符串的trim()函数, 怎么解决?

我们可以自己重写一个trim函数

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>扩展字符串的trim函数</title>
</head>
<body>
  <script type="text/javascript">
   // 低版本的IE浏览器不支持字符串的trim()函数, 怎么解决?, 可以自己对String类扩展一个全新的trim()函数
    String.prototype.trim=function () { // 重写String的trim方法
             // alert("扩展之后的trim方法")
             // 去除当前字符串的前后空白
             // 在当前的方法中的this代表的就是当前字符串
             // 使用正则表达式需要// 里面放的是正则表达式  \s+  ^表示字符串开始 表示有一个空格或者多个   $表示字符串结束
             return this.replace(/^\s+/,"").replace(/\s+$/,"");
    }
     window.onclick = function () {
      // 获取按钮的点击事件
       document.getElementById("btn").onclick = function () {
         // 获取用户名
           var usernameValue = document.getElementById("username").value;
           // 去除前后空白
           usernameValue = usernameValue.trim()
           //测试
           alert("--->"+usernameValue+"<---");
       }
 }
  </script>
  <input type="text" id="username">
  <input type="button" id="btn" value="获取用户名">
</body>
</html>
```





## 表单验证

用户名不能为空

用户名必须在6-14位之间

用户名只能有数字和字母组成, 不能含有其他符号

密码和确定密码一致, 邮箱地址合法

统一失去焦点验证

错误提示信息统一在span标签中提示, 并且要求字体12号, 红色

文本框在次获取焦点后, 清空错误提示信息, 如果文本框中数据不合法要求清空文本框的value

最终表单中所有项都合法方可提交

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单验证</title>
    <style>
        span{
            color: red;
            font-size: 12px;
        }
    </style>
    <script type="text/javascript" src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
</head>
<body>
        <script type="text/javascript">
            /**
             需求:

             用户名不能为空
             用户名必须在6-14位之间
             用户名只能有数字和字母组成, 不能含有其他符号
             密码和确定密码一致, 邮箱地址合法
             统一失去焦点验证
             错误提示信息统一在span标签中提示, 并且要求字体12号, 红色
             文本框在次获取焦点后, 清空错误提示信息, 如果文本框中数据不合法要求清空文本框的value
             最终表单中所有项都合法方可提交
             */

            window.onload = function () {
                // 得到用户名
                var username = document.getElementById("username");
                // 得到username的span标签
                var usernameError = document.getElementById("usernameError");


                // 给用户名文本框绑定blur(失去焦点)事件
                username.onblur= function () {
                    // 得到用户名(就是输入文本框的value), 并且去除前面空格
                    var userValue = username.value.trim();

                    // 用户名的正则表达式 6到14位（字母，数字）
                    var uPattern = new RegExp("^[a-zA-Z0-9-]{6,14}$");

                    if ( userValue == "") {
                        // 当用户名为空的时候, span标签会显示用户名不能为空
                        usernameError.innerText="用户名不能为空";
                    }else if (!uPattern.test(userValue)){
                        // 用户名必须在6-14位之间并且不能加上字符, 要不然这里会提示
                        usernameError.innerText="用户名必须要6-14位之间并且不能加上字符";
                    }

                }

                // 当用户名得到焦点, 会去除span中的字, 并且清空文本框的字或者空格
                username.onfocus = function () {

                    // 当 span标签中有提示错误的时候, 就清空文本框的内容
                    if (usernameError.innerText!=""){
                        username.value="";
                    }
                    // 清除span的必须要在下面, 要不然上面的if会一直不执行, 因为清除了span标签的字
                    usernameError.innerText="";
                }

                // 得到密码1
                var pwd = document.getElementById("pwd");
                // 得到密码2
                var pwd2 = document.getElementById("pwd2");
                // 得到密码2的span标签
                var pwdError = document.getElementById("pwdError");
                var pwdError1 = document.getElementById("pwd1Error");
                // 密码1的value
                var pwd1value = pwd.value.trim();
                pwd.onblur= function () {
                    if (pwd1value == "") {
                        pwdError1.innerText="密码不能为空"
                    }
                }
                // 密码和确定密码一致
                 pwd2.onblur = function () {
                    // 得到密码1和2,标签清空前面空格

                      var value2 = pwd2.value.trim();
                      // 如果密码为空, 会提示
                     if (value2 == "") {
                         pwdError.innerText="密码不能为空"
                     }else if (pwd1value!=value2){ // 如果密码1不等于2, 会提示
                         pwdError.innerText="密码必须一致"
                     }
                 }

                 // 当 密码2得到焦点以后会清除span标签的字
                pwd2.onfocus = function () {
                    // 当 span标签中有提示错误的时候, 就清空密码2的内容
                    if (pwdError.innerText!=""){
                        pwd2.value="";
                    }
                    // 清除span的必须要在下面, 要不然上面的if会一直不执行, 因为清除了span标签的字
                    pwdError.innerText="";
                }


                // 得到邮箱
                var email = document.getElementById("email");
                // 得到邮箱的span标签
                var emailError = document.getElementById("emailError");
                // 邮箱验证
                // 当邮箱失去焦点的时候
                email.onblur = function () {
                    // 邮箱的正则表达式
                    var regExp = new RegExp("^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\\.[a-zA-Z0-9-]+)*\\.[a-zA-Z0-9]{2,6}$");
                    //得到邮箱文本框的value
                    var emailvValue = email.value.trim();
                    // 当邮箱为空或者格式不对的时候, 会提示错误
                    if (emailvValue == "") {
                        emailError.innerText="邮箱不能为空";
                    }else if (!regExp.test(emailvValue)){
                        emailError.innerText="邮箱格式不对"
                    }

                }


                // 当邮箱得到焦点以后会清除span标签的字
                email.onfocus = function () {
                    // 当 span标签中有提示错误的时候, 就清空邮箱的内容
                    if (emailError.innerText!=""){
                        email.value="";
                    }
                    // 清除span的必须要在下面, 要不然上面的if会一直不执行, 因为清除了span标签的字
                    emailError.innerText="";
                }

                // 给提交按钮绑定鼠标单击事件
                // 获取表单对象通过id
                var submit = document.getElementById("submit2");
                submit.onclick= function () {
                    // 触发用户名,确定密码,邮箱的blur事件
                    // 使用技术触发事件

                       usernameError.focus();
                       usernameError.blur()


                   //  setTimeout("",50)
                    pwdError.focus();
                    pwdError.blur();

                    emailError.focus();
                    emailError.blur();
                    // 当所有表单项都是合法的时候, 提交表单
                    if (usernameError.innerText=="" && pwdError.innerText=="" && emailError.innerText==""){
                        // 提交表单
                        var form = document.getElementById("for");
                        form.action="https://www.baidu.com";
                        form.submit();
                    }
                }

            }
        </script>

      <div >
          <form action="JavaScript:void(0)" method="post" id="for">
              <table>

                  <!--用户名-->
                  <tr>
                      <td> 用户名 </td>
                      <td> <input type="text" name="username" id="username"> </td>
                      <td> <span id="usernameError"></span><br> </td>
                  </tr>

                  <!--密码-->
                  <tr>
                      <td> 密码 </td>
                      <td> <input type="password" name="password" id="pwd"></td>
                      <td> <span id="pwd1Error"></span><br> </td>
                  </tr>


                  <!--确定密码-->
                  <tr>
                      <td> 确定密码 </td>
                      <td> <input type="password" id="pwd2"> </td>
                      <td>  <span id="pwdError"></span><br> </td>
                  </tr>


                  <!--邮箱-->
                  <tr>
                      <td> 邮箱 </td>
                      <td> <input type="text" name="email" id="email"> </td>
                      <td> <span id="emailError"></span><br> </td>
                  </tr>

                  <!--提交加重置-->
                  <tr>
                      <td>
                          <input type="reset">
                      </td>

                      <td>
                          <!--<input type="submit"  value="注册"> 不使用submit-->
                          <input type="button" id="submit2"  value="注册">
                      </td>
                  </tr>


              </table>

          </form>
      </div>
</body>
</html>
```







## 复选框的全选和取消全选

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>复选框的全选和取消全选</title>
</head>
<body>
      <script type="text/javascript">
      window.onload = function () {
          // 先获取全选
          var selectAll = document.getElementById("selectAll");
          // 获取其他复选框的name
          var aihao = document.getElementsByName("aihao");
          // 全选的点击事件
          selectAll.onclick = function () {
              // 遍历复选框
              for (let i = 0; i < aihao.length; i++) {
                  // 如果全选打钩了, 其他也会跟着打钩
                  aihao[i].checked=selectAll.checked;
              }

              // 遍历复选框
              for (let i = 0; i < aihao.length; i++) {
                  // 复选框的点击事件
                  aihao[i].onclick = function () {
                      // 设置一个监视复选框打钩的变量
                      var ip= 0;
                      // 当复选框每次被点击以后, 就会遍历
                      for (let j = 0; j < aihao.length; j++) {
                          // 如果aihao[j].checked是true, ip就++
                          if (aihao[j].checked) {
                              ip++;
                          }
                          // 如果全部复选框都打上钩了 aihao.length 一定等于 ip
                          selectAll.checked = (aihao.length == ip)
                      }
                  }
              }
          }
      }
      </script>
     <input type="checkbox" id="selectAll">全选 <br>
     <input type="checkbox" name="aihao" value="smokes"/>抽烟 <br>
     <input type="checkbox" name="aihao" value="drink"/>喝酒  <br>
     <input type="checkbox" name="aihao" value="perm"/>烫头  <br>
</body>
</html>
```





## 获取下拉列表选中项中的value

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>获取下拉列表选中项中的value</title>
</head>
<body>

        <script type="text/javascript">
          window.onload = function () {
            var cs = document.getElementById("cs");
            // onchange 改变事件, 当值改变的时候就会触发改变事件
            cs.onchange = function () {
              alert(cs.value)
            }
          }

        </script>
       <select id="cs">
         <option >请选择你的城市</option>
         <option value="bj">北京</option>
         <option value="gz">广州</option>
         <option value="sz">深圳</option>
         <option value="dg">东莞</option>
         <option value="xm">厦门</option>
         <option value="sh">上海</option>
       </select>
</body>
</html>
```



## 显示网页时钟

`js`中的Date类

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>显示网页时钟</title>
</head>
<body>
      <script type="text/javascript">
          /*
               关于JS中内置的支持类: Data, 可以用来获取时间/日期
           */
              // 获取系统当前时间
              var nowTime = new Date();
              // 输出
              //  document.write(nowTime); // Fri Apr 08 2022 22:28:46 GMT+0800 (中国标准时间) 相当于java中的sout
              // 转换成具有本地语言环境的日期格式
              nowTime = nowTime.toLocaleString();
              document.write(nowTime); // 2022/4/8 22:31:51    年月日加时间
              document.write("<br>")

            //  当以上格式表示自己需要的, 可以通过日期获取年月日等信息, 自定制日期格式
              var date = new Date();
              var n = date.getFullYear(); // 获取年
              var month = date.getMonth(); // 获取月
              var day = date.getDay();// 获取日
              var hours = date.getHours(); // 获取时
              var minutes = date.getMinutes();// 获取分
              var milliseconds = date.getMilliseconds();// 获取毫秒
               var time = date.getTime(); // 获取时间戳, 从1970年1月1日  00:00:00:0000到当前系统时间的总毫秒数
               document.write(n+"年"+month+"月"+day+"日"+hours+"点"+minutes+"分"+milliseconds+"毫秒") ;
      </script>
</body>
</html>
```

![image-20220408225016441](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220408225016441.png)



### setInterval函数

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>显示网页时钟</title>
</head>
<body>
      <script type="text/javascript">
                  var hqsj = function () {
                      var date = new Date();
                      var fullYear = date.getFullYear(); // 获取年
                      var month = date.getMonth(); // 获取月
                      var day = date.getDay(); // 获取日
                      var hours = date.getHours(); // 获取时
                      var minutes = date.getMinutes(); // 获取分
                      var seconds = date.getSeconds(); //获取秒
                      document.getElementById("d").innerText= fullYear+"年"+month+"月"+day+"日"+hours+"时"+minutes+"分"+seconds+ "秒"
                  }
                 // setInterval函数
                  // 每隔1秒调用hqsj函数

                  function start () {
                      // 从这行代码执行结束开始, 则会不断的, 每隔1000毫秒调用一次hqsj()函数
                      interval =window.setInterval("hqsj()", 1000);  // 如果前面没有var 会变成全局变量
                      // alert(interval) // 从2开始
                  }

                  function  stup (){
                      window.clearInterval(interval);
                  }
      </script>

      <div id="d"></div>
      <input type="button" value="显示系统时间" id="btu"  onclick="start();"><br>
      <input type="button" value="时间停止" id="btu1" onclick="stup()" ><br>
</body>
</html>
```





## 内置类Array

### 创建数组

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>内置类Array</title>
</head>
<body>
       <script type="application/javascript">

            // 创建长度为0的数组
            var arr = [];
            alert(arr.length) // 0

            // 数据类型随意
            var arr2 = [1,2,3,"avc",false,3.14];
            alert(arr2.length) // 6

            // 下标会越界吗? 不会的, 下标是从0开始的, 虽然长度是6, 0 1 2 3 4 5
            arr2[6]="132l";
            alert(arr2+"---------"+arr2[6]) // 1,2,3,avc,false,3.14,,132l---------132l
            document.write("<br>")

            // 遍历数组
            for (let arr2Element of arr2) {
                 document.write(arr2Element+"<br>")
            }

            // 另一种创建数组的对象的方式
            var array = new Array();
            alert(array.length); // 0

            var a2 = new Array(3)
            alert(a2.length); // 3

            var  a3 = new Array(2,3,false);
            alert(a3.length); // 3

       </script>
</body>
</html>
```



### 数组的方法

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>内置类Array</title>
</head>
<body>
       <script type="application/javascript">

           var  a = [1,2,3,4];
           alert(a.length); // 4

           // join函数, 会把数组的元素取出来, 然后再把自己写入的符号添加进每个元素的中间, 然后拼接成一个字符串
           var s = a.join("-");
           alert(s); // 1-2-3-4

           // push函数是用来添加数组元素的, 在数组的末尾添加一个元素
           a.push(10);
           alert(a.length); // 5

           // pop函数, 将数组末尾的元素弹出, 就是会弹出数组中的最后一个元素, 数组长度会-1
           var number = a.pop();
           alert(number) // 10
           alert(a.length)  // 4
           // 注意: JS中的数组可以自动模拟栈的自动模拟数据结构, 后进先出, 先进后出原则
           // push压栈
           // pop弹栈

           // 反转数组
           a.reverse();
           alert(a.join("-")); // 4-3-2-1
       </script>
</body>
</html>
```



# `BOM`编程

### open和close方法

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>BOM编程-open和close</title>
</head>
<body>
      <script type="application/javascript">
              /*
                  1. BOM编程中, window对象是顶级对象, 代表浏览器窗口.
                  2. window有open和close方法, 可以开启窗口和关闭窗口
               */
      </script>
      <input type="button" value="开启百度(新窗口)" onclick="window.open('https://www.baidu.com')">
      <input type="button" value="开启百度(当前窗口)" onclick="window.open('https://www.baidu.com','_self')">
      <input type="button" value="开启百度(新窗口)" onclick="window.open('https://www.baidu.com','_blank')">
      <input type="button" value="开启百度(父窗口)" onclick="window.open('https://www.baidu.com','_parent')">
      <input type="button" value="开启百度(顶级窗口)" onclick="window.open('https://www.baidu.com','_top')"><br>
      <input type="button" value="打开cs.html" onclick="window.open('cs.html')">
</body>
</html>
```

测试关闭的页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>测试关闭当前窗口</title>
</head>
<body>
     <input type="button" value="关闭当前窗口" onclick="window.close()">
</body>
</html>
```



### 弹出消息框和确定框

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>弹出消息框和确定框</title>
    <script type="application/javascript">
     function del() {
         /*
            // 用户点确定就返回true, 取消false
            var b = window.confirm("亲, 确定删除这个学习资料吗!");
            if (b) {
                alert("删除学习资料成功")
            }else {
                alert("取消删除")
            }
            */

            //   // 简化代码
            if (window.confirm("亲, 确定删除这个学习资料吗!")) {
                alert("删除学习资料成功")
            }else {
                alert("取消删除")
            }

        }
    </script>
</head>
<body>
       <input type="button" value="弹出消息框" onclick="window.alert('消息框!')">
       <!--删除操作的时候都要提前得到用户的确认-->
       <input type="button" value="弹出确定框(比如说删除)" onclick="del()">
</body>
</html>
```





### 设置顶级窗口

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>将当前窗口改为顶级窗口</title>
</head>
<body>
     <iframe src="005.html" width="500px" height="px"></iframe>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<script type="application/javascript">
    /*
         如果当前这个窗口表示顶级窗口的话, 将当前窗口设置为顶级窗口
    */
    function setTop() {
        /*
             window是当前浏览器窗口, 代表005.html
             这个if的意思是, 当前窗口的顶级窗口如果"不是自己"
             window.top就是当前窗口对应的顶级窗口
             window.self表示当前自己这个窗口

             现在这个测试, window.top是003html
             window.self 为 005
         */
        if (window.top!=window.self){
            // 将当前窗口设置为顶级窗口
            // window.self.location 是005的地址
            // 将顶级窗口的window.top.location地址设置为005
            window.top.location=window.self.location;
        }
    }
</script>
    005页面
    <input type="button" value="如果当前窗口不是顶级窗口的话, 将当前窗口设置为顶级窗口" onclick="setTop()">
</body>
</html>
```



测试:

![image-20220412163447009](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220412163447009.png)

效果:

![image-20220412163522844](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220412163522844.png)

### history(历史)对象

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>006.html</title>
</head>
<body>
           <a href="007.html">007页面</a>
            <!--window.history 为 历史对象, .go(1) 为前进,  -1为后退 -->
           <input type="button" value="前进" onclick="window.history.go(1)">
</body>
</html>
```



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>007.html</title>
</head>
<body>
     007 page!
    <!--后退有两种方式, history对象的back()函数,  或者go(-1)函数-->
     <input type="button" value="后退" onclick="window.history.back()">
     <input type="button" value="后退" onclick="window.history.go(-1)">
</body>
</html>
```





### location对象设置浏览器地址栏上的URL

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>location对象设置浏览器地址栏上的url</title>
</head>
<body>
       <script type="application/javascript">
            function stu() {
                /*var location = window.location;
                location.href=="https://www.baidu.com";*/

                // 注意需要加https 负责跳转不了
                // window.location.href="https://www.baidu.com";

                // href删除也可以
                // window.location="https://www.baidu.com";

                //document.location.href="https://www.baidu.com";
                document.location="https://www.baidu.com";
            }
       </script>
</body>
      <input type="button" value="百度" onclick="stu()">
</html>

<!--
      总结, 有那些方法可以通过浏览器往服务器发请求?
      1. 表单form的提交
      2. 超链接
      3. document.location
      4. window.location
      5. window.open("url")
      6. 直接在浏览器地址栏上输入url, 然后回车

      以上所有的请求方式都可以携带数据给服务器, 只有通过表单提交的数据才是动态的

-->
```





# `JSON`

## 什么是`JSON`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JSON</title>
</head>
<body>
      <script type="application/javascript">
          /*
               1. 什么是JSON, 有什么用?
                  JavaScript Object Notation, 简称JSON.  (数据交换格式)
                  JSON主要的作用是: 一种标准的数据交换格式. (目前非常流行, 90%以上的系统都使用JSON, 系统A与系统B交换和数据的话, 都是采用JSON)

               2. JSON是一种标准的轻量级的数据交换格式, 特点是:
                  体积小, 易解析

               3. 在实际的开发中有两种数据交换格式, 使用最多, 其一是JSON, 另一个是XML
                  XML体积较大, 解析麻烦, 但是其优点是: 语法严谨. (通常银行相关的系统之间进行数据交换的话会使用XML)

               4. JSON的语法格式
                  var jsonObj = {
                      "属性名" : "属性值",
                      "属性名" : "属性值",
                      "属性名" : "属性值",
                      "属性名" : "属性值",
                      "属性名" : "属性值"
                      ...
                  }
           */

          // 创建一个json对象(JSON也可以称为无类型对象. 轻量级, 轻巧, 体积小, 易解析)
          var studentObj = {
              "sho" : "110",
              "sname" : "张三",
              "sex" : "男"
          }

          // 访问json对象的属性
          alert(studentObj.sho+","+studentObj.sname+","+studentObj.sex)

          // 之前没有使用json的时候, 定义类, 创建对象, 访问对象的属性
          Student = function (sho,sname,sex) {
              this.sho=sho;
              this.sname=sname;
              this.sex=sex;
          }

          var stu = new Student("1001","李四","男");
          alert(stu.sho+","+stu.sname+","+stu.sex)


          // json数组
          var students = [
              {"sno":"110","sname":"王五","sex":"男"},
              {"sno":"120","sname":"lqt","sex":"男"},
              {"sno":"130","sname":"wbn","sex":"男"}
          ];

          // 遍历json数组
          for (let i = 0; i < students.length; i++) {
                var so = students[i];
              alert(so.sho+","+so.sname+","+so.sex)
          }

      </script>
</body>
</html>
```



## 复杂的`JSON`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>复杂一些的JSON对象</title>
</head>
<body>
       <script type="application/javascript">
           var  user = {
               "usercode" : 110,
               "username" : "张三",
               "sex" : "true",
               "address" : {"city" : "北京", "street" : "大兴区", "zipcode" : "1212121"},
               "aihao" : ["smoke","drink","tt"]
           }


           // 访问人名以及居住的城市
           alert(user.username+","+user.address.city) // 张三,北京


           // 设计json格式的数据, 这个json格式的数据可以描述整个班级中每一个学生的信息, 以及总人数信息
           var users = {
               "total" : 3,
               "students" : [
                   {"id":"1","name":"wbm","sex":"男","birth":"1990-10-20"},
                   {"id":"2","name":"lqt","sex":"男","birth":"1990-10-20"},
                   {"id":"3","name":"wbx","sex":"男","birth":"1990-10-20"}
               ]
           };

       </script>
</body>
</html>
```





## `eval`函数

作用是将一段字符串, 转换成`JSON`格式

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>eval函数</title>
</head>
<body>
   <script type="application/javascript">
       /*
           JSON是一种行业的数据交换格式标准
           JSON在JS中以JS对象的形式存在
        */

       window.eval("var i =100");
       //  var i =100; // 相当于这样
       alert("i="+i);  // i=100

       /*
           eval函数的作用是, 将字符串当做一段js代码解释并执行
           
           java连接数据库, 查询数据之后, 将数据在java程序中拼接成JSON格式的"字符串", 将JSON格式的字符串响应到浏览器
           也就是说响应到浏览器上的仅仅是一个"JSON格式的字符串",还不是一个JSON对象
           可以使用eval函数, 将json格式的字符串转换成json对象
        */
       var fromJava = "{\"name\":\"张三\",\"password\":\"123456\"}"; // 这是java程序发过来的json的"字符串"
       window.eval("var jsonObj ="+fromJava);
       // 访问json对象
       alert(jsonObj.name+","+jsonObj.password); // 张三,123456, 在前端取数据
       
       /*
           面试题:
              在JS当中, []和{}有什么区别?
                  [] 是数组
                  {} 是json
              
              java中的数组:  int[] arr = {1,2,3,4} 
              JS中的数组: var arr = [1,2,3,4];
              JSON: var jsonObj = {"属性名":"属性值"}
              
       */
       
       var json = {
           "username" : "wbm"
       }
       // js访问json对象的属性
       alert(json.username);
       alert(json[username]);
   </script>

</body>
</html>
```



## 设置table的tbody

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>设置table的tbody</title>
</head>
<body>
    <script type="application/javascript">
        // 有这些json数据
        var data = {
            "total": 4,
            "emps" : [
                {"empno":7369,"ename":"SMITH","sal":800},
                {"empno":7499,"ename":"ALLEN","sal":1600},
                {"empno":7521,"ename":"WARD","sal":1250},
                {"empno":7566,"ename":"JONES","sal":2975}
            ]
        };

        // 希望把这些数据展示到table中
        window.onload = function () {
            // 获取按钮的id
            var tbody = document.getElementById("displayBth");
            // 设置点击事件
            tbody.onclick = function () {
                // 获取json的数据
                var emps = data.emps;
                // 用来拼接字符串
                var html = "";
                // 遍历json数据
                for (let i = 0; i < emps.length; i++) {
                      var emp = emps[i];
                      // 拼接字符串
                      html += "<tr>";
                      html += "<td>" + emp.empno + "</td>";
                      html += "<td>" + emp.ename + "</td>";
                      html += "<td>" + emp.sal + "</td>";
                }
                // 把拼接好的字符串放到table中
                document.getElementById("empTbody").innerHTML = html;
                // 获取有多少条数据
                document.getElementById("count").innerText = data.total;
            }
        }
    </script>

    <!--当点击这个按钮, 就会显示员工信息列表-->
    <input type="button" value="显示员工信息列表" id="displayBth">
    <h2>员工信息列表</h2>
    <hr>
     <table border="1px" width="50%">
         <tr>
             <th>员工编号</th>
             <th>员工名字</th>
             <th>员工工资</th>
         </tr>

         <tbody id="empTbody">
        <!--
        <tr>
             <td>7369</td>
             <td>SMITH</td>
             <td>800</td>
         </tr>

         <tr>
             <td>7499</td>
             <td>ALLEN</td>
             <td>1600</td>
         </tr>

         <tr>
             <td>7521</td>
             <td>WARD</td>
             <td>1250</td>
         </tr>
         -->

         </tbody>
     </table>
     总共<span id="count">0</span>条数据
</body>
</html>
```





```xml
<?xml version="1.0" encoding="GBK"?>
<Students>
    
    <!--
        HTML和XML有一个父亲: SGML(标准通用的标记语言.)
        HTML主要做页面展示: 所以语法松散. 很随意.
        XML主要做数据存储和数据描述的: 所以语法相当严格
    -->
    <student id ="100">
        <sname>张三</sname>
        <sex>男</sex>
    </student>

    <student id ="101">
        <sname>王五</sname>
        <sex>男</sex>
    </student>

    <student id ="102">
        <sname>李四</sname>
        <sex>男</sex>
    </student>
</Students>
```





























