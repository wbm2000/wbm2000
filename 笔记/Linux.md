

Linux

## 入门概述

> 我们为什么要学习Linux

linux诞生了这么多年，以前还喊着如何能取代windows系统，现在这个口号已经小多了，任何事物发展都有其局限性都有其天花板。就如同在国内再搞一个社交软件取代腾讯一样，想想而已基本不可能，因为用户已经习惯于使用微信交流，不是说技术上实现不了解而是老百姓已经习惯了，想让他们不用，即使他们自己不用亲戚朋友还是要用，没有办法的事情。

用习惯了windows操作系统，再让大家切换到别的操作系统基本上是不可能的事情，改变一个人已经养成的习惯太难。没有办法深入到普通老百姓的生活中，并不意味着linux就没有用武之地了。在服务器端，在开发领域linux倒是越来越受欢迎，很多程序员都觉得不懂点linux都觉得不好意思，linux在开源社区的地位依然岿然不动。

尤其是作为一个后端程序员，是必须要掌握Linux的，因为这都成为了你找工作的基础门槛了，所以不得不学习！

> Linux 简介

Linux 内核最初只是由芬兰人林纳斯·托瓦兹（Linus Torvalds）在赫尔辛基大学上学时出于个人爱好而编写的。

Linux 是一套免费使用和自由传播的类 Unix 操作系统，是一个基于 POSIX（可移植操作系统接口） 和 UNIX 的多用户、多任务、支持多线程和多 CPU 的操作系统。

Linux 能运行主要的 UNIX 工具软件、应用程序和网络协议。它支持 32 位和 64 位硬件。Linux 继承了 Unix 以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。

> Linux 发行版

Linux 的发行版说简单点就是将 Linux 内核与应用软件做一个打包。

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LDkhrDl4H9TqZhwyeNSeaNIyC5tbowflHyRITPKvgAySf3AZJibEUTrSo3fzRm85VDfInZ2olkIgg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

目前市面上较知名的发行版有：Ubuntu、RedHat、CentOS、Debian、Fedora、SuSE、OpenSUSE、Arch Linux、SolusOS 等。

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LDkhrDl4H9TqZhwyeNSeaN7ZnOBfl3V10ButFaRVtnBasIl9rr8qiaibvaQb7iaClPpuxeDFpHyeibHQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

> Linux 应用领域

今天各种场合都有使用各种 Linux 发行版，从嵌入式设备到超级计算机，并且在服务器领域确定了地位，通常服务器使用 LAMP（Linux + Apache + MySQL + PHP）或 LNMP（Linux + Nginx+ MySQL + PHP）组合。

目前 Linux 不仅在家庭与企业中使用，并且在政府中也很受欢迎。

- 巴西联邦政府由于支持 Linux 而世界闻名。
- 有新闻报道俄罗斯军队自己制造的 Linux 发布版的，做为 G.H.ost 项目已经取得成果。
- 印度的 Kerala 联邦计划在向全联邦的高中推广使用 Linux。
- 中华人民共和国为取得技术独立，在龙芯处理器中排他性地使用 Linux。
- 在西班牙的一些地区开发了自己的 Linux 发布版，并且在政府与教育领域广泛使用，如 Extremadura 地区的 gnuLinEx 和 Andalusia 地区的 Guadalinex。
- 葡萄牙同样使用自己的 Linux 发布版 Caixa Mágica，用于 Magalh?es 笔记本电脑和 e-escola 政府软件。
- 法国和德国同样开始逐步采用 Linux。



> Linux vs Windows

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LDkhrDl4H9TqZhwyeNSeaN2skuyLAeialtTQFEDQ5Fd6bPWx2gWVdW6SlHpjV53uTysVOLnk96deQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## 环境搭建

Linux 的安装，安装步骤比较繁琐，现在其实云服务器挺普遍的，价格也便宜，如果直接不想搭建，也可以直接买一台学习用用！

> 安装CentOS（虚拟机安装，耗资源）

1、可以通过镜像进行安装！

2、可以使用我已经制作好的镜像！视频中讲解了该种方式！

3、安装 VMware 虚拟机软件，然后打开我们的镜像即可使用！



> 购买云服务器（推荐）

虚拟机安装后占用空间，也会有些卡顿，我们作为程序员其实可以选择购买一台自己的服务器，这样的话更加接近真实线上工作；

1、阿里云购买服务器：https://www.aliyun.com/minisite/goods?userCode=0phtycgr

2、购买完毕后，获取服务器的ip地址，重置服务器密码，就可以远程登录了

3、下载 xShell 工具，进行远程连接使用！连接成功效果如下：

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LDkhrDl4H9TqZhwyeNSeaNBvcond6ZtueD4qoY5dzGpdogSd9AgcibvN9Hqicx0PLIuCyCeDIrr3FA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**注意事项：**

如果要打开端口，需要在阿里云的安全组面板中开启对应的出入规则，不然的话会被阿里拦截！



> 如果前期不好操作，可以推荐安装宝塔面板，傻瓜式管理服务器

安装教程：https://www.bt.cn/bbs/thread-19376-1-1.html

1、开启对应的端口

2、一键安装

3、安装完毕后会得到远程面板的地址，账号，密码，就可以登录了

4、登录之后就可以可视化的安装环境和部署网站！

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LDkhrDl4H9TqZhwyeNSeaN2Z7icsXTBvbiaU4uTv0y0SUhfibscT3fZHd8Lib1ic54gjLiaLTru2ru64cA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

> 关于域名

如果自己的网站想要上线，就一定要购买一个域名然后进行备案；

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LDkhrDl4H9TqZhwyeNSeaNzgvAZ87ostL7etOEus0vHU1nw9ua07yDIVLGMH4BSzumn9kvX0DkoA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

备案的话需要一些认证和时间，备完完毕后，就可以解析到自己的网站了，这个时候就可以使用域名来进行服务器的访问！



## 走近Linux系统

> 开机登录

开机会启动许多程序。它们在Windows叫做"服务"（service），在Linux就叫做"守护进程"（daemon）。

开机成功后，它会显示一个文本登录界面，这个界面就是我们经常看到的登录界面，在这个登录界面中会提示用户输入用户名，而用户输入的用户将作为参数传给login程序来验证用户的身份，密码是不显示的，输完回车即可！

一般来说，用户的登录方式有三种：

- 命令行登录
- ssh登录
- 图形界面登录

最高权限账户为 root，可以操作一切！

> 关机

在linux领域内大多用在服务器上，很少遇到关机的操作。毕竟服务器上跑一个服务是永无止境的，除非特殊情况下，不得已才会关机。

关机指令为：shutdown ；

```
sync # 将数据由内存同步到硬盘中。

shutdown # 关机指令，你可以man shutdown 来看一下帮助文档。例如你可以运行如下命令关机：

shutdown –h 10 # 这个命令告诉大家，计算机将在10分钟后关机

shutdown –h now # 立马关机

shutdown –h 20:25 # 系统会在今天20:25关机

shutdown –h +10 # 十分钟后关机

shutdown –r now # 系统立马重启

shutdown –r +10 # 系统十分钟后重启

reboot # 就是重启，等同于 shutdown –r now

halt # 关闭系统，等同于shutdown –h now 和 poweroff
```

最后总结一下，不管是重启系统还是关闭系统，首先要运行 **sync** 命令，把内存中的数据写到磁盘中。

> 系统目录结构

登录系统后，在当前命令窗口下输入命令：

```
ls /
```

你会看到如下图所示：

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LDkhrDl4H9TqZhwyeNSeaNSvqpApZkrQNCQFhVhyPoPdtFTibRBEssIj6EmiapgETvK2brVhfliaRRg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

树状目录结构：（Linux的一切资源都挂载在这个 / 根节点下）

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LDkhrDl4H9TqZhwyeNSeaNibQYW2xbQIL38lrCCSPEzFKJhCiau0FvQMFSa37NQxTTbbo3PrpjJic5g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**以下是对这些目录的解释：**

- **/bin**：bin是Binary的缩写, 这个目录存放着最经常使用的命令。
- **/boot：** 这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件。
- **/dev ：** dev是Device(设备)的缩写, 存放的是Linux的外部设备，在Linux中访问设备的方式和访问文件的方式是相同的。
- **/etc：** 这个目录用来存放所有的系统管理所需要的配置文件和子目录。
- **/home**：用户的主目录，在Linux中，每个用户都有一个自己的目录，一般该目录名是以用户的账号命名的。
- **/lib**：这个目录里存放着系统最基本的动态连接共享库，其作用类似于Windows里的DLL文件。
- **/lost+found**：这个目录一般情况下是空的，当系统非法关机后，这里就存放了一些文件。
- **/media**：linux系统会自动识别一些设备，例如U盘、光驱等等，当识别后，linux会把识别的设备挂载到这个目录下。
- **/mnt**：系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在/mnt/上，然后进入该目录就可以查看光驱里的内容了。
- **/opt**：这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则就可以放到这个目录下。默认是空的。
- **/proc**：这个目录是一个虚拟的目录，它是系统内存的映射，我们可以通过直接访问这个目录来获取系统信息。
- **/root**：该目录为系统管理员，也称作超级权限者的用户主目录。
- **/sbin**：s就是Super User的意思，这里存放的是系统管理员使用的系统管理程序。
- **/srv**：该目录存放一些服务启动之后需要提取的数据。
- **/sys**：这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个文件系统 sysfs 。
- **/tmp**：这个目录是用来存放一些临时文件的。
- **/usr**：这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似于windows下的program files目录。
- **/usr/bin：** 系统用户使用的应用程序。
- **/usr/sbin：** 超级用户使用的比较高级的管理程序和系统守护程序。
- **/usr/src：** 内核源代码默认的放置目录。
- **/var**：这个目录中存放着在不断扩充着的东西，我们习惯将那些经常被修改的目录放在这个目录下。包括各种日志文件。
- **/run**：是一个临时文件系统，存储系统启动以来的信息。当系统重启时，这个目录下的文件应该被删掉或清除。
- /www : 存放服务器网站相关的资源, 环境. 网站的项目



## 常用的基本命令

### 目录管理

>绝对路径, 相对路径

我们知道Linux的目录结构为树状结构，最顶级的目录为根目录 `/`。

其他目录通过挂载可以将它们添加到树中，通过解除挂载可以移除它们。

在开始本教程前我们需要先知道什么是绝对路径与相对路径。



>绝对路径

路径的写法，由根目录 `/` 写起，例如：`/usr/share/doc` 这个目录   因为在linux中的根目录是 / 所以是从 / 开始的 

比如:  我们用绝对路径 到  www目录下的wwwroot的这个目录 

![image-20220126135535032](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126135535032.png)



 也就是使用命令  cd /www/wwwroot

![image-20220126141329993](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126141329993.png)

 

> 相对路径：

查看 wwwroot目录下有什么文件

![image-20220126141524622](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126141524622.png)



可以看到有一个default的目录

我们可以 cd default/  这样到default  这个目录

![image-20220126141906480](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126141906480.png)







> ls()列出目录

在Linux中 ls命令 可能是最常用的

- ls -a : 查看全部的文件, 包括隐藏文件

- ls -l : 列出所有的文件, 包含文件的属性和权限, 不包括隐藏文件

- ls -al : 所有的Linux可以组合使用!   这个表示 查看全部文件, 包括隐藏文件, 也包含文件的属性和权限

  ![image-20220126143146064](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126143146064.png)



> cd 命令 切换目录

- cd   目录名: 切换目录的命令

- cd .. : 返回上一级目录

- cd ./ : 当前目录

- cd ../user : 返回上一层, 并且切换到user目录

- cd ~  : 会到 root目录

  ![image-20220126144034392](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126144034392.png)



> pwd 显示当前用户所在的目录

![image-20220126144226535](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126144226535.png)





> mkdir 创建一个目录

- mkdir 目录名 : 创建一个目录

![image-20220126144513134](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126144513134.png)

- 如果想创建层级目录: 不是这样 mkdir  test1/test2/test3 

  是这样mkdir -p test1/test2/test3

  ![image-20220126145215880](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126145215880.png)

![image-20220126145338998](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126145338998.png)





> rmdir 删除目录  

rmdir 仅能删除空的目录 , 如果下面存在文件, 需要先删除文件.

![image-20220126145854785](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126145854785.png)



如果这个文件夹里面不为空的话, 不能这样删除

递归删除多个目录 加上 -p

![image-20220126150143154](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126150143154.png)



只能这样删除 **rmdir -p test/test1/test2**  前提是 test2 目录下没有文件

![image-20220126150532794](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126150532794.png)





> cp (复制文件 或 目录)

可以看到 home目录下 有一个index.html文件 我们来复制它



![image-20220126151450695](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126151450695.png)



![image-20220126152021860](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126152021860.png)



> 如果复制的文件, 已经有了

![image-20220126154826335](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126154826335.png)





> rm  (移除文件或者目录)

- rm -f 忽略不存在的文件, 不会出现警告

  ![image-20220126155957320](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126155957320.png)

- rm -r 递归删除目录 , 如果删除一个总目录它会跳到最下面的子目录开始删除, 并且会有提示

![image-20220126160612948](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220126160612948.png)



- rm -i 互动. 删除询问是否删除
- rm -rf /   系统中所有文件会被删除, 删库跑路就是这样操作的



> mv 移动文件或者目录

- mv -f 强制移动
- mv -u 只替换已经更新过的文件

![image-20220127135326215](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220127135326215.png)



- mv 还可以重命名文件

  ![image-20220127135723699](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220127135723699.png)





### 基本属性

> 看懂文件属性

Linux系统是一种典型的多用户系统，不同的用户处于不同的地位，拥有不同的权限。为了保护系统的安全性，Linux系统对不同的用户访问同一文件（包括目录文件）的权限做了不同的规定。

在Linux中我们可以使用ll或者ls –l命令来显示一个文件的属性以及文件所属的用户和组，如：

![image-20220127150310916](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220127150310916.png)



实例中，boot文件的第一个属性用"d"表示。"d"在Linux中代表该文件是一个目录文件。

在Linux中第一个字符代表这个文件是目录、文件或链接文件等等：

=当为[ d ]则是目录

当为[ - ]则是文件；

若是[ l ]则表示为链接文档 ( link file )；

若是[ b ]则表示为装置文件里面的可供储存的接口设备 ( 可随机存取装置 )；

若是[ c ]则表示为装置文件里面的串行端口设备，例如键盘、鼠标 ( 一次性读取装置 )。

接下来的字符中，以三个为一组，且均为『rwx』 的三个参数的组合。

其中，[ r ]代表可读(read)、[ w ]代表可写(write)、[ x ]代表可执行(execute)。

要注意的是，这三个权限的位置不会改变，如果没有权限，就会出现减号[ - ]而已。

每个文件的属性由左边第一部分的10个字符来确定（如下图）：

![image-20220127151403776](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220127151403776.png)



从左至右用0-9这些数字来表示。

第0位确定文件类型，第1-3位确定属主（该文件的所有者）拥有该文件的权限。第4-6位确定属组（所有者的同组用户）拥有该文件的权限，第7-9位确定其他用户拥有该文件的权限。

其中：

第1、4、7位表示**读权限**，如果用"r"字符表示，则有读权限，如果用"-"字符表示，则没有读权限；

第2、5、8位表示**写权限**，如果用"w"字符表示，则有写权限，如果用"-"字符表示没有写权限；

第3、6、9位表示**可执行权限**，如果用"x"字符表示，则有执行权限，如果用"-"字符表示，则没有执行权限。

对于文件来说，它都有一个特定的所有者，也就是对该文件具有所有权的用户。

同时，在Linux系统中，用户是按组分类的，一个用户属于一个或多个组。

文件所有者以外的用户又可以分为文件所有者的同组用户和其他用户。

因此，Linux系统按文件所有者、文件所有者同组用户和其他用户来规定了不同的文件访问权限。

在以上实例中，boot 文件是一个目录文件，属主和属组都为 root。



#### 修改文件属性

> chgrp：更改文件属组

```test
chgrp [-R] 属组名 文件名
```

-R：递归更改文件属组，就是在更改某个目录文件的属组时，如果加上-R的参数，那么该目录下的所有文件的属组都会更改。



> chown：更改文件属主，也可以同时更改文件属组

```
chown [–R] 属主名 文件名
chown [-R] 属主名：属组名 文件名
```

![image-20220127152859560](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220127152859560.png)



![image-20220127153136705](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220127153136705.png)



> chmod：更改文件9个属性

```
chmod [-R] xyz 文件或目录
```

Linux文件属性有两种设置方法，一种是数字，一种是符号。

Linux文件的基本权限就有九个，分别是owner/group/others三种身份各有自己的read/write/execute权限。

先复习一下刚刚上面提到的数据：文件的权限字符为：『-rwxrwxrwx』， 这九个权限是三个三个一组的！其中，我们可以使用数字来代表各个权限，各权限的分数对照表如下：

r:4 w:2 x:1

![image-20220127153653182](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220127153653182.png)

每种身份(owner/group/others)各自的三个权限(r/w/x)分数是需要累加的，例如当权限为：[-rwxrwx---] 分数则是：

owner = rwx = 4+2+1 = 7

group = rwx = 4+2+1 = 7

others= --- = 0+0+0 = 0



```
chmod 770 filename
```

### 文件内容查看

> 概述

Linux系统中使用以下命令来查看文件的内容：

- cat 由第一行开始显示文件内容

![image-20220128134911438](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128134911438.png)



- tac 从最后一行开始显示，可以看出 tac 是 cat 的倒着写！

![image-20220128135103824](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128135103824.png)



- nl 显示的时候，顺道输出行号！

![image-20220128135216783](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128135216783.png)



- more 一页一页的显示文件内容, 只能往下翻

![image-20220128140001134](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128140001134.png)



- less 与 more 类似，但是比 more 更好的是，他可以往前翻页！(空格翻页, 上下键表示翻动页面) 使用Q离开

  ![image-20220128140426404](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128140426404.png)

  查找字符串  使用 /要查询的字符  / 是向下查询, 向上查询使用?

  ![image-20220128141410324](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128141410324.png)

这里查找set

![image-20220128141446322](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128141446322.png)

使用?

![image-20220128141629242](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128141629242.png)



![image-20220128141704367](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128141704367.png)

n继续寻找下一个

N向上寻找

- head 只看头几行

![image-20220128140513524](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128140513524.png)

- tail 只看尾巴几行

![image-20220128140547767](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128140547767.png)



控制多少行

加参数 -n 在加行数

tail -n 20 文件名

head  一样



![image-20220128140921153](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128140921153.png)

你可以使用 man [命令]来查看各个命令的使用文档，如 ：man cp。

网络配置目录: `/etc/sysconfig/network-scripts`

![image-20220128133938094](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128133938094.png)

在Linux中可以像cmd 中 ping, 也可以查看网络配置

ifconfig命令查看网络配置

![image-20220128134349389](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220128134349389.png)





> cat 由第一行开始显示文件内容

语法：

```
cat [-AbEnTv]
```

选项与参数：

-A ：相当於 -vET 的整合选项，可列出一些特殊字符而不是空白而已；

-b ：列出行号，仅针对非空白行做行号显示，空白行不标行号！

-E ：将结尾的断行字节 $ 显示出来；

-n ：列印出行号，连同空白行也会有行号，与 -b 的选项不同；

-T ：将 [tab] 按键以 ^I 显示出来；

-v ：列出一些看不出来的特殊字符

测试：



```
# 查看网络配置: 文件地址 /etc/sysconfig/network-scripts/
[root@kuangshen ~]# cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE=eth0
BOOTPROTO=dhcp
ONBOOT=yes
```

> tac

tac与cat命令刚好相反，文件内容从最后一行开始显示，可以看出 tac 是 cat 的倒着写！如：



```
[root@kuangshen ~]# tac /etc/sysconfig/network-scripts/ifcfg-eth0
ONBOOT=yes
BOOTPROTO=dhcp
DEVICE=eth0
```



> nl 显示行号

语法：



```
nl [-bnw] 文件
```

选项与参数：

-b ：指定行号指定的方式，主要有两种：-b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)；-b t ：如果有空行，空的那一行不要列出行号(默认值)；

-n ：列出行号表示的方法，主要有三种：-n ln ：行号在荧幕的最左方显示；-n rn ：行号在自己栏位的最右方显示，且不加 0 ；-n rz ：行号在自己栏位的最右方显示，且加 0 ；

-w ：行号栏位的占用的位数。

测试：



```
[root@kuangshen ~]# nl /etc/sysconfig/network-scripts/ifcfg-eth0
1DEVICE=eth0
2BOOTPROTO=dhcp
3ONBOOT=yes
```



> more 一页一页翻动

在 more 这个程序的运行过程中，你有几个按键可以按的：

空白键 (space)：代表向下翻一页；

Enter ：代表向下翻『一行』；

/字串 ：代表在这个显示的内容当中，向下搜寻『字串』这个关键字；

:f ：立刻显示出档名以及目前显示的行数；

q ：代表立刻离开 more ，不再显示该文件内容。

b 或 [ctrl]-b ：代表往回翻页，不过这动作只对文件有用，对管线无用。



```
[root@kuangshen etc]# more /etc/csh.login
....(中间省略)....
--More--(28%) # 重点在这一行喔！你的光标也会在这里等待你的命令
```



> less 一页一页翻动，以下实例输出/etc/man.config文件的内容：

less运行时可以输入的命令有：

空白键 ：向下翻动一页；

[pagedown]：向下翻动一页；

[pageup] ：向上翻动一页；

/字串 ：向下搜寻『字串』的功能；

?字串 ：向上搜寻『字串』的功能；

n ：重复前一个搜寻 (与 / 或 ? 有关！)

N ：反向的重复前一个搜寻 (与 / 或 ? 有关！)

q ：离开 less 这个程序；



```
[root@kuangshen etc]# more /etc/csh.login
....(中间省略)....
:   # 这里可以等待你输入命令！
```





> head 取出文件前面几行

语法：

```
head [-n number] 文件
```

选项与参数：-n 后面接数字，代表显示几行的意思！

默认的情况中，显示前面 10 行！若要显示前 20 行，就得要这样：



```
[root@kuangshen etc]# head -n 20 /etc/csh.login
```



> tail 取出文件后面几行

语法：

```
tail [-n number] 文件
```

选项与参数：

-n ：后面接数字，代表显示几行的意思

默认的情况中，显示最后 10 行！若要显示最后 20 行，就得要这样：



```
[root@kuangshen etc]# tail -n 20 /etc/csh.login
```

## 拓展：Linux 链接概念

Linux 链接分两种，一种被称为硬链接（Hard Link），另一种被称为符号链接（Symbolic Link）。

情况下，ln 命令产生硬链接。

> 硬连接

硬连接指通过索引节点来进行连接。在 Linux 的文件系统中，保存在磁盘分区中的文件不管是什么类型都给它分配一个编号，称为索引节点号(Inode Index)。在 Linux 中，多个文件名指向同一索引节点是存在的。比如：A 是 B 的硬链接（A 和 B 都是文件名），则 A 的目录项中的 inode 节点号与 B 的目录项中的 inode 节点号相同，即一个 inode 节点对应两个不同的文件名，两个文件名指向同一个文件，A 和 B 对文件系统来说是完全平等的。删除其中任何一个都不会影响另外一个的访问。

硬连接的作用是允许一个文件拥有多个有效路径名，这样用户就可以建立硬连接到重要文件，以防止“误删”的功能。其原因如上所述，因为对应该目录的索引节点有一个以上的连接。只删除一个连接并不影响索引节点本身和其它的连接，只有当最后一个连接被删除后，文件的数据块及目录的连接才会被释放。也就是说，文件真正删除的条件是与之相关的所有硬连接文件均被删除。

> 软连接

另外一种连接称之为符号连接（Symbolic Link），也叫软连接。软链接文件有类似于 Windows 的快捷方式。它实际上是一个特殊的文件。在符号连接中，文件实际上是一个文本文件，其中包含的有另一文件的位置信息。比如：A 是 B 的软链接（A 和 B 都是文件名），A 的目录项中的 inode 节点号与 B 的目录项中的 inode 节点号不相同，A 和 B 指向的是两个不同的 inode，继而指向两块不同的数据块。但是 A 的数据块中存放的只是 B 的路径名（可以根据这个找到 B 的目录项）。A 和 B 之间是“主从”关系，如果 B 被删除了，A 仍然存在（因为两个是不同的文件），但指向的是一个无效的链接。

测试：



```
[root@kuangshen /]# cd /home
[root@kuangshen home]# touch f1 # 创建一个测试文件f1
[root@kuangshen home]# ls
f1
[root@kuangshen home]# ln f1 f2     # 创建f1的一个硬连接文件f2
[root@kuangshen home]# ln -s f1 f3   # 创建f1的一个符号连接文件f3
[root@kuangshen home]# ls -li       # -i参数显示文件的inode节点信息
397247 -rw-r--r-- 2 root root     0 Mar 13 00:50 f1
397247 -rw-r--r-- 2 root root     0 Mar 13 00:50 f2
397248 lrwxrwxrwx 1 root root     2 Mar 13 00:50 f3 -> f1
```

从上面的结果中可以看出，硬连接文件 f2 与原文件 f1 的 inode 节点相同，均为 397247，然而符号连接文件的 inode 节点不同。



```
# echo 字符串输出 >> f1 输出到 f1文件
[root@kuangshen home]# echo "I am f1 file" >>f1
[root@kuangshen home]# cat f1
I am f1 file
[root@kuangshen home]# cat f2
I am f1 file
[root@kuangshen home]# cat f3
I am f1 file
[root@kuangshen home]# rm -f f1
[root@kuangshen home]# cat f2
I am f1 file
[root@kuangshen home]# cat f3
cat: f3: No such file or directory
```

通过上面的测试可以看出：当删除原始文件 f1 后，硬连接 f2 不受影响，但是符号连接 f1 文件无效；

依此您可以做一些相关的测试，可以得到以下全部结论：

删除符号连接f3,对f1,f2无影响；

删除硬连接f2，对f1,f3也无影响；

删除原文件f1，对硬连接f2没有影响，导致符号连接f3失效；

同时删除原文件f1,硬连接f2，整个文件会真正的被删除。



echo : 向文件写人字符

![image-20220203135244411](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220203135244411.png)



touch : 创建文件

![image-20220203135330144](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220203135330144.png)





## Vim编辑器

### 什么是Vim编辑器

Vim通过一些插件可以实现和IDE的功能!
 Vim是从Vi发展出来的一个文本编辑器。代码补完、编译及错误跳转等方便编程的功能特别丰富,在程序员中被广泛使用。尤其是Linux中,必须要会使用Vim (查看内容, 编辑内容,保存内容! )
 简单的来说，Vi是老式的字处理器,不过功能已经很齐全了,但是还是有可以进步的地方。
 Vim则可以说是程序开发者的一项很好用的工具。



> 三种使用方式:

基本上Vi/Vim共分为三种模式,分别是, 命令模式( Command mode) ,输入模式( Insert mode ) 和 底线命令模式( Lastline mode )。这三种模式的作用分别是:

**命令模式**
用户刚刚启动Vi/Vim ,便进入了命令模式。
此状态下敲击键盘动作会被Vim识别为命令,而非输入字符。比如我们此时按下i ,并不会输入一个字符, i被当作了一个命令。
以下是常用的几个命令:
●i切换到输入模式,以输入字符。
●x删除当前光标所在处的字符。
●:切换到底线命令模式,以在最底一行输入命令。
若想要编辑文本:启动Vim,进入了命令模式,按下i,切换到输入模式。
命令模式只有一些最基本的命令,因此仍要依靠底线命令模式输入更多命令。









**输入模式**
在命令模式下按下i就进入了输入模式。
在输入模式中，可以使用以下按键：
 字符按键以及Shift组合，输入字符
 ENTER，回车键，换行
 BACK SPACE，退格键，删除光标前一个字符
 DEL，删除键，删除光标后一个字符
 方向键，在文本中移动光标
 HOME/END，移动光标到行首/行尾
 Page Up/Page Down，上/下翻页
 Insert，切换光标为输入/替换模式，光标将变成竖线/下划线
 ESC，退出输入模式，切换到命令模式

![image-20220203141111541](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220203141111541.png)





**底线命令模式**
在命令模式下按下:（英文冒号）就进入了底线命令模式。
底线命令模式可以输入单个或多个字符的命令，可用的命令非常多。
在底线命令模式中，基本的命令有（已经省略了冒号）：
q 退出程序
w 保存文件
按ESC键可随时退出底线命令模式。
2020/7/1





## 账号管理

 Linux系统是一个多用户多任务的分时操作系统,任何一个要使用系统资源的用户,都必须首先向系统管理员申请一个账号,然后以这个账号的身份进入系统。
 用户的账号一方面可以帮助系统管理员对使用系统的用户进行跟踪,并控制他们对系统资源的访问;另一方面也可以帮助用户组织文件,并为用户提供安全性保护。
 每个用户账号都拥有一个唯一的用户名和各自的口令。
 用户在登录时键入正确的用户名和口令后,就能够进入系统和自己的主目录。
 实现用户账号的管理,要完成的工作主要有如下几个方面:
 ●用户账号的添加、删除与修改。
 ●用户口令的管理。
 ●用户组的管理。

> 用户账号的管理

 用户账号的管理工作主要涉及到用户账号的添加、修改和删除。
 添加用户账号就是在系统中创建一个新账号,然后为新账号分配用户号、用户组、主目录和登录ShelI等资源。



> useradd 命令 添加用户

useradd -选项 用户名

- -m:自动创建这个用户的主目录

  useradd -m  yh

  ![image-20220204131317938](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204131317938.png)

  添加的用户会在 /home目录 多出一个用户名的文件夹



-G:给用户分配组



理解一下本质: Linux中一切皆文件,这里的添加用户说白了就是往某-个文件中写入用户的信息了! /etc/passwd

![image-20220204131746394](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204131746394.png)





> 删除用户 userdel

userdel 用户名   如果就这样删除的话他只会删除这个用户, 并不会删除home目录的用户文件夹

需要加一个参数 -r

userdel -r 用户名

![image-20220204132143638](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204132143638.png)





> 修改用户 usermod

对应修改的内容 修改那个用户

![image-20220204133256567](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204133256567.png)



> 切换用户

服务器默认是root用户

![image-20220204133639881](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204133639881.png)



1.切换用户的命令为: su username [username是你的用户名]

![image-20220204133921666](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204133921666.png)



2.从普通用户切换到root用户,还可以使用命令: sudo su

3.在终端输入exit或logout或使用快捷方式ctrl+d ,可以退回到原来用户,其实ctrl+d也是执行的exit命令

![image-20220204135125237](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204135125237.png)

4.在切换用户时,如果想在切换用户之后使用新用户的工作环境,可以在su和username之间加,例如: [su- root]
$表示普通用户，#表示超级用户,也就是root用户



> 用户的密码设置

我们一般通过root创建用户的时候, 需要配置密码!

linux上输入密码是不会显示的, 正常输入就可以了

如果是超级用户

```bash
passwd root 
new password #新密码
re password #修改密码
```

![image-20220204135758483](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204135758483.png)





普通用户

```bash
passwd
(current)UNIX password:
new password: #密码不能过于简单
re password:
```

![image-20220204135943774](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204135943774.png)







普通用户登录

![image-20220204140222853](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204140222853.png)



![image-20220204140239269](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204140239269.png)登录成功



> 普通用户登录修改密码 直接输入passwd

![image-20220204140618853](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204140618853.png)



> 锁定账户

root ,比如张三辞职了!冻结这个账号, 一旦冻结,这个人就登录不上系统了!

```bash
passwd -l cqh #锁定之后这个用户就不能再登录了
passwd -d cqh #把密码清空 这样也能防止用户登录
```

![image-20220204140932299](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204140932299.png)



![image-20220204141023851](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204141023851.png)登录不了了



解锁

```te
passwd -u 用户名
```

![image-20220204141413165](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204141413165.png)





## 用户组管理

 属主、属组
 每个用户都有一个用户组,系统可以对一个用户组中的所有用户进行集中管理(开发、测试、运维)。不同Linux 系统对用户组的规定有所不同,如Linux下的用户属于与它同名的用户组,这个用户组在创建用户时同时创建。
 用户组的管理涉及用户组的添加、删除和修改。组的增加、删除和修改实际上就是对/etc/group文件的更新。



> 创建一个用户组  groupadd 

```tex

[root@wbm2073568608 ~]# groupadd wbmsyg  # 创建一个组叫 wbmsyg
[root@wbm2073568608 ~]# cat /etc/group  # 查看组有多少
root:x:0:  # 0是id 也可以说是权限的等级, root是0
bin:x:1:
daemon:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mem:x:8:
kmem:x:9:
wheel:x:10:
cdrom:x:11:
mail:x:12:postfix
man:x:15:
dialout:x:18:
floppy:x:19:
games:x:20:
tape:x:33:
video:x:39:
ftp:x:50:
lock:x:54:
audio:x:63:
nobody:x:99:
users:x:100:
utmp:x:22:
utempter:x:35:
input:x:999:
systemd-journal:x:190:
systemd-network:x:192:
dbus:x:81:
polkitd:x:998:
ssh_keys:x:997:
sshd:x:74:
postdrop:x:90:
postfix:x:89:
chrony:x:996:
nscd:x:28:
tcpdump:x:72:
ntp:x:38:
www:x:1000: 
mysql:x:1001:
cgred:x:995:
redis:x:1002:
springboot:x:1003: 
wbm:x:1004:
wbmm:x:1005:
wbmsyg:x:1006:  #刚创建的组

```



创建完用户组后可以得到一个组的id, 这个id是可以指定的  

groupadd -g 520{id} 组名

```tex
[root@wbm2073568608 ~]# groupadd -g 520 wbmsu
[root@wbm2073568608 ~]# cat /etc/group
wbmsu:x:520:

```





> 删除用户组 groupdel 用户组名

![image-20220204143503853](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204143503853.png)





> 修改用户组的权限信息和名字   groupmod -g(修改id) -n(修改名字)  要修改的用户组名



- 修改id

```tex
[root@wbm2073568608 ~]# cat /etc/group
wbm:x:1004:
wbmm:x:1005:   # 本来是1005的
wbmsyg:x:1006:

[root@wbm2073568608 ~]# groupmod -g 555 wbmm

[root@wbm2073568608 ~]# cat /etc/group
wbm:x:1004:
wbmm:x:555:  # 555了
wbmsyg:x:1006:

```



- 修改用户组名

![image-20220204144537004](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220204144537004.png)



> 用户切换用户组

````tex
#当前登录用户 cqh
$ newgrp root #切换为root
````



> 拓展 用户账户文件的查看(了解即可) /etc/passwd

用户名:口令(登录密码，我们不可见) :用户标识号:组标识号:注释性描述:主目录:登录She11

这个文件中的每一行都代表这一用户,我们可以从这里看出这个用户的主目录在那里,可以看到属于哪一个组!

```tex
[root@wbm2073568608 ~]# cat /etc/passwd
root(用户名):x(口令(登录密码，我们不可见)):0(用户标识号):0(组标识号):root(注释性描述):/root(主目录):/bin/bash(登录She11)
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
chrony:x:998:996::/var/lib/chrony:/sbin/nologin
nscd:x:28:28:NSCD Daemon:/:/sbin/nologin
tcpdump:x:72:72::/:/sbin/nologin
ntp:x:38:38::/etc/ntp:/sbin/nologin
www:x:1000:1000::/home/www:/sbin/nologin
mysql:x:1001:1001::/home/mysql:/sbin/nologin
redis:x:1002:1002::/home/redis:/sbin/nologin
springboot:x:1003:1003::/home/springboot:/sbin/nologin
wbm:x:1004:1004::/home/2073568608:/bin/bash
wbmm:x:1005:555::/home/wbmm:/bin/bash

```



登录口令:把真正的加密后的用户口令字存放到/etc/shadow文件中,保证我们密码的安全性!

```tex
[root@wbm2073568608 ~]# cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
[root@wbm2073568608 ~]# cat /etc/shadow
// 被加密的密码
root:$6$MrChgUE8$MPdCWBGdK9ywBq7ZvzImHdX6n33EqcXpRHC/zw0eoCbK4O6S8RYQJP0mfbQKVB8w9XXBciD9EKLPC.3MBpoD./:19027:0:99999:7:::
bin:*:17834:0:99999:7:::
daemon:*:17834:0:99999:7:::
adm:*:17834:0:99999:7:::
lp:*:17834:0:99999:7:::
sync:*:17834:0:99999:7:::
shutdown:*:17834:0:99999:7:::
halt:*:17834:0:99999:7:::
mail:*:17834:0:99999:7:::
operator:*:17834:0:99999:7:::
games:*:17834:0:99999:7:::
ftp:*:17834:0:99999:7:::
nobody:*:17834:0:99999:7:::
systemd-network:!!:18378::::::
dbus:!!:18378::::::
polkitd:!!:18378::::::
sshd:!!:18378::::::
postfix:!!:18378::::::
chrony:!!:18378::::::
nscd:!!:18378::::::
tcpdump:!!:18378::::::
ntp:!!:19015::::::
www:!!:19015:0:99999:7:::
mysql:!!:19015:0:99999:7:::
redis:!!:19015:0:99999:7:::
springboot:!!:19015:0:99999:7:::
wbm:!!:19027:0:99999:7:::
wbmm:$6$bBO7Iqbi$JfKjF4yQ8uqZ6m/ImW/RW5ht4VY9JnRQkNNdrTcZbFmHb.KetR8Mkvfw8hrrSoln/NqjFYkAHEb/Mrr6H9wkh0:19027:0:99999:7:::
[root@wbm2073568608 ~]# ^C
[root@wbm2073568608 ~]# 

```



用户组的所有信息都存放在/etc/group文件中。

```tex
[root@wbm2073568608 ~]# cat /etc/group
root:x:0:
bin:x:1:
daemon:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mem:x:8:
kmem:x:9:
wheel:x:10:
cdrom:x:11:
mail:x:12:postfix
man:x:15:
dialout:x:18:
floppy:x:19:
games:x:20:
tape:x:33:
video:x:39:
ftp:x:50:
lock:x:54:
audio:x:63:
nobody:x:99:
users:x:100:
utmp:x:22:
utempter:x:35:
input:x:999:
systemd-journal:x:190:
systemd-network:x:192:
dbus:x:81:
polkitd:x:998:
ssh_keys:x:997:
sshd:x:74:
postdrop:x:90:
postfix:x:89:
chrony:x:996:
nscd:x:28:
tcpdump:x:72:
ntp:x:38:
www:x:1000:
mysql:x:1001:
cgred:x:995:
redis:x:1002:
springboot:x:1003:
wbm:x:1004:
wbmsyg:x:1006:
ggggg:x:555:

```



## 磁盘管理

> df(列出文件系统整体的磁盘使用量)   

![image-20220205144529240](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205144529240.png)



- df -h

  ![image-20220205144729448](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205144729448.png)

  





> du(检查磁盘空间使用量)

![image-20220205145146891](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205145146891.png)

- du -a (包括隐藏文件)

  ![image-20220205145224286](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205145224286.png)



- du -sm /* (检查根目录下每个目录所占用的容量)



Mac或者想使用Linux挂载我们的一些本地磁盘或者文件!

挂载：mount

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200703084513927.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29rRm9ycmVzdDI3,size_16,color_FFFFFF,t_70#pic_center)

卸载：umount-f [挂载位置] 强制卸载
除了这个之外，以后安装了JDK，可以使用Java命令查看信息



## 进程管理

> 什么是进程

1. 在Linux中 ,每一个程序都是有自己的一个进程,每一个进程都有一个id号!

2. 每一个进程呢,都会有一个父进程!

3. 进程可以有两种存在方式:前台!后台运行!

4. 一般的话服务都是后台运行的，基本的程序都是前台运行的

   

   > 命令

   ps 查看当前系统中正在执行的各种进程的信息！
   ps- xx：
     -a 显示当前终端所有的进程信息

   ![image-20220205150342959](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205150342959.png)

   

     -u 以用户的信息显示进程

   ![image-20220205150418259](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205150418259.png)

   

     -x 显示后台运行进程的参数



```tex
#ps -aux  查看所有进程
ps-aux|grep mysql  查看mysql相关进程
# | 在Linux中这个叫管道符   A|B
# grep 查找文件中符合条件的字符串
```



对于我们来说,这里目前只需要记住一个命令即可ps -xx|grep进程名字!过滤进程信息!
ps-ef ：可以查看到父进程的信息

```te
ps-ef|grep mysql 看父进程我们一般可以通过目录树结构来查看
#进程树
#pstree -pu
#-p 显示父id
#-u 显示用户组
```



结束进程：杀掉进程 等价于Windows结束任务

```text
kill -9 进程id  # 表示强制结束该进程
```



## 环境安装

安装软件一般有三种方式
 rpm（在线发布一个SpringBoot项目）
 解压缩
 yum在线安装

### JDK安装

1、下载IDK rpm。 去oralce官网下载即可!
2、安装java环境

```test
java -version 检测当前系统是否存在Java环境 和windows命令一样
#如果有的话就需要卸载
rpm -qa|grep jdk 查看JDK版本信息
rpm -e --nodeps jdk_ 卸载


[root@wbm2073568608 ~]# rpm -qa|grep jdk  # 如果 java -version查看有jdk版本, 那么先查看jdk版本信息
jdk1.8.0_121-1.8.0_121-fcs.x86_64   #显示jdk信息
[root@wbm2073568608 ~]# rpm -e --nodeps jdk1.8.0_121-1.8.0_121-fcs.x86_64 # (需要卸载的版本信息)
[root@wbm2073568608 ~]# java -version  #在次查看是否还有
-bash: java: 未找到命令   # 表示不存在jdk了


```



> 卸载完毕后可安装JDK

```tes
rpm -ivh rpm包 
```

![image-20220205154013197](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205154013197.png)

![image-20220205154038558](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205154038558.png)安装成功



> 配置环境变量: /etc/profile 在文件的最后面增加java的配置和window安装环境变量一样!

```tex
vim /etc/profile

在这里的最后面输入
JAVA_HOME=/usr/java/jdk-14.0.1
JRE_HOME=$JAVA_HOME/jre
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
export JAVA_HOME JRE_HOME PATH CLASSPATH
```



让这个配置文件生效!

````tex
    source /etc/profile
````



 狂神老师用的是阿里云，自带网络了，此处给用虚拟机的同学使用。虚拟机联网教程：[虚拟机和主机联网教程](https://blog.csdn.net/u012049667/article/details/81171003)
 配置完后在Linux防火墙中开启相应端口 使用java -jar发布 如果你的项目在云服务器上，就可以在公网上进行发布查看了

```tes
#开启防火墙端口
firewall-cmd --zone=public --add-port=9000/tcp --permanent  # 9000 表示开启 9000端口
#重启防火墙
systemctl restart firewalld.service
#查看所有开启的端口，如果是阿里云 需要配置安全组规则
firewall-cmd --list-ports


# 查看firewall服务状态
systemctl status firewalld
# 开启、重启、关闭、firewalld.service服务
# 开启
service firewalld start
# 重启
service firewalld restart
# 关闭
service firewalld stop
# 查看防火墙规则
firewall-cmd --list-all # 查看全部信息
firewall-cmd --list-ports # 只看端口信息
# 开启端口
开端口命令：firewall-cmd --zone=public --add-port=7777/tcp --permanent
重启防火墙：systemctl restart firewalld.service
命令含义：
--zone #作用域
--add-port=80/tcp #添加端口，格式为：端口/通讯协议
```

![image-20220205160615156](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205160615156.png)



> 发布一个项目试试

新建一个springboot 项目 写一个hello类

```java
package com.example.hello;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class Hello {

    @ResponseBody
    @RequestMapping("/hello")
    public String hello(){
        return "hello word";
    }
}

```

![image-20220205160752824](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205160752824.png)



![image-20220205160824356](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205160824356.png)



![image-20220205160912716](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205160912716.png)



最后在cmd测试是否成功



![image-20220205160959659](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205160959659.png)最后在服务器发布



### Tomcat安装

ssm war 就需要放在tomcat中运行
1.下载tomcat 官网下载即可
2.解压tar -zxvf apache-tomcat-9.0.36.tar.gz

![image-20220205162919722](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205162919722.png)

![image-20220205163005684](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205163005684.png)



3.启动tomcat

````tex
#执行 
./startup.sh
#停止
./shutdown.sh
````



```tes
[root@wbm2073568608 ~]# cd /home/wbm
[root@wbm2073568608 wbm]# cd apache-tomcat-9.0.58
[root@wbm2073568608 apache-tomcat-9.0.58]# cd bin/
[root@wbm2073568608 bin]# ./startup.sh   #在bin目录执行
Using CATALINA_BASE:   /home/wbm/apache-tomcat-9.0.58
Using CATALINA_HOME:   /home/wbm/apache-tomcat-9.0.58
Using CATALINA_TMPDIR: /home/wbm/apache-tomcat-9.0.58/temp
Using JRE_HOME:        /usr/java/jdk1.8.0_131/jre
Using CLASSPATH:       /home/wbm/apache-tomcat-9.0.58/bin/bootstrap.jar:/home/wbm/apache-tomcat-9.0.58/bin/tomcat-juli.jar
Using CATALINA_OPTS:   
Tomcat started.
[root@wbm2073568608 bin]# 

```

命令含义:
 --zone 作用域
 --add-port-80/tcp 添加端口， 格式为:端口/通讯协议
 --permanent 永久生效，没有此参数重启后失效

 如果是阿里云 上传完毕的项目直接购买自己的域名,备案解析过去即可!
 域名解析后,如果端口是80 - http或者443-https 可以直接访问,如果是9000 8080 ,就需要通过Apcahe或者Nginx做一下反向代理即可（配置文件）



如果安装了宝塔需要进入宝塔放行端口

![image-20220205165239099](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205165239099.png)





### Docker（yum安装）

1.检测CentOS 7

```test
cat /etc/redhat-release
```

![image-20220205165706683](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205165706683.png)





2.安装我们的准备环境

```test
yum -y install 包名
#yum install 安装命令 -y  所有的提示都为y


yum -y install gcc  
yum -y install gcc-c++
```

![image-20220205170508473](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205170508473.png)



![image-20220205170537960](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205170537960.png)

3.卸载以前的docker

```test
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

![image-20220205165926002](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205165926002.png)因为没有下载



4.下载环境

```test
yum install -y yum-utils \device-mapper-persistent-data \lvm2
```

![image-20220205171049374](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205171049374.png)

5.使用国内阿里云镜像

```test
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

![image-20220205171117672](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205171117672.png)

6.更新yum软件包安装

```test
yum makecache fast
```

![image-20220205171154698](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220205171154698.png)

7.安装docker ce

```test
yum -y install docker-ce docker-ce-Cli containerd.io
```



8.启动docker

```test
systemctl start docker
```



9.测试

```test
docker version
docker run hello-world
docker images
```









