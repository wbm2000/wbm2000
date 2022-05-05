# NoSql 概述

## 为什么要用NoSql

先从历史开始讲吧

> 1、单机数据库时代

![image-20220208130521307](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220208130521307.png)

90年代, 一个基本的网站访问量一般不会太大, 单个数据库完成足够的

那个时候, 更多的去使用静态网页 HTML 服务器根本没有太大的压力!

那么 , 在这种情况下 : 整个网站的瓶颈是什么?

1. 数据量如果太大, 一个机器放不下了
2. 数据的索引 (B+ Tree), 一个机器内存也放不下
3. 访问量 (读写混合) , 一个服务器承受不了

只要开始出现以上的情况之一, 那么久必须要晋级了 !



> 2 . Memcached (缓存) + MySQL + 垂直拆分(读写分离)

网站80%的情况下都是在读, 每次都要去查询数据库的话就十分的麻烦 ! 

所以说我们希望减轻数据的压力, 我们可以使用缓存来保证效率 !

发展过程 : 优化数据结构和索引-->文件缓存(IO)---> MemCached (以前最热门的技术)

![image-20220208134342072](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220208134342072.png)





> 3 . 分库分表 + 水平拆分 + MySQL集群

技术和业务在发展的同时, 对人的要求也越来越高!

`本质 : 数据库(读 , 写)`

早些年是使用 MyISAM : 表锁, 十分影响效率 ! 高并发下就会出现严重的锁问题

现在使用的是 Innodb : 行锁

慢慢的就开始使用分库分表来解决写的压力 ! MySQL在那个年代推出了表分区! 这个并没有多少公司使用! 

MySQL 的 集群 , 很好满足那个年代的需求!

![image-20220208140127757](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220208140127757.png)



> 4 . 如今最近的年代

这十年之间, 世界已经发生了翻天覆地的变化 (定位, 也是一种数据, 音乐 .....)

MySQL 等关系型数据库就不够用了 ! 数据量很多, 变化很快 !

MySQL 有的使用它来储存一些比较大的文件, 博客, 图片 ! 数据库表很大, 效率就低了 ! 如果有一种数据库来专门处理这种数据, MySQL压力就会变得十分小( 研究如何处理这些问题! ) 大数据的IO压力下, 表几乎没法更大



> 目前一个基本的互联网项目!

![image-20220209133544614](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220209133544614.png)





> 为什么要用NoSql !

用户的个人信息, 社交网络, 地理位置. 用户自己产生的数据, 用户日志等等爆发式增长!

这时候我们就需要使用NoSQL数据库了, NoSQL 可以很好的处理以上的情况 !



## 什么是NoSQL

> NoSQL

NoSQL = Not Only SQL (不仅仅是SQL)

关系型数据库 : 表格, 行, 列

NoSQL 泛指非关系型数据库, 随着 Web2.0互联网的诞生, 传统的关系型数据库很难对付web2.0时代, 尤其是超大规模的高并发的社区 ! 暴露出来很多难以克服的问题, NoSQL在当今大数据环境下发展的十分迅速, Redis是发展最快的, 而且是我吗当下必须要掌握的一个技术!

很多的数据类型用户的个人信息, 社交网络, 地理位置. 这些数据类型的存储不需要一个固定的格式 ! 不需要多余的操作就可以横向扩展 !        Map<String, Object> 使用键值对来控制 !



> NoSQL 特点

1. 方便扩展 (数据之间没有关系, 很好扩展! )

2. 大数据量高性能(Redis 一秒写8万次, 读取11万, NoSQL的缓存记录级, 是一种微粒度的缓存, 性能会比较高)

3. 数据类型是多样性的 ! (不需要事先设计数据库 ! 随取随用 ! 如果是数据量十分大的表, 很多人就无法设计了)

4. 传统 RDBMS 和NoSQL

   ```test
   传统的 RDBMS
   - 结构化组织
   - SQL
   - 数据和关系都存在单独的表中 row col
   - 数据操作, 数据定义语言
   - 严格的一致性
   - 基础的事务
   - ...
   ```

   ```test
   NoSQL
   - 不仅仅是数据
   - 没有固定的查询语言
   - 键值对存储, 列存储, 文档存储, 图形数据库(社交关系)
   - 最终一致性
   - CAP定理 和 BASE  (异地多活)
   - 高性能, 高可用, 高可扩
   - ....
   ```

   



> 3v+3高 (了解)

大数据时代的3v : 主要是描述问题的

1. 海量（Volume）
2. 多样（Variety）
3. 实时（Velocity）



大数据时代的3高 : 主要是对程序的要求

1. 高并发
2. 高可扩 (随时水平拆分 , 机器不够了, 可以扩展机器)
3. 高性能 (保证用户体验和性能)



真正在公司中的实践 :NoSQL + RDBMS 一起使用才是最强的



## 阿里巴巴演进分析

这么多东西难道都是在一个数据库中的吗?

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220209142111239.png" alt="image-20220209142111239" style="zoom:40%;" />



![在这里插入图片描述](https://img-blog.csdnimg.cn/20201119122135351.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQ2ODQ3NA==,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201119122214516.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQ2ODQ3NA==,size_16,color_FFFFFF,t_70#pic_center)



没有什么是加一层解决不了的，如果有，就加两层

```test
# 商品的基本信息
名称、价格、商家信息
MySQL / Oracle 去IOE化（IOE：IBM、Oracle、EMC存储设备）

# 商品描述
评论，文本信息多
文档型数据库，MongoDB

# 图片
分布式文件系统 FastDFS
淘宝：TFS
Google：GFS
Hadoop：HDFS
阿里云：OSS

# 商品关键字（搜索）
搜索引擎 solr elasticsearch
淘宝：ISearch，ISearch作者，阿里的多隆

# 商品热门波段信息
内存数据库
Redis  Tair  Memcached...

# 商品交易，外部支付接口
第三方应用
```

大型互联网应用

- 数据类型多样！
- 数据源多样，频繁重构！
- 数据改造，大面积改动



解决问题

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201119122243761.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQ2ODQ3NA==,size_16,color_FFFFFF,t_70#pic_center)



热点缓存

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201119122302616.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQ2ODQ3NA==,size_16,color_FFFFFF,t_70#pic_center)









## NoSQL的四大分类

**KV键值对:**

- 新浪 : Redis
- 美团 : Redis + Tair
- 阿里, 百度 : Redis + memeache



**文档型数据库(bson格式 和 json 一样)**

- MongoDB(一般必须要掌握)
  - MongoDB 是一个基于分布式文件存储的数据库, C++编写的, 主要用来处理大量的文档!
  - MongoDB 是一个介于关系型数据库和非关系型数据库中 中间的产品! MongoDB 是非关系型数据库中功能最丰富, 最像关系型数据库的 ! 
- ConthDB



**列存储数据库**

- HBase
- 分布式文件系统



**图关系数据库**

- 它不是存图片的！它存放的是关系，就好比一个人的社交圈，可以动态扩充
- Neo4j，InfoGrid



> 4种分类的对比

![img](https://img-blog.csdnimg.cn/20201119122339567.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQ2ODQ3NA==,size_16,color_FFFFFF,t_70#pic_center)





# Redis入门

## 概述

> Redis 是什么?

Redis（==Re==mote ==Di==ctionary ==S==erver )，即远程字典服务

是一个开源的使用ANSI ==C语言== 编写、支持网络、可基于内存亦可持久化的日志型、Key-Value[数据库](https://baike.baidu.com/item/数据库/103728)，并提供多种语言的API。

![image-20220209152211992](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220209152211992.png)

redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件，并且在此基础上实现了master-slave(主从)同步。

免费和开源 ! 是当下最热门的NoSQL 技术之一 ! 也被人们称之为结构化数据库 !



> Redis 能干嘛 ?

1. 内存存储, 持久化, 内存中是断电即失, 所以说持久化很重要 (rdb, aof)
2. 效率高, 可以用于高速缓存
3. 发布订阅系统
4. 地图信息分析
5. 计时器, 计数器(浏览量)
6. ......



> Redis 特性

1. 多样的数据类型
2. 持久性
3. 集群
4. 事务
5. ....



> 学习中需要的东西

1. 官网 : https://redis.io/

2. 中文网 : https://www.redis.net.cn/

3. 下载地址 : 通过官网下载

   ![image-20220209153057920](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220209153057920.png)

注意 : Wdinow 在GitHub下载, (停更很久了)

==Redis推荐都是在Linux服务器搭建的, 我们是基于Linux学习的==





## Windows安装

1. 下载安装包 : https://github.com/microsoftarchive/redis/releases

2. 下载完毕得到压缩包 :

   ![image-20220209160058197](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220209160058197.png)

3. 解压到自己电脑上的环境目录下 就可以了

   ![image-20220209160643165](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220209160643165.png)

4. 开启Redis, 双击运行服务即可!

   ![image-20220209160923942](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220209160923942.png)

5. 使用redis客户端来链接redis

   ![image-20220209161344356](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220209161344356.png)

   windows下使用确实简单, 但是Redis推荐我们使用Linux去开发使用















## Linux安装

1. 下载安装包

   ![image-20220210153114820](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220210153114820.png)

2. 解压文件

   

![image-20220210153851359](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220210153851359.png)



3. 进入解压后的文件, 可以看到Redis的配置文件

   ![image-20220210191620790](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220210191620790.png)

4. 基本的环境安装 ==yum install gcc-c++==   

   ![image-20220210191844943](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220210191844943.png)

   ​             

   

5. 因为redis-5 以上要使用 gcc 5.3以上版本进行编译, 但是centos 7 默认安装的gcc版本是4.8.5, 所以需要升级gcc版本

   ![image-20220211101531590](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211101531590.png)



6. 升级gcc的操作

   ```tes
   # 升级到gcc 9.3：
   yum -y install centos-release-scl
   yum -y install devtoolset-9-gcc devtoolset-9-gcc-c++ devtoolset-9-binutils
   scl enable devtoolset-9 bash
   # 需要注意的是scl命令启用只是临时的，退出shell或重启就会恢复原系统gcc版本。
   
   # 如果要长期使用gcc 9.3的话：
   echo -e "\nsource /opt/rh/devtoolset-9/enable" >>/etc/profile
   ```

   ![image-20220211102400001](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211102400001.png)



7. 安装redis

   下载安装

   ```tes
   # 解压安装包
   tar -zxvf 包
   
   # 进入安装包
   cd redis-6.2.5/
   
   # 编译和安装
   make && make test && make install
   ```

   安装出错的话执行：

   ```tes
   # 编译出错时，清出编译生成的文件
   make distclean
   
   # 卸载
   make uninstall
   ```



8. 配置

   - 将服务端脚本和客户端脚本移动到新建的文件夹下面

     ```tes
     # 在安装目录下创建一个 bin 目录
     [root@node01 redis-6.2.5]# mkdir bin
     [root@node01 redis-6.2.5]# cd src/
     
     # 将 redis-server 和 redis-cli 移动到 bin 目录中
     [root@node01 src]# cp redis-server ../bin/
     [root@node01 src]# cp redis-cli ../bin/
     
     
     # 将 redis 的配置文件 redis.conf 移动到 bin 目录下
     [root@node01 redis-6.2.5]# cp redis.conf bin/
     [root@node01 redis-6.2.5]# cd bin/
     ```

   - 配置redis.conf 文件

     ```tes
     # 修改配置文件，修改的内容在下面
     vim redis.conf
     
     # 设置可以访问redis服务的IP
     bind 0.0.0.0
     
     # 设置redis的访问端口
     port 6379
     
     # 设置访问redis的密码
     requirepass 123456
     
     # 设置 redis-server 以守护线程方式启动
     daemonize yes
     ```

     

9. 启动redis

   ```tes
   [root@node01 bin]# ./redis-server redis.conf 
   [root@node01 bin]# ./redis-cli 
   ```

   ![image-20220211110959353](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211110959353.png)

   ![image-20220211123846514](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211123846514.png)

10. 查看redis的进程是否开启!  ==ps -ef|grep redis==

    ![image-20220211124157180](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211124157180.png)

11. 关闭Redis服务 ==shutdown==

    ![image-20220211124439670](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211124439670.png)

12. 在次查看进程是否存在

    ![image-20220211124639455](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211124639455.png)





## 测试性能

**redis-benchmark**是一个压力测试工具

官方自带的性能测试工具

redis-benchmark 命令参数!

![img](https://images2017.cnblogs.com/blog/707331/201802/707331-20180201145503750-901697180.png)

我们来简单测试下 :

```bash
# 测试 : 100个并发链接  10万个请求
redis-benchmark -h localhost -p 6379 -c 100 -n 1000000
```

![image-20220211155633812](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211155633812.png)

如何查看这些分析呢

![image-20220211160503565](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211160503565.png)





## 基础的知识

redis默认有16个数据库  查看==vim redis.conf==

![image-20220211161154364](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211161154364.png)

默认使用的是第0个数据库

可以使用select进行切换数据库!

```bash
127.0.0.1:6379> select 3  # 切换数据库
OK

127.0.0.1:6379[3]> DBSIZE # 查看数据库大小
(integer) 0

127.0.0.1:6379[3]> set wbn wbm  # 添加一个数据
OK

127.0.0.1:6379[3]> DBSIZE  
(integer) 1  # 可以看到数据库的大小变成了 1


127.0.0.1:6379> select 8  # 切换到第8个数据库
OK
127.0.0.1:6379[8]> DBSIZE 
(integer) 0   # 没有东西
127.0.0.1:6379[8]> get wbn # 也获取不到 3号数据库的东西
(nil)
127.0.0.1:6379[8]> select 3  # 重新回到 3号数据库
OK
127.0.0.1:6379[3]> get wbn  # get刚才添加的 
"wbm"    


```



清空当前数据库 ==FLUSHDB==

```bash
127.0.0.1:6379[3]> keys * # 查看所有的key
1) "wbn"

127.0.0.1:6379[3]> FLUSHdb  # 清除当前数据库
OK
127.0.0.1:6379[3]> keys *  # 可以看到没有key
(empty array)
```



清空所有数据库 ==FLUSHALL==

```bash
127.0.0.1:6379> keys *   # 查看0数据库的所有key
1) "key:__rand_int__"
2) "name"
3) "wbm"
4) "counter:__rand_int__"
5) "mylist"

127.0.0.1:6379> select 3  # 切换到3数据库 
OK

127.0.0.1:6379[3]> FLUSHALL # 清除所有数据库
OK

127.0.0.1:6379[3]> select 0 # 切换到0数据库
OK

127.0.0.1:6379> keys * # 可以看到没了
(empty array)


```



思考: 为什么redis端口号是6379



> 4.0之前 Redis 是单线程的 !  

Redis是很快的, 官方表示, Redis是基于内存操作, 多线程是靠CPU的, 但是Redis是单线程的, 所以CPU不是Redis性能瓶颈, Redis的瓶颈是根据机器的内存和网络带宽, 既然可以使用单线程来实现, 就使用单线程了!

Redis 是 C语言写的, 官方提供的数据为 100000+ 的QPS, 完全不比同样是使用 key-vale 的Memecache差



**Redis 为什么单线程还这么快 ?**

1. 误区1 : 高性能的服务器一定是多线程的
2. 误区2: 多线程(cpu 上下文切换 会耗时间的) 一定比单线程效率高 !

cpu>内存>硬盘

核心 : redis 是将所有的数据全部放在内存中的, 所以说使用单线程去操作效率是很高的, 多线程, 对于内存系统来说, 如果没有上下文切换效率是最高的 ! 多次读写都是在一个CPU上的, 在内存情况下, 这个就是最佳的方案 ! 



> Redis 不仅仅是单线程

一般来说 Redis 的瓶颈并不在 CPU，而在内存和网络。如果要使用 CPU 多核，可以搭建多个 Redis 实例来解决。

其实，Redis 4.0 开始就有多线程的概念了，比如 Redis 通过多线程方式在后台删除对象、以及通过 Redis 模块实现的阻塞命令等。



> redis 6.0  以后 

Redis 6 正式发布了，其中有一个是被说了很久的多线程IO： Redis 6.0 网络处理多线程



> 为什么网络处理要引入多线程？

之前的段落说了，Redis 的瓶颈并不在 CPU，而在内存和网络。

内存不够的话，可以加内存或者做数据结构优化和其他优化等，但网络的性能优化才是大头，网络 IO 的读写在 Redis 整个执行期间占用了大部分的 CPU 时间，如果把网络处理这部分做成多线程处理方式，那对整个 Redis 的性能会有很大的提升。







# 五大数据类型

官网文档

![image-20220211170921880](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220211170921880.png)



## Redis-Key

> 判断 键(key) 是否存在 ==exists 要判断的key==

```bash
127.0.0.1:6379> keys *
(empty array)

127.0.0.1:6379> set wbm wbm
OK

127.0.0.1:6379> get wbm
"wbm"

127.0.0.1:6379> set qq qq
OK

127.0.0.1:6379> keys *
1) "qq"
2) "wbm"

127.0.0.1:6379> exists wbn # 是否存在wbn 的 key   0表示不存在 1表示存在
(integer) 0
127.0.0.1:6379> exists wbm
(integer) 1

```



> 清除 某个key ==move key 1==   1表示当前数据库

```bash
127.0.0.1:6379> keys *
1) "qq"
2) "wbm"

127.0.0.1:6379> move qq 1 # 清除 qq这个key
(integer) 1     # 返回1 表示清除成功

127.0.0.1:6379> keys *
1) "wbm"
```



>  设置n秒以后清除 key     ==EXPIRE key  设置秒数==     可以使用 ==ttl key==  查看key失效的时间

```bash
127.0.0.1:6379> set qwbm 123456
OK

127.0.0.1:6379> keys *
1) "wbm"
2) "qwbm"

127.0.0.1:6379> get qwbm
"123456"

127.0.0.1:6379> EXPIRE qwbm 10 # 设置 qwbm 在10秒以后失效
(integer) 1

127.0.0.1:6379> TTL qwbm  # ttl key 可以查看key在几秒失效
(integer) 1         

127.0.0.1:6379> TTL qwbm # 返回 -2 表示已经失效
(integer) -2

127.0.0.1:6379> get qwbm  # 可以看到没了
(nil)

```



> 查看 key的value 是什么类型的  ==type key== 

```bash
127.0.0.1:6379> type wbm
string
127.0.0.1:6379> set www 123456
OK
127.0.0.1:6379> type www
string
```





## String(字符串)

在原有的value值的后面添加字符  ==APPEND key value==  如果往不存在的 key 放值, 他会自动set这个key

```bash
127.0.0.1:6379> set wbm wbm  # 添加一个 key 
OK
127.0.0.1:6379> get wbm
"wbm"
127.0.0.1:6379> APPEND wbm "207356"  # 往 key 添加字符
(integer) 9
127.0.0.1:6379> get wbm
"wbm207356"


127.0.0.1:6379> keys * # 可以看到这里不存在www 这个key
1) "wbm"
2) "key1"

127.0.0.1:6379> APPEND www "www" 
(integer) 3

127.0.0.1:6379> keys *  
1) "www"
2) "wbm"
3) "key1"

```





查看字符串有多少 ==STRLEN key==

```bash
127.0.0.1:6379> STRLEN wbm
(integer) 9
```



i++的操作  ==incr key==

```bash
127.0.0.1:6379> set views 0   # 设置 views 的值为0
OK
127.0.0.1:6379> get views    # 查看 
"0"
127.0.0.1:6379> incr views   
(integer) 1

127.0.0.1:6379> incr views
(integer) 2

127.0.0.1:6379> get views
"2"

```



i--的操作 ==decr key==

```bash
127.0.0.1:6379> get views  # 一开始的值
"2"
127.0.0.1:6379> decr views
(integer) 1

127.0.0.1:6379> decr views
(integer) 0

127.0.0.1:6379> decr views
(integer) -1

127.0.0.1:6379> decr views
(integer) -2

127.0.0.1:6379> get views  # 最后的值变成 -2
"-2"
```





i+多 ==incrby key 设置一次增加多少值==

```bash
127.0.0.1:6379> get views
"198" 

127.0.0.1:6379> incrby views 100
(integer) 298

127.0.0.1:6379> incrby views 100
(integer) 398

127.0.0.1:6379> get views
"398"

```



i-多 ==decrby key 设置一次减少多少值==

```bash
127.0.0.1:6379> get views
"398"
127.0.0.1:6379> decrby views 100
(integer) 298

```





截取某一段字符 ==GETRANGE  key  从什么下标开始  从什么下标结束==

```bash
127.0.0.1:6379> keys *
(empty array)

127.0.0.1:6379> set key1 "hello wbm"
OK

127.0.0.1:6379> GETRANGE key1 0 3
"hell"

127.0.0.1:6379> GETRANGE key1 0 -1  # 0到-1 表示截取全部字符串
"hello wbm"

```



替换某个字符串 ==setrange key 1(什么位置开始)  xx(替换什么)==

```bash
127.0.0.1:6379> set key2 abcdefg
OK

127.0.0.1:6379> get key2
"abcdefg"

127.0.0.1:6379> setrange key2 1 xx
(integer) 7

127.0.0.1:6379> get key2
"axxdefg"

```



set 一个key 并且设置过期时间 ==setex key3 30(单位秒) "hello"==

```bash
127.0.0.1:6379> setex key3 30 "hello"
OK
127.0.0.1:6379> TTL key3
(integer) 18
127.0.0.1:6379> TTL key3
(integer) 15
127.0.0.1:6379> TTL key3
(integer) 7
127.0.0.1:6379> get key3
(nil)

```



判断是否有这个key, 如果有这个key就不在新建, 如果不存在就创建一个 ==setnx my "redis"== 如果返回1 表示创建成功, 如果返回0表示创建失败

```bash
127.0.0.1:6379> setnx my "redis"
(integer) 1
127.0.0.1:6379> get my
"redis"
127.0.0.1:6379> setnx my "redis"
(integer) 0
```





创建多个key  ==mset key vlues key vlues ...==

```bash
127.0.0.1:6379> keys *
(empty array)

127.0.0.1:6379> mset k1 123 k2 345 k3 678
OK

127.0.0.1:6379> keys *
1) "k3"
2) "k1"
3) "k2"

```



获取多个key值 ==mget key key...==

```bash
127.0.0.1:6379> mget k1 k2 k3
1) "123"
2) "345"
3) "678"
```



==msetnx== 的意思是 可以设置多个key 并且会判断他是否存在, 重点是, 其中一个存在, 他就会创建失败

msetnx 是一个原子性的操作, 要么同时成功, 要么同时失败

```bash
127.0.0.1:6379> keys *
1) "k3"
2) "k1"
3) "k2"

127.0.0.1:6379> msetnx k1 tt k4 22  # 可以看到 k4是不存在的, 但是返回0, 表示创建失败
(integer) 0

127.0.0.1:6379> keys *
1) "k3"
2) "k1"
3) "k2"

```



实战中可以这样使用

```bash
set user:1 {name:wbm,age:3} # 设置一个user:1 对象 值为 json字符来保存一个对象 !

127.0.0.1:6379> mset user:1:name wbm user:1:age 2
OK
127.0.0.1:6379> keys *
1) "k1"
2) "k3"
3) "user:1:name"
4) "user:1:age"
5) "k2"

```



先get在set, ==getset key vlues== 如果这个key不存在就创建

```bash
127.0.0.1:6379> getset db redis  
(nil) # 表示db不存在
127.0.0.1:6379> get db  # 如果不存在就会创建
"redis"
127.0.0.1:6379> getset db db # 存在就返回vlues , 并且修改为当前设置的vlues
"redis"
127.0.0.1:6379> get db
"db"
```





## List

基本的数据类型, 列表

![image-20220213183332172](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220213183332172.png)

在redis里面, 我们可以吧list玩成, 栈, 队列, 阻塞队列!

所有的list命令都是用  `l  `  开头的



### 添加

==lpush key value==  

```bash
127.0.0.1:6379> keys *
(empty array)

127.0.0.1:6379> lpush list one  # 将一个值或者多个值, 插入到列表的头部 (左)
(integer) 1

127.0.0.1:6379> lpush list two  
(integer) 2

127.0.0.1:6379> lpush list three
(integer) 3

127.0.0.1:6379> lrange list 0 -1   # 查看 0 到最后一个
1) "three"
2) "two"
3) "one"

# lpush 是往左添加, rpush 就是往右添加

127.0.0.1:6379> rpush list wbm   # 将一个值或者多个值, 插入到列表的尾部 (右)
(integer) 4

127.0.0.1:6379> lrange list 0 -1
1) "three"
2) "two"
3) "one"
4) "wbm"

```



### 移除

==lpop 移除左边的第一个, 或者说头部==

==rpop 右 尾部==

```bash
127.0.0.1:6379> lrange list 0 -1  # 查看list的所有元素
1) "three"
2) "two"
3) "one"
4) "wbm"

127.0.0.1:6379> lpop list  # 移除头部的第一个, 并且返回被删除的元素
"three"

127.0.0.1:6379> lrange list 0 -1 # 可以看到 元素1 three被删除了
1) "two"
2) "one"
3) "wbm"

127.0.0.1:6379> rpop list # 移除尾部的第一个, 并且返回被删除的元素
"wbm"

127.0.0.1:6379> lrange list 0 -1
1) "two"
2) "one"

```





### 获取 Lis类型 的 key 的某一个元素

==lindex key 要获取元素的下标==

```bash
127.0.0.1:6379> lrange list 0 -1
1) "two"
2) "one"

127.0.0.1:6379> lindex list 0  # 获取 下标0
"two"

127.0.0.1:6379> lindex list 1  # 获取 下标1
"one"

127.0.0.1:6379> lindex list 2 # 不存在返回nil
(nil)

```



### 返回列表的长度

==llen key==

```bash
127.0.0.1:6379> lpush key one two three  # 创建 
(integer) 3
127.0.0.1:6379> llen key
(integer) 3

```





### 移除指定的值

```bash
127.0.0.1:6379> lrange key 0 -1
1) "one"
2) "thow"
3) "thow"
4) "three"
5) "two"

127.0.0.1:6379> lrem key 1 one  # 删除 1 个 one元素
(integer) 1

127.0.0.1:6379> lrem key 2 thow # 因为有两个 thow元素, 这里的2 表示删除 2个thow元素
(integer) 2

127.0.0.1:6379> lrange key 0 -1
1) "three"
2) "two"

```



截断

==ltrim==

```bash
127.0.0.1:6379> lpush list "h1"
(integer) 1

127.0.0.1:6379> lpush list "h2"
(integer) 2

127.0.0.1:6379> lpush list "h3"
(integer) 3

127.0.0.1:6379> lpush list "h4"
(integer) 4

127.0.0.1:6379> lrange list 0 -1
1) "h4"
2) "h3"
3) "h2"
4) "h1"

127.0.0.1:6379> ltrim list 1 2  # 所谓的截断的 参数就是保留下标几到几
OK
127.0.0.1:6379> lrange list 0 -1 # 上面的意思就是保留 1 到2的元素
1) "h3"
2) "h2"

```





### ==rpoplpush== 清除最后一个元素 , 并将他移动到另外一个表中

```bash
127.0.0.1:6379> lpush list "1" "2" "3" "4"
(integer) 4

127.0.0.1:6379> lrange list 0 -1 # 查看
1) "4"
2) "3"
3) "2"
4) "1"

127.0.0.1:6379> rpoplpush list list2 # 删除最后一个元素, 并且把他复制到 list2表中 , 如果list2表不存在就自动创建
"1"

127.0.0.1:6379> lrange list 0 -1  # 少了个1
1) "4"
2) "3"
3) "2"

127.0.0.1:6379> lrange list2 0 -1 # 1出现在 新表中
1) "1"

```



### 将列表中指定下标的值替换为另外一个值, 更新操作 ==lset key 下标 要修改的值==

```bash
127.0.0.1:6379> EXISTS list # 判断是否有 list 这个key
(integer) 0

127.0.0.1:6379> lset list 9 'wwww' # 修改 list 第9下标的值 改为www
(error) ERR no such key   # 报错因为没这个key

127.0.0.1:6379> lpush list '1'  # 添加 一个名为list的key 下标0位1
(integer) 1

127.0.0.1:6379> LRANGE list 0 -1  # 查看 lise的值
1) "1"

127.0.0.1:6379> lset list 0 '888888' # 修改 list 下标0的值 
OK

127.0.0.1:6379> lrange list 0 -1 # 可以看到成功
1) "888888"

127.0.0.1:6379> lset list 1 llll  # 如果下标不存在, 会报错
(error) ERR index out of range


```



### linsert 插入列表 

> 将某个具体的value插入到列表中的某个元素的前面或者后面

```bash
127.0.0.1:6379> rpush mylist "hello"
(integer) 1

127.0.0.1:6379> rpush mylist "word"
(integer) 2

127.0.0.1:6379> lrange mylist 0 -1
1) "hello"
2) "word"

127.0.0.1:6379> linsert mylist before 'word' '207' # before参数表示 往word的前面插入
(integer) 3
127.0.0.1:6379> lrange mylist 0 -1
1) "hello"
2) "207"
3) "word"
127.0.0.1:6379> linsert mylist after 'word' '356' # after 后面插入
(integer) 4
127.0.0.1:6379> lrange mylist 0 -1
1) "hello"
2) "207"
3) "word"
4) "356"

```



> ### List 小结

- 他实际上是一个链表, before Node after , left, right 都可以插入值
- 如果key 不存在, 创建新的链表
- 如果key存在, 新增内容
- 如果移除了所有值, 空链表, 也代表不存在
- 在两边插入或者改动值, 效率最高, 中间元素, 相对来说效率会低一点





## Set(集合)

set中的值是不能重复的

==sadd==

#### 添加操作, 还有判断元素是否存在

```bash
127.0.0.1:6379> sadd myset 'hello' # 如果不存在myset这个key 会自动创建, 并且赋值
(integer) 1    # 1表示成功

127.0.0.1:6379> sadd myset 'wbm' # 如果存在直接赋值
(integer) 1

127.0.0.1:6379> sadd myset '207356'
(integer) 1

127.0.0.1:6379> SMEMBERS myset
1) "207356"
2) "wbm"
3) "hello"

127.0.0.1:6379> SISMEMBER myset hello # 判断 key 是否有这个值
(integer) 1

127.0.0.1:6379> sismember myset woe # 如果不存在这个值 就返回0
(integer) 0

```



#### 查看set的key 有多少元素

```bash
127.0.0.1:6379> scard myset # 查看有多少元素
(integer) 3
127.0.0.1:6379> sadd myset 555 # 添加一个元素
(integer) 1 
127.0.0.1:6379> scard myset # 在次查看多少元素
(integer) 4

```



#### 在set中是不能重新重复的元素

```bash
127.0.0.1:6379> sadd myset 8887  # 成功
(integer) 1
127.0.0.1:6379> sadd myset 8887  # 失败
(integer) 0

```



#### 移除元素

==srem==

```bash
127.0.0.1:6379> SMEMBERS myset  # 查看set类型的元素
1) "hello"
2) "207356"
3) "555"
4) "wbm"
5) "8887"
127.0.0.1:6379> srem myset 555 # 移除 set类型的 某个值
(integer) 1   # 1 表示成功
127.0.0.1:6379> smembers myset # 可以看到555没了
1) "207356"
2) "hello"
3) "wbm"
4) "8887"

```



#### 随机

因为set集合是无序的

```bash
127.0.0.1:6379> SMEMBERS myset # 查看全部元素
1) "207356"
2) "hello"
3) "wbm"
4) "8887" 
127.0.0.1:6379> SRANDMEMBER myset  # 随机抽1个元素
"8887"
127.0.0.1:6379> SRANDMEMBER myset
"hello"
127.0.0.1:6379> SRANDMEMBER myset
"207356"
127.0.0.1:6379> SRANDMEMBER myset
"wbm"
127.0.0.1:6379> SRANDMEMBER myset 2  # 加个参数2 抽2个元素
1) "207356"
2) "8887"

```





#### 随机删除一个set类型的key

```bash
127.0.0.1:6379> SMEMBERS myset # 查看全部元素
1) "207356"
2) "hello"
3) "wbm"
4) "8887"

127.0.0.1:6379> spop myset #随机删除一个元素
"8887"
127.0.0.1:6379> spop myset #随机删除一个元素
"wbm"
127.0.0.1:6379> spop myset #随机删除一个元素
"hello"
127.0.0.1:6379> SMEMBERS myset # 可以看到最后只剩下一个元素了
1) "207356"

```





#### 将一个指定的元素,移动到另外一个key中

==smove 要被移动的key 目的地的key 要移动的元素==

```bash
127.0.0.1:6379> sadd myset hello
(integer) 1
127.0.0.1:6379> sadd myset wored
(integer) 1
127.0.0.1:6379> sadd myset 5888
(integer) 1
127.0.0.1:6379> sadd myset 99999
(integer) 1

127.0.0.1:6379> SMEMBERS myset
1) "99999"
2) "wored"
3) "5888"
4) "hello"

127.0.0.1:6379> sadd mysey2 207
(integer) 1

127.0.0.1:6379> smove myset myset2 5888
(integer) 1

127.0.0.1:6379> SMEMBERS myset2
1) "5888"

127.0.0.1:6379> smove myset myset2 hello
(integer) 1

127.0.0.1:6379> SMEMBERS myset2
1) "hello"
2) "5888"

127.0.0.1:6379> SMEMBERS myset
1) "99999"
2) "wored"

```



#### 查看1个set类型和另外一个的不交集部分

==sdiff key1 key2==

```bash
127.0.0.1:6379> sadd key1 a
(integer) 1

127.0.0.1:6379> sadd key1 b
(integer) 1

127.0.0.1:6379> sadd key1 c
(integer) 1

127.0.0.1:6379> sadd key2 c
(integer) 1

127.0.0.1:6379> sadd key2 d
(integer) 1

127.0.0.1:6379> sadd key2 e
(integer) 1

127.0.0.1:6379> sdiff key1 key2 # 查看key1 条件是key1和key2不交集的的元素 也就是不相同的元素
1) "a"
2) "b"

```



#### 交集部分

==SINTER key1 key2==   共同好友就可以这样实现

```bash
127.0.0.1:6379> SINTER key1 key2
1) "c"

```





#### 并集把两个或者多个set类型的key和起来, 把重复的变成一个

```bash
127.0.0.1:6379> SUNION key1 key2 # 两个key合起来
1) "a"
2) "b"
3) "c"
4) "d"
5) "e"
```





## Hash(哈希)

相当于一个Map集合, key<key-value>, 本质和string类型没有太大区别, 还是一个简单的 key- value

#### 创建和获取hash类型

```bash
27.0.0.1:6379> hset myhash key1 wbm  # 创建一个hash类型,名字myhash<key1-wbm>
(integer) 1
127.0.0.1:6379> hget myhash key1  # 获取hash的某个key的值
"wbm"
127.0.0.1:6379> hmset myhash key1 www key2 gggg key3 hhhh  # 创建多个hash类型, 如果这个key有了会被覆盖的
OK
127.0.0.1:6379> hmget myhash key1 key2 key3
1) "www"
2) "gggg"
3) "hhhh"
127.0.0.1:6379> hgetall myhash # 获取一个hash类型的全部key和value
1) "key1"
2) "www"
3) "key2"
4) "gggg"
5) "key3"
6) "hhhh"

```



#### 删除hash类型



> 删除某一个key-value

```bash
127.0.0.1:6379> hgetall myhash
1) "key1"
2) "www"
3) "key2"
4) "gggg"
5) "key3"
6) "hhhh"
127.0.0.1:6379> hdel myhash key1 # 删除myhash中的key,key1和他的value
(integer) 1
127.0.0.1:6379> hgetall myhash  # 可以看到key1和他的值没了
1) "key2"
2) "gggg"
3) "key3"
4) "hhhh"

```



#### 查看一个hash类型有多少键值对(key-value)

>hlen key

```bash
127.0.0.1:6379> hgetall myhash  # 查看全部键值对
1) "key2"
2) "gggg"
3) "key3"
4) "hhhh"

127.0.0.1:6379> hlen myhash #查看键值对有多少对
(integer) 2 
127.0.0.1:6379> hset myhash key55 55 # 添加一个键值对
(integer) 1
127.0.0.1:6379> hlen myhash # 可以看到变成3了
(integer) 3

```



判断hash类型有没有这个key

```bash
127.0.0.1:6379> hgetall myhash
1) "key2"
2) "gggg"
3) "key3"
4) "hhhh"
5) "key55"
6) "55"
127.0.0.1:6379> HEXISTS myhash key55
(integer) 1
127.0.0.1:6379> HEXISTS myhash key5
(integer) 0

```





#### 只查看hash类型的key或者value

> hkeys   key           hvals key

```bash
127.0.0.1:6379> hkeys myhash
1) "key2"
2) "key3"
3) "key55"
127.0.0.1:6379> hvals myhash
1) "gggg"
2) "hhhh"
3) "55"
```



#### hash类型的value i++

```bash
127.0.0.1:6379> hset myhash wbm3 5
(integer) 1
127.0.0.1:6379> HINCRBY myhash wbm3 1 # 加1
(integer) 6
127.0.0.1:6379> HINCRBY myhash wbm3 -1 # 加-1 可以当做 i--
(integer) 5

```



#### 如果这个key不存在就创建并且赋值, 如果这个key存在,就失败

```bash
127.0.0.1:6379> hsetnx myhash 5555 520
(integer) 1
127.0.0.1:6379> hsetnx myhash 5555 52
(integer) 0
```



可以这样用

一个user类 字段有id name age

```bash
127.0.0.1:6379> hset user:1: name wbm
(integer) 1
127.0.0.1:6379> hset user:1: age 15
(integer) 1
127.0.0.1:6379> hgetall user:1:
1) "name"
2) "wbm"
3) "age"
4) "15"

```





## Zset(有序集合)

在set的基础上, 增加了一个值, set k1 v1   zset k1 score1 v1 



#### 创建zset

```bash
127.0.0.1:6379> zadd myzset 1 one
(integer) 1
127.0.0.1:6379> zadd myzset 2 two
(integer) 1
127.0.0.1:6379> zadd myzset 3 three
(integer) 1

```



#### 查看zset

```bash
127.0.0.1:6379> ZRANge myzset 0 -1
1) "one"
2) "two"
3) "three"
```



#### zset排序

````bash
127.0.0.1:6379> zadd salary 2500 xh   # 设置xh 工资2500
(integer) 1
127.0.0.1:6379> zadd salary 3000 zs  # 设置zs 工资3000
(integer) 1
127.0.0.1:6379> zadd salary 500 wbm  # wbm 工资500
(integer) 1
127.0.0.1:6379> zadd salary 8000 wbb # wbb 工资8000
(integer) 1
127.0.0.1:6379> zrange salary 0 -1  # 查看
1) "wbm"
2) "xh"
3) "zs"
4) "wbb"
127.0.0.1:6379> ZRANGEBYSCORE salary -inf +inf  # 查看zset集合的工资 -inf(负无穷) +inf(正无穷) 意思就是工资从低到高
1) "wbm"    #从小到大
2) "xh"
3) "zs"
4) "wbb"
127.0.0.1:6379> ZRANGEBYSCORE salary -inf 2500 withscores # 负无穷到 2500  (withscores)并且把工资数查出来
1) "wbm"
2) "500"
3) "xh"
4) "2500"

127.0.0.1:6379> ZREVRANGE salary 0 -1 withscores  # 从大到小  withscores表示把工资数查出来
1) "wbb"
2) "8000"
3) "zs"
4) "3000"
5) "wbm"
6) "500"



````



#### 移除zset的元素

```bash
127.0.0.1:6379> zrange salary 0 -1  # 查看
1) "wbm"
2) "xh"
3) "zs"
4) "wbb"

127.0.0.1:6379> zrem salary xh  # 删除 xh这个元素
(integer) 1

127.0.0.1:6379> zrange salary 0 -1 # 再次查看发现没了
1) "wbm"
2) "zs"
3) "wbb"

```



#### 查看zset有多少元素

```bash
127.0.0.1:6379> zrange salary 0 -1
1) "wbm"
2) "zs"
3) "wbb"

127.0.0.1:6379> zcard salary
(integer) 3

```





#### 查看zset的区间值, 比如 1 和3的区间值

```bash
127.0.0.1:6379> zadd myset 1 hello
(integer) 1
127.0.0.1:6379> zadd myset 2 word
(integer) 1
127.0.0.1:6379> zadd myset 3 wbm
(integer) 1
127.0.0.1:6379> zadd myset 4 207356
(integer) 1

127.0.0.1:6379> ZCOUNT myset 1 2
(integer) 2
127.0.0.1:6379> ZCOUNT myset 1 4
(integer) 4

```



案例思路 : set 排序 存储班级成绩表  工资表排序

普通信息 1, 重要信息 2 , 带权重进行判断!

排行榜应用实现 



# 三种特殊数据类型

## geospatial (地理位置)

朋友的定位, 附近的人, 打车距离计算

Redis的Get  在Redis3.2版本就推出了 , 这个功能可以推算地理位置的信息, 两地之间的距离, 方圆几里的人

可以查询一些测试数据:http://www.jsons.cn/lngcode/

有10个命令

![image-20220215122550158](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220215122550158.png)



### getadd  添加位置

```bash
# getadd 添加一个位置
# 规则: 两级无法直接添加, 我们一般会下载城市数据, 直接通过java程序一次性导入!
# 参数 key 值( 经度 纬度 名字)
127.0.0.1:6379> geoadd china:city 116.40 39.90 bj # key 经度 纬度 名字
(integer) 1

127.0.0.1:6379> geoadd china:city 121.47 31.23 sh
(integer) 1

127.0.0.1:6379> geoadd china:city 106.50 29.53 cq
(integer) 1

127.0.0.1:6379> geoadd china:city 114.08 22.54 sz
(integer) 1


```



### geopos 获取指定的城市的经度纬度

```bash
127.0.0.1:6379> geopos china:city bj  # 获取北京的经度纬度
1) 1) "116.39999896287918091"
   2) "39.90000009167092543"
127.0.0.1:6379> geopos china:city bj cq  # 北京 重庆
1) 1) "116.39999896287918091"
   2) "39.90000009167092543"
2) 1) "106.49999767541885376"
   2) "29.52999957900659211"
127.0.0.1:6379> geopos china:city bj cq sh # 北京 重庆 上海
1) 1) "116.39999896287918091"
   2) "39.90000009167092543"
2) 1) "106.49999767541885376"
   2) "29.52999957900659211"
3) 1) "121.47000163793563843"
   2) "31.22999903975783553"

```



### Geodist 获取两人之间的距离

单位:

- m 表示单位为米
- km 表示单位为千米
- mi 表示单位为英里
- ft 表示单位为英尺

```bash
127.0.0.1:6379> geodist china:city bj cq m # 查看北京和重庆的距离 单位m
"1464070.8051"
127.0.0.1:6379> geodist china:city bj sh km # 查看北京和上海的距离 爹km
"1067.3788"

```





### georadius  以给定的经纬度为中心, 找出某一个半径内的元素

```bash
127.0.0.1:6379> georadius china:city 110 30 1000 km  # 在一个key中 经度 纬度 附近1000km的人
1) "cq"
2) "sz"
127.0.0.1:6379> georadius china:city 110 30 500 km # 500km的人
1) "cq"

127.0.0.1:6379> georadius china:city 110 30 1000 km withcoord
1) 1) "cq"
   2) 1) "106.49999767541885376"
      2) "29.52999957900659211"
2) 1) "sz"
   2) 1) "114.08000081777572632"
      2) "22.53999903789756587"


# count 限制  1 表示限制一个
127.0.0.1:6379> georadius china:city 110 30 1000 km withcoord count 1 
1) 1) "cq"
   2) 1) "106.49999767541885376"
      2) "29.52999957900659211"
      
# count 限制  2 表示限制二个
127.0.0.1:6379> georadius china:city 110 30 1000 km withcoord count 2
1) 1) "cq"
   2) 1) "106.49999767541885376"
      2) "29.52999957900659211"
2) 1) "sz"
   2) 1) "114.08000081777572632"
      2) "22.53999903789756587"




```



### georadiusbymember 就比如我附近1000米的城市有多少

````bash
127.0.0.1:6379> GEORADIUSBYMEMBER china:city bj 1000 km # 北京附近 1000 km 有多少个城市
1) "bj"
127.0.0.1:6379> GEORADIUSBYMEMBER china:city bj 10000 km # 10000km
1) "cq"
2) "sz"
3) "sh"
4) "bj"

````



### Geohash 命令 返回一个或多个位置元素的Geohash

该命令将返回11个字符的Genhash字符串!

```bash
127.0.0.1:6379> geohash china:city bj cq
1) "wx4fbxxfke0"
2) "wm5xzrybty0"

```



geo 底层的失效原理就是Zset ! 我们可以使用Zset命令来操作geo

```bash
127.0.0.1:6379> ZRANge china:city 0 -1
1) "cq"
2) "sz"
3) "sh"
4) "bj"
127.0.0.1:6379> ZRANge china:city 0 -1 withscores
1) "cq"
2) "4026042091628984"
3) "sz"
4) "4046432296800546"
5) "sh"
6) "4054803462927619"
7) "bj"
8) "4069885360207904"
127.0.0.1:6379> zrem china:city cq
(integer) 1
127.0.0.1:6379> ZRANge china:city 0 -1 withscores
1) "sz"
2) "4046432296800546"
3) "sh"
4) "4054803462927619"
5) "bj"
6) "4069885360207904"

```







## Hyperloglog

> 什么是基数?

A{1,3,5,7,8,7}

B{1,3,5,7,8,}

基数(不重复的元素) =5



> 简介

Redis2.8.9 版本就更新了Hyperloglog 数据结构

Redis Hyperloglog 基数统计的算法 !

==优点 : 占用的内存是固定, 2^64 不同的元素的技术,只需要浪费 12kb 的内存 如果要从内存角度来比较的话 Hyperloglog 是首选==

**就比如b站的播放量, 一个人访问一个视频多次, 但是还是算作一个人**

传统的方式, set 保存用户的id , 然后就可以统计set 中的元素数量作为标准判断 !

这个方式如果保存大量的用户id , 就会比较麻烦 , 我们的目的是为了计数, 而不是保存用户id

0.81%错误率 ! 统计uv任务, 可以忽略不计的



基本使用

```bash
127.0.0.1:6379> pfadd myset a b c d e f g h i j k  #创建一个Hyperloglog  值为 a b c d e f g h i j k
(integer) 1
127.0.0.1:6379> pfcount myset # 查看有多少 
(integer) 11
127.0.0.1:6379> 
127.0.0.1:6379> pfadd myset a b c d e f 3  # 可以看到这里有6个是同样的, 1个不存在的
(integer) 1
127.0.0.1:6379> pfcount myset  #在次查看 可以看到就加1了
(integer) 12

```



### 两个Hyperloglog 并集 为一个 Hyperloglog 

```bash
127.0.0.1:6379> pfadd myset a s d f g h j k l  # 创建第一组元素
(integer) 1
127.0.0.1:6379> PFCOUNT myset # 查看第一组有多少个元素
(integer) 9 


127.0.0.1:6379> pfadd myset1 q w d e r f g y j # 创建第二个
(integer) 1

127.0.0.1:6379> pfcount myset1
(integer) 9

127.0.0.1:6379> PFMERGE myset2 myset myset1 #合并两组 mykey mykey1 =>mykey2 并集
OK

127.0.0.1:6379> pfcount myset2
(integer) 14


```

如果允许容错, 那么一定可以使用 Hyperloglog !

如果不允许容错, 就使用 set 或者自己的数据类型即可 !





## Bitmaps

> 位存储

统计用户信息, 活跃 , 不活跃 ! 登录 , 未登录 ! 打卡.. 两个状态的, 都可以使用Bitmaps !

Bitmaps 位图, 数据结构 !都是操作二进制位进行记录, 就只有0和1两个状态 !

365天 = 365 bit 1字节=8bit  46个字节左右!



> 测试

使用bitmaps 来记录一周的打卡 0 表示打卡成功  1 迟到或者没打卡 

```bash
127.0.0.1:6379> setbit sign 0 1
(integer) 0
127.0.0.1:6379> setbit sign 1 0
(integer) 0
127.0.0.1:6379> setbit sign 2 1
(integer) 0
127.0.0.1:6379> setbit sign 3 1
(integer) 0
127.0.0.1:6379> setbit sign 4 0
(integer) 0
127.0.0.1:6379> setbit sign 5 0
(integer) 0
127.0.0.1:6379> setbit sign 6 1
(integer) 0

```



查看某一天是否有打卡

```bash
127.0.0.1:6379> getbit sign 7  # 不存在会返回0
(integer) 0
127.0.0.1:6379> getbit sign 6  
(integer) 1
127.0.0.1:6379> getbit sign 1
(integer) 0

```





查看打卡数

```bash
127.0.0.1:6379> bitcount sign  # 获取 为1的数量
(integer) 4

```





# 事务

Redis 事务本质 : 一组命令的集合 ! 一个事务中的所有命令都会被序列化, 在事务执行过程中, 会执行顺序执行 !

一次性, 顺序性, 排他性 ! 执行一些列的命令

==**Redis 单条命令是保存原子性的, 但是事务是不保证原子性的**==

==**Redis事务没有隔离级别的概念 !**==

所有的命令在事务中, 并没有直接被执行, 只有发起执行命令的时候才会执行



Redis的事务:

- 开启事务(multi)
- 命令入队()
- 执行事务( exec )



> 正常执行事务

```bash
127.0.0.1:6379> multi  # 开启事务
OK

# 命令入队
127.0.0.1:6379(TX)> set k1 v1   # 创建一个 k1的key
QUEUED                          # 表示在等等执行事务

127.0.0.1:6379(TX)> set k2 v2
QUEUED

127.0.0.1:6379(TX)> get k2
QUEUED

127.0.0.1:6379(TX)> set k3 v3
QUEUED

# 执行事务
127.0.0.1:6379(TX)> exec
1) OK
2) OK
3) "v2"
4) OK
```



> 放弃事务

```bash
127.0.0.1:6379> multi  # 开启事务
OK
# 命令入队
127.0.0.1:6379(TX)> set k1 v5
QUEUED
127.0.0.1:6379(TX)> set k8 88
QUEUED
# 放弃事务
127.0.0.1:6379(TX)> discard
OK
```



> 编译型异常 (代码有问题 ! 命令有错) , 事务中所有的命令都不会执行 !

```bash *
1) "k3"
2) "k1"
3) "k2"

127.0.0.1:6379> multi
OK

127.0.0.1:6379(TX)> set k1 m1
QUEUED

127.0.0.1:6379(TX)> set # 错误的命令
(error) ERR wrong number of arguments for 'set' command

127.0.0.1:6379(TX)> gg # 错误的命令
(error) ERR unknown command `gg`, with args beginning with: 

127.0.0.1:6379(TX)> set k2 m2
QUEUED

127.0.0.1:6379(TX)> set k8 55
QUEUED

127.0.0.1:6379(TX)> set k55 55
QUEUED

127.0.0.1:6379(TX)> EXEC  # 执行事务报错
(error) EXECABORT Transaction discarded because of previous errors.

127.0.0.1:6379> get k8   # 执行所有的命令都不会被执行
(nil)
```





> 运行时异常 (1/0), 如果事务队列中存在语法性, 那么执行命令的时候, 其他命令是可以正常执行的, 错误命令抛出异常

```bash
127.0.0.1:6379> set  k1 v1  # 设置k1的值为v1 
OK

127.0.0.1:6379> multi  # 开启事务
OK

# 命令入队
127.0.0.1:6379(TX)> incr k1 # 让k1 加1 但是k1是字符串, 所以这里是一定会报错的
QUEUED
127.0.0.1:6379(TX)> set k2 v2
QUEUED
127.0.0.1:6379(TX)> set k3 v2
QUEUED
127.0.0.1:6379(TX)> set k4 v2
QUEUED
127.0.0.1:6379(TX)> get k3
QUEUED

# 执行命令
127.0.0.1:6379(TX)> EXEC
1) (error) ERR value is not an integer or out of range   # 可以看到加1操作失败了, 但是其他依旧成功执行了
2) OK
3) OK
4) OK
5) "v2"

```



> 监控 ! Watch

**悲观锁** :

- 很悲观, 什么时候都会出问题, 无论做什么都会加锁 !

**乐观锁** :

- 很乐观, 以为什么时候都不会出问题, 所以不会上锁 !  更新的时候去判断一下, 在此期间是否有人修改过这个数据, 
- 获取 version
- 更新的时候比较  version



> Redis 监视测试

正常执行成功

```bash
127.0.0.1:6379> set m 100 # m 有100 块钱
OK
127.0.0.1:6379> set o 0  # m 花了 0块钱
0OK
127.0.0.1:6379> watch m # 监视 m 对象
OK
127.0.0.1:6379> multi  # 开启事务
OK
127.0.0.1:6379(TX)> decrby m 20  # m 减20
QUEUED
127.0.0.1:6379(TX)> INCRby 0 20 # 也就是m 花了20 这里加20
QUEUED
127.0.0.1:6379(TX)> EXEC
1) (integer) 80
2) (integer) 20

# 事务正常结束, 数据期间没有发生变动, 这个时候就正常执行成功
```



测试多线程修改值, 使用watch 可以当做redis的乐观锁操作

```bash
127.0.0.1:6379> watch m  # 监视 m
OK
127.0.0.1:6379> multi  # 开启事务
OK
# 命令入队
127.0.0.1:6379(TX)> decrby m 10
QUEUED
127.0.0.1:6379(TX)> INCRby o 10
QUEUED
# 还没执行的时候, 另外一条线程修改了我们的值, 这个时候, 就会导致事务执行失败
127.0.0.1:6379(TX)> EXEC
(nil)

```



> 如果执行失败, 就重新监视

```bash
127.0.0.1:6379> UNWATCH  # 如果监视过程中执行失败了必须先 解锁 解除监视
OK
127.0.0.1:6379> watch m  # 监视 m 
OK
127.0.0.1:6379> multi # 开启事务
OK
# 命令入队
127.0.0.1:6379(TX)> DECRby m 100
QUEUED
127.0.0.1:6379(TX)> incrby o 100
QUEUED
# 执行事务
127.0.0.1:6379(TX)> EXEC # 对比监控的值是否发生了变化, 如果没有变化, 那么可以执行, 如果有变化就执行失败
1) (integer) 900
2) (integer) 100

```





# Jedis

我们要使用java来操作Redis

> 什么是jedis 是Redis 官方推荐的 java链接开发工具 ! 使用java 操作 Redis中间价 ! 如果你要使用java操作redis, 那么一定要对 jedis 十分的熟悉 !



创建项目导入对应的依赖

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220217143749403.png" alt="image-20220217143749403" style="zoom:50%;" />



```xml
<!--导入 jedis的包-->
<dependencies>
    <dependency>
        <groupId>redis.clients</groupId>
        <artifactId>jedis</artifactId>
        <version>3.2.0</version>
    </dependency>

    <!--fastjson-->
    <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>fastjson</artifactId>
        <version>1.2.62</version>
    </dependency>
```



如果报

==Failed connecting to host 118.178.240.254:6379== 这个错

![在这里插入图片描述](https://img-blog.csdnimg.cn/8cfe6abd82c54e5ea27260ff85137d22.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rij5rij5p6X,size_20,color_FFFFFF,t_70,g_se,x_16)

> 编码测试

- 连接数据库
- 操作命令
- 断开连接



```java
public static void main(String[] args) {
    // 1. new jedis对象即可
    Jedis jedis = new Jedis("118.178.240.254", 6379);
    // jedis 所有的命令就是我们之前学习的所有指令
    System.out.println(jedis.ping());
}
```

输出:  PONG表示连接成功

![image-20220217145655638](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220217145655638.png)





## 常用的API

String

List

Set

Hash

Zest



## 事务

```java
public static void main(String[] args) {
    Jedis jedis = new Jedis("118.178.240.254",6379);
    JSONObject jsonObject = new JSONObject();
    jsonObject.put("hello","word");
    jsonObject.put("hello2","word");
    jsonObject.put("hello3","word");

    jedis.flushDB();
    String s = jsonObject.toJSONString();
    // 开启事务
    Transaction multi = jedis.multi();
    try {
        multi.set("kkk","5555");
        multi.set("gggg",s);
        int i= 1/0;  // 这里会抛出异常
        multi.exec();  // 执行事务
    } catch (Exception e) {
        multi.discard();   // 放弃事务
        e.printStackTrace();
    }finally {
        System.out.println(jedis.get("kkk"));
        System.out.println(jedis.get("gggg"));
        jedis.close();// 关闭链接
    }


}
```



# SpringBoot整合

SpringBoot 操作数据 : Spring-Data Jpa JDBC MongoDB Redis !

SpringData 也就是和 SpringBoot 其名的项目 !

说明 :在SpringBoot2.x之后, 原来使用的jedis 被替换为了 lettuce

jedis : 采用的直连, 多个线程操作的话, 是不安全的, 如果需要避免不安全的, 使用 jedis pook 连接池  

lettuce : 采用netty, 实例可以再多个线程中进行共享, 不存在线程不安全的情况 ! 可以减少线程数据了

源码分析 :

```java
// RedisAutoConfiguration 类

@Bean
@ConditionalOnMissingBean(name = {"redisTemplate"}) // 如果不存在redisTemplate才生效, 我们可以自定义一个
@ConditionalOnSingleCandidate(RedisConnectionFactory.class)
public RedisTemplate<Object, Object> redisTemplate(RedisConnectionFactory redisConnectionFactory) {
    // 默认的 RedisTemplate 没有过多的设置, redis 对象都是需要序列化的 ! 
    // 两个泛型 都是Object的类型, 我们后使用需要强制转换, <String, Object>
    RedisTemplate<Object, Object> template = new RedisTemplate();
    template.setConnectionFactory(redisConnectionFactory);
    return template;
}

@Bean
@ConditionalOnMissingBean  // 由于 String是Redis中最常用的类型, 所以说单独提出来了 一个bean
@ConditionalOnSingleCandidate(RedisConnectionFactory.class)
public StringRedisTemplate stringRedisTemplate(RedisConnectionFactory redisConnectionFactory) {
    StringRedisTemplate template = new StringRedisTemplate();
    template.setConnectionFactory(redisConnectionFactory);
    return template;
```

> 整合测试

1. 导入依赖
2. 配置链接

```properties
# SpringBoot 所有的配置类 都有一个自动配置类  RedisAutoConfiguration
# 自动配置类都会绑定一个 properties 配置文件 RedisProperties
# 配置Redis
spring.redis.host=118.178.240.254
spring.redis.port=6379
```

3. 测试

```java
@Autowired  // 注入 redis配置
private RedisTemplate redisTemplate;
 @Test
 void contextLoads() {

     // redisTemplate
     // opsForValue 操作字符串 类似String
     // opsForList 操作List
     // opsForSet 操作Set
     // opsForHash 操作Hash
     // opsForZset 操作Zset
     // opsForGeo 操作Geo

     // 除了基本的操作, 我们常用的方法都可以直接通过redisTemplate操作, 比如事务, 和基本的增删改查

    /* // 获取redis的链接对象
     RedisConnection connection = redisTemplate.getConnectionFactory().getConnection();
     connection.flushAll();
     connection.flushDb();*/


     redisTemplate.opsForValue().set("wbm","2073568608");
     System.out.println(redisTemplate.opsForValue().get("wbm"));
     System.out.println(redisTemplate.keys("*"));


 }
```



> 默认是使用jdk的序列化

![image-20220218124237611](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220218124237611.png)

![image-20220218124412289](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220218124412289.png)



> 如果直接set 对象这样是不行的不行先把 pojo类序列化 继承Serializable 接口

![image-20220218152914193](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220218152914193.png)

```java
@Component
@Data
@AllArgsConstructor
@NoArgsConstructor
// 在企业中, 我们的所有 pojo 都会序列化 !
public class User implements Serializable {

    private String name;
    private Integer age;
}



 @Test
     public void test() throws JsonProcessingException {
        // 真实开发 一般都使用json 来传递对象
        User user = new User("wbm", 18);
       // String s = new ObjectMapper().writeValueAsString(user);
        redisTemplate.opsForValue().set("wbm",user);
        System.out.println(redisTemplate.opsForValue().get("wbm"));
    }
```





> 使用其他的序列化方式, 我们来编写一个自己的 RedisTemplate

```java
@Configuration
public class RedisConfig {
    // 编写我们自己的redisTempLate
    /**
     * retemplate相关配置
     * @param factory
     * @return
     */
    @Bean
    public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory factory) {

        RedisTemplate<String, Object> template = new RedisTemplate<>();
        // 配置连接工厂
        template.setConnectionFactory(factory);

        //使用Jackson2JsonRedisSerializer来序列化和反序列化redis的value值（默认使用JDK的序列化方式）
        Jackson2JsonRedisSerializer jacksonSeial = new Jackson2JsonRedisSerializer(Object.class);

        ObjectMapper om = new ObjectMapper();
        // 指定要序列化的域，field,get和set,以及修饰符范围，ANY是都有包括private和public
        om.setVisibility(PropertyAccessor.ALL, JsonAutoDetect.Visibility.ANY);
        // 指定序列化输入的类型，类必须是非final修饰的，final修饰的类，比如String,Integer等会跑出异常
        // om.enableDefaultTyping(ObjectMapper.DefaultTyping.NON_FINAL);
        jacksonSeial.setObjectMapper(om);

        // 值采用json序列化
        template.setValueSerializer(jacksonSeial);
        //使用StringRedisSerializer来序列化和反序列化redis的key值
        template.setKeySerializer(new StringRedisSerializer());

        // 设置hash key 和value序列化模式
        template.setHashKeySerializer(new StringRedisSerializer());
        template.setHashValueSerializer(jacksonSeial);
        template.afterPropertiesSet();

        return template;
    }
}
```



> 可以看到不乱码了

![image-20220218160229633](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220218160229633.png)





### RedisUtil工具类

在SpringBoot中，如要操作Redis，就需要一直调用RedisTemplate.opsxxx的方法，一般在工作中不会去这样使用，公司里都会内部将这些操作数据类型的API进行一个封装，就像在学JDBC还有Mybatis等框架的时候，都会有一个XxxUtil的Java工具类，使用起来比较简单

这边推荐一个GitHub：https://github.com/iyayu/RedisUtil.git





# Redis.conf 详解

启动的时候，就通过配置文件来启动 ！



> 单位   配置文件 unit单位 对大小写不敏感

![image-20220218212147659](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220218212147659.png)



> 包含  好比我们学习spring 使用improt include包含多个配置文件

![image-20220218212525594](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220218212525594.png)



> 网络

```bash
bind 127.0.0.1 -::1  # 绑定id
protected-mode yes  #保护模式
port 6379  # 端口设置
```



> 通用

```bash
daemonize yes # 以守护进程的方式运行, 默认是no, 我们需要自己开启为yes
pidfile /var/run/redis_6379.pid  # 如果以后台的方式运行,我们就需要指定一个 pid 进程文件


#日志 4 个级别 默认是notice
# Specify the server verbosity level.
# This can be one of:
# debug (a lot of information, useful for development/testing)
# verbose (many rarely useful info, but not a mess like the debug level)
# notice (moderately verbose, what you want in production probably) 生产环境
# warning (only very important / critical messages are logged)
loglevel notice 
logfile "" # 日志的文件位置名
databases 16 # 数据库的数量, 默认是16个
always-show-logo no # 是否总是显示logo 就是启动的logo 默认是no
```



> 快照

持久化, 在规定的时间内, 执行了多少次操作, 则会持久化到文件 .rdb  .aof

redis 是内存数据库, 如果没有持久化, 那么数据断电及失 !

```bash
# 如果3600秒内, 如果至少有一个key进行了修改, 我们就进行持久化操作
# save 3600 1 
# 如果300秒内, 如果至少页100个key 进行了修改, 我们就进行持久化操作 
# save 300 100
#  如果60秒内, 如果至少页10000个key 进行了修改, 我们就进行持久化操作
# save 60 10000

# 我们之后学习持久化, 会自己定义这个测试

stop-writes-on-bgsave-error yes # 持久化如果出错, 是否还需要继续工作 !
rdbcompression yes # 是否压缩 rdb 文件, 需要消耗cpu资源
rdbchecksum yes  # 保存rdb文件的时候, 进行错误的检查校验 !
dir ./    # rdb 文件保存的命令


```



> REPLICATION 复制, 后面会记主从复制的



> SECURITY  安全

![image-20220218220011018](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220218220011018.png)

```bash
127.0.0.1:6379> config get requirepass  # 查看密码
1) "requirepass"
2) ""
127.0.0.1:6379> config set requirepass 123456 # 设置密码
OK
127.0.0.1:6379> config get requirepass # 查看密码
1) "requirepass"
2) "123456"

# 如果权限不够要先输入密码 命令: auth 123456
```



> CLIENTS   限制

```bash
maxclients 10000 # 设置能链接上redis的最大链接客服数量
maxmemory <bytes> # redis 配置最大的内存容量 
 maxmemory-policy noeviction # 内存到达上限之后的处理策略
 # 移除一些过期的key
 # 报错
 #...
```

#### **maxmemory-policy 六种方式**

**1、volatile-lru：**只对设置了过期时间的key进行LRU（默认值） 

**2、allkeys-lru ：** 删除lru算法的key  

**3、volatile-random：**随机删除即将过期key  

**4、allkeys-random：**随机删除  

**5、volatile-ttl ：** 删除即将过期的  

**6、noeviction ：** 永不过期，返回错误



> APPEND ONLY 模式  aof配置

```bash
appendonly no # 默认是不开启的aof模式, 默认是使用rdb持久化的, 在大部分所有的情况下, rdb完全够用
appendfilename "appendonly.aof" # 持久化的文件的名字


# appendfsync always  # 每次修改都会 sync(同步) 消耗性能
appendfsync everysec #每秒执行一次sync 可能会丢失一秒的数据
# appendfsync no  # 不执行 sync 这个时候操作系统自己同步数据, 速度最快

```





# Redis 持久化

Redis 是内存数据库, 如果不将内存中的数据库状态保存到磁盘, 那么一旦服务器进程退出, 服务器中的数据库状态也会消失. 所以Redis 提供了持久化功能



## RDB (Redis DataBase)

> 什么是RDB

在主从复制中, rdb就是备用的, 放在从机上面

<img src="https://img-blog.csdnimg.cn/img_convert/802eccb6c17bb9fd51c013581a29a819.png" alt="img" style="zoom:50%;" />



在指定的时间间隔内将内存中的数据集快照写入磁盘, 也就是行话讲的Snapshot快照, 它恢复时是将快照文件直接读到内存里.

Redis会单独创建 (fork) 一个子进程来进行持久化, 会将数据写入到一个临时文件中, 持久化过程就都结束了, 再用这个临时文件替换上次持久化好的文件. 整个过程中, 主进程是不进行任何IO操作的, 这就确保了极高的性能. 如果需要进行大规模数据的恢复, 且对于数据恢复的完整性不是非常敏感, 那RDB方式要比AOF方式更加的高效. RDB的缺点是最后一次持久化后的数据可能丢失. 我们默认的就是RDB, 一般情况下不需要修改这个配置 !

有时候在生产环境我们会将这个文件进行备份

==Rdb保存的文件是 dump.rdb== 都是在我们的配置文件中快照中进行配置的

![image-20220220212630502](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220220212630502.png)在配置文件中有设置名字



![image-20220220213306324](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220220213306324.png)





> 触发机制

1. save的规则满足的情况下, 会自动触发rdb规则
2. 执行 flushall 命令, 也会触发我们的rdb规则
3. 退出redis, 也会产生 rdb文件

备份就自动生成一个 dump.rdb

![image-20220220214911360](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220220214911360.png)





> 如何恢复rdb文件

1. 只需要将rdb文件放在我们redis启动目录就可以, redis启动的时候会自动检查dump.rdb 恢复其中的数据!

2. 查看需要存在的位置

   ```bash
   127.0.0.1:6379> config get dir
   1) "dir"
   2) "/opt/redis-6.2.6/bin" # 如果在这个目录下存在 dump.rdb文件, 启动就会自动恢复其中的数据
   ```



> 几乎就它自己默认的配置就够用



优点:

1. 适合大规模的数据恢复 ! 
2. 对数据的完整性要求不高



缺点:

1. 需要一定的时间间隔进程操作 ! 如果redis意外宕机了, 这个最后一次修改数据就没有了
2. fork进程的时候, 会占用一定的内存空间 !



## AOF (Append Only File)

将我们的所有命令都纪录下来, history, 恢复的时候就把这个文件的命令全部执行一遍 !

> 是什么

以日志的形式来纪录每个写操作, 将Redis执行过的所有指令纪录下来 (读操作不纪录), 只许追加文件当不可以改写文件, Redis启动之初会读取文件重新构建数据, 换言之, redis重启的话就根据日志文件的内容将写指令从前到后执行一次以完成数据的恢复工作

==Aof保存的是 appenonly.aof 文件==



> append

![image-20220221133207713](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221133207713.png)

默认是不开启的, 我们需要手动进行配置 ! 我们只需要将 appendonly 改为yes就开启了aof ! 重启redis 就可以生效了 

如果这个 aof文件有错误, 这时候 redis 是启动不起来的, 我们需要修复这个配置文件

> 测试

先把数据库清空并且退出redis

```bash
127.0.0.1:6379> flushall  # 清空数据库
OK
127.0.0.1:6379> SHUTDOWN # 退出
not connected> exit
[root@localhost bin]# 

```

在把持久化rdb文件删除 ==dump.rdb==

```bash
[root@localhost bin]# rm -rf dump.rdb 
[root@localhost bin]# ls
appendonly.aof  redis-check-aof  redis-cli  redis.conf  redis-server
[root@localhost bin]# 
```

在修改 aof文件 改一个错误的命令

```bash
$2
v1
*3
$3
set         
$2          
k2          
$2          
v2         
*3
$3            
set   
$2
k3
$2  
v3  
*3
$3  
set 
$2  
k4  
$2
888888v4 
*2
$6
SELECT
$1
55555555555555555555555555555555555555555555555555555550

```

再次启动redis, 可以看到登录失败了

```bash
[root@localhost bin]# ./redis-server redis.conf 
[root@localhost bin]# ./redis-cli 
Could not connect to Redis at 127.0.0.1:6379: Connection refused  # 可以看到报错了
not connected> exit # 退出 
```

如果这个aof文件有错误, 这时候 redis 是启动不起来的, 我们需要修复这个配置文件

redi 给我们提供了一个工具 ==redis-check-aof --fix==

6.0版本的 redis-check-aof 文件在src目录中

```bash
# 因为redis-check-aof这个文件在src命令所以这里写了他的全路径 /opt/redis-6.2.6/src/redis-check-aof --fix appendonly.aof 
 
 [root@localhost bin]#  /opt/redis-6.2.6/src/redis-check-aof --fix appendonly.aof 
0x              87: Expected \r\n, got: 3838
AOF analyzed: size=223, ok_up_to=110, ok_up_to_line=33, diff=113
This will shrink the AOF from 223 bytes, with 113 bytes, to 110 bytes
Continue? [y/N]: y
Successfully truncated AOF

```



修复后的 aof文件, 可以看到 k4 v4没了

```bash
*2
$6
SELECT
$1
0           
*3          
$3          
set         
$2         
k1
$2            
v1    
*3
$3
set 
$2  
k2
$2  
v2  
*3  
$3  
set
$2
k3
$2
v3
```



再次启动redis

```bash
[root@localhost bin]# ./redis-server redis.conf 
[root@localhost bin]# ./redis-cli
127.0.0.1:6379> 
127.0.0.1:6379> keys *
1) "k3"
2) "k2"
3) "k1"
```



> 重写规则

aof默认就是文件的无限追加, 文件会越来越大

![image-20220221142443254](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221142443254.png)

如果aof文件大于64m, 太大了 ! fork一个新的进程来将我们的文件进行重写 !



> aof的优点和缺点

```bash
appendonly no # 默认是不开启的aof模式, 默认是使用rdb持久化的, 在大部分所有的情况下, rdb完全够用
appendfilename "appendonly.aof" # 持久化的文件的名字

# appendfsync always  # 每次修改都会 sync(同步) 消耗性能
appendfsync everysec #每秒执行一次sync 可能会丢失一秒的数据
# appendfsync no  # 不执行 sync 这个时候操作系统自己同步数据, 速度最快
```



优点:

1. 每一次修改都同步, 文件的完整性会更加好
2. 每秒同步一次, 可能会丢失一秒的数据
3. 从不同步, 效率是最高的



缺点:

1. 相当于数据文件来说, aof远远大于rdb, 修复的速度也比rdb慢
2. aof 运行效率也要比rdb慢, 所以redis默认的配置就是rdb持久化



> 扩展

1. RDB持久化方式能够在指定的时间间隔内对你的数据进行快照存储
2. AOF持久化方式纪录每次对服务器写的操作, 当服务器重启的时候会重新执行这些命令来恢复原始的数据,AOF命令以Redis 协议追加保存每次写的操作到文件末尾, Redis还能对AOF文件进行后台重写, 使得AOF文件的体积不至于过大
3. 只做缓存, 如果你只希望你的数据在服务器运行的时候存在, 你也可以不使用持久化
4. 同时开启两种持久化方式
   - 在这种情况下, 当redis重启的时候会优先载入AOF文件来修复原始的数据, 因为在通常情况下AOF文件保存的数据集要比RDB文件保存的数据集要完整
   - RDB的数据不实时, 同时使用两者时服务器重启也会找AOF文件, 那要不要使用AOF呢? 作者不建议,因为RDB要适合用于备份数据库(AOF在不断变化不好备份), 快速重启, 而且不会有AOF可能潜在的Bug,留着作为一个万一的手段.
5. 性能建议
   - 因为RDB文件只用作后备用途,建议只在Slave持久化RDB文件, 而且只要15分钟备份一次就够了, 只保留 save 900 1 这条规则
   - 如果 Enable AOF, 好处是在最恶劣情况下也只会丢失两秒数据, 启动脚本较简单只looad自己的AOF文件就可以了, 代价一是带来了持续的IO, 二是AOF rewrite 的最后将 rewrite 过程中产生的新数据写到新文件造成的阻塞几乎是不可避免的. 只要硬盘许可, 应该尽量减少AOF rewrite 的频率, AOF重写的基础大小默认值64m太小了, 可以设置到5g以上, 默认超过原大小100%大小重写可以改到适当的数值
   - 如果不Enable AOF, 仅靠 Master-Slave Repllcation 实现高可用性也可以, 能省掉一大笔IO, 也减少了rewrite时带来的系统波动. 代价是如果 Master/Slave 同时倒掉(断电), 会丢失十几分钟的数据, 启动脚本也要比较两个 Master/Slave 中的RDB文件, 载入较新的那个, 微博就是这种架构







# Redis发布与订阅

Redis的发布订阅（publish/subscribe）是一种消息通信模式，发送者（publish）发送消息，订阅者（subscribe）接收消息

Redis客户端可以订阅任意数量的频道

订阅/发布消息图：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201119123521181.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQ2ODQ3NA==,size_16,color_FFFFFF,t_70#pic_center)

下图展示了频道 channel1 ， 以及订阅这个频道的三个客户端 —— client2 、 client5 和 client1 之间的关系：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200513215523258.png)

当有新消息通过 PUBLISH 命令发送给频道 channel1 时， 这个消息就会被发送给订阅它的三个客户端：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051321553483.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg3MzIyNw==,size_16,color_FFFFFF,t_70)





命令：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201119123616735.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQ2ODQ3NA==,size_16,color_FFFFFF,t_70#pic_center)



> 测试

订阅端:

```bash
127.0.0.1:6379> SUBSCRIBE wbms  # 订阅 wbms
Reading messages... (press Ctrl-C to quit)
1) "subscribe"
2) "wbms"
3) (integer) 1
# 等待读取推送的消息
1) "message"  # 消息
2) "wbms"     # 来自wbms频道
3) "207hello" # 消息内容
1) "message"
2) "wbms"
3) "207hel8888888lo"
```

发送端:

在开启一个服务

```bash
127.0.0.1:6379> PUBLISH wbms "207hello"  # 往wbms频道 发送消息
(integer) 1
127.0.0.1:6379> PUBLISH wbms "207hel8888888lo"
(integer) 1
127.0.0.1:6379> 
```



原理：

Redis是C语言编写，在实现消息的发布和订阅的时候，Redis将其封装在一个后缀名为点c的文件中，pubsub.c

![img](https://img-blog.csdnimg.cn/20201119123637685.png#pic_center)

通过subscribe和publish命令实现消息的发布和订阅，当用户订阅了一个频道之后，redis-server里面维护了一个字典，字典里有很多个Channel（频道），字典的值就是一个链表，链表中保存的是订阅了这个频道的用户，使用publish命令往频道发送数据之后，redis-server使用此频道作为key，去遍历这个指定的value链表，将信息依次发送过去

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201119123704135.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQ2ODQ3NA==,size_16,color_FFFFFF,t_70#pic_center)

发布订阅的实现场景

1、实时沟通消息系统

2、微信公众号（点击关注，后台发送一篇博客，订阅的用户就可以监听到）

....





# Redis主从复制

> 概念

　　主从复制，是指将一台Redis服务器的数据，复制到其他的Redis服务器。前者称为主节点(master/leader)，后者称为从节点(slave/follower)；==数据的复制是单向的，只能由主节点到从节点.==
Master以写为主，Slave 以读为主。

　　==默认情况下，每台Redis服务器都是主节点；==

且一个主节点可以有多个从节点(或没有从节点)，但一个从节点只能有一个主节点。（）

主从复制的作用主要包括：

1、数据冗余：主从复制实现了数据的热备份，是持久化之外的一种数据冗余方式。
2、故障恢复：当主节点出现问题时，可以由从节点提供服务，实现快速的故障恢复；实际上是一种服务的冗余。
3、负载均衡：在主从复制的基础上，配合读写分离，可以由主节点提供写服务，由从节点提供读服务（即写Redis数据时应用连接主节点，读Redis数据时应用连接从节点），分担服务器负载；尤其是在写少读多的场景下，通过多个从节点分担读负载，可以大大提高Redis服务器的并发量。
4、高可用（集群）基石：除了上述作用以外，主从复制还是哨兵和集群能够实施的基础，因此说主从复制是Redis高可用的基础。
一般来说，要将Redis运用于工程项目中，只使用一台Redis是万万不能的（宕机），原因如下：

1、从结构上，单个Redis服务器会发生单点故障，并且一台服务器需要处理所有的请求负载，压力较大；
2、从容量上，单个Redis服务器内存容量有限，就算一台Redis服务器内存容量为256G，也不能将所有内存用作Redis存储内存，一般来说，==单台Redis最大使用内存不应该超过20G==。
电商网站上的商品，一般都是一次上传，无数次浏览的，说专业点也就是"多读少写"。

对于这种场景，我们可以使如下这种架构：

![狂神redis笔记(下)_IT_16](https://s7.51cto.com/images/blog/202107/23/8e1102bae3263cd660458721854d180c.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_100,g_se,x_10,y_10,shadow_90,type_ZmFuZ3poZW5naGVpdGk=)



主从复制, 读写分类 ! 80%的情况下都是在进行读操作 ! 减缓服务器的压力 ! 架构中经常使用 ! 一主二从 !

只要在公司中, 主从复制就是必须要使用的, 因为在真实的项目中不可能单机使用Redis !



## 环境配置

只配置从库, 不用配置主库, 因为Redis默认就是一个主库

> 查看当前库的信息 ==info replication==

```bash
[root@localhost bin]# ./redis-server redis.conf 
[root@localhost bin]# ./redis-cli # 启动
127.0.0.1:6379> info replication 
# Replication
role:master  # 角色默认是主
connected_slaves:0 #0  表示没有从机
master_failover_state:no-failover
master_replid:dc2c18f05d0bde14fb53f689cd9f2e0777370667
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:0
second_repl_offset:-1
repl_backlog_active:0
repl_backlog_size:1048576
repl_backlog_first_byte_offset:0
repl_backlog_histlen:0
127.0.0.1:6379> 
```

> 创建3个从的配置文件

复制3个配置文件, 然后修改对应的信息

1. 端口号
2. pid 名字
3. log文件名字
4. dump.rdb名字

![image-20220221161056584](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221161056584.png)



> 为3个从的配置文件 修改端口

```bash
[root@localhost bin]# vim redis79.conf 
[root@localhost bin]# vim redis80.conf 
[root@localhost bin]# vim redis81.conf 
# 修改端口 修改日志文件名字 修改RDB的文件名字 进程id pidfile /var/run/redis_6380.pid
```



修改完毕之后启动我们的3个Redis服务器, 可以通过进程信息信息查看 !

![image-20220221163000989](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221163000989.png)



## 一主二从

==默认情况下, 每台Redis服务器都是主节点== 我们一般情况下只用配置从机就行了

就一个服务器登录的时候要加上端口号

```bash
 ./redis-cli -p 6381
```



认老大! 一主(79)二从(80,81端口)

==slaveof 主机的ip 端口==

```bash

127.0.0.1:6380> SLAVEOF 127.0.0.1 6379  # 找谁当自己的主
OK
127.0.0.1:6380> info replication
# Replication
role:slave
master_host:127.0.0.1    # 主的ip
master_port:6379         # 端口
master_link_status:up
master_last_io_seconds_ago:8
master_sync_in_progress:0
slave_read_repl_offset:504
slave_repl_offset:504
slave_priority:100
slave_read_only:1
replica_announced:1
connected_slaves:0
master_failover_state:no-failover
master_replid:01708dd2c6d3d99cb359e44bf8d63ab2d7979b1b
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:504
second_repl_offset:-1
repl_backlog_active:1
repl_backlog_size:1048576
repl_backlog_first_byte_offset:463
repl_backlog_histlen:42
```

查看主机

```bash
127.0.0.1:6379> INFO replication
# Replication
role:master       # 角色为 主
connected_slaves:2 # 两个从者
# 从者的ip和端口
slave0:ip=127.0.0.1,port=6381,state=online,offset=476,lag=0 
slave1:ip=127.0.0.1,port=6380,state=online,offset=476,lag=0
master_failover_state:no-failover
master_replid:01708dd2c6d3d99cb359e44bf8d63ab2d7979b1b
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:476
second_repl_offset:-1
repl_backlog_active:1
repl_backlog_size:1048576
repl_backlog_first_byte_offset:1
repl_backlog_histlen:476
```



真正的主从配置应该在配置文件中配置, 这样的话就是永久的, 我们这里使用的是命令, 是暂时的

![image-20220221184549788](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221184549788.png)



> 细节

主机可以写,从机不能写只能读 ! 主机中的所有信息和数据, 都会自动被从机保存

主机写:

![image-20220221185123163](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221185123163.png)



从机只能读取内容 !

![image-20220221185306656](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221185306656.png)



==主机断开连接, 从机依旧连接到主机的, 但是没有写操作, 这个时候, 主机如果回来了, 从机依旧可以直接获取到主机写的信息==

==如果是使用命令行, 来配置的主从, 这个时候如果重启了, 就会变成主机, 只要在变为从机, 立马就从主机中获取值==



> 复制原理

如果一个Slave指定了一个master做老大，那么Master节点就会发送一个叫做sync的同步命令，在使用了SLAVEOF命令之后，Master接收到了，就会启动后台的存盘进程，开始收集修改数据集的命令，在存盘进程执行完毕之后，会将数据文件发送给Slave，实现一次完全同步

说到同步，这个有两个概念需要多聊一嘴

1、全量复制，Slave文件在接到Master发来的数据文件之后，会将其存盘并加载到内存

2、增量复制，Master和Slave已经实现同步的情况下，如果Master继续修改数据集，会将命令再次收集起来，再发送给Slave

只要是重新连接Master的服务器，在连接之后都会自动执行全量复制！！！



> 层层链路 

上一个M链接下一个S !

![image-20220221193908156](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221193908156.png)



这时候也可以完成我们的主从复制 !



> 如果没有老大了，这个时候能不能选择出来一个老大呢？手动！

如果主机断开了连接，我们可以使用`SLAVEOF no one`让自己变成主机！其他的节点就可以手动连接到最新的主节点（手动）！如果这个时候老大修复了，那么久重新连接！



# 哨兵模式 (自动选举老大的)

**主从切换技术的方法是：当主服务器宕机后，需要手动把一台从服务器切换为主服务器，这就需要人工干预，费事费力，还会造成一段时间内服务不可用。这不是一种推荐的方式，更多时候，我们优先考虑哨兵模式**。

谋朝篡位的自动版, 能够后台监控主机是否故障, 如果故障了根据投票数==自动将库转化为主库==

哨兵模式是一种特殊的模式, 首先Redis提供了哨兵的命令, 哨兵是一个独立的进程, 作为进程, 它会独立运行. 

其原理是**哨兵通过发送命令, 等待Redis服务器响应, 从而监控运行的多个Redis实例**

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8xMTMyMDAzOS01N2E3N2NhMjc1N2QwOTI0LnBuZw?x-oss-process=image/format,png)



哨兵的作用：

- 通过发送命令，让Redis服务器返回监控其运行状态，包括主服务器和从服务器。
- 当哨兵监测到master宕机，会自动将slave切换成master，然后通过**发布订阅模式**通知其他的从服务器，修改配置文件，让它们切换主机。

然而一个哨兵进程对Redis服务器进行监控, 可能会出现问题, 为此, 我们可以使用多个哨兵进行监控. 各个哨兵之间还会进行监控,这样就形成了多哨兵模式

多哨兵模式

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8xMTMyMDAzOS0zZjQwYjE3YzA0MTIxMTZjLnBuZw?x-oss-process=image/format,png)



假设主服务器宕机, 哨兵1线检测到这个结果, 系统并不会马上进行failover过程, 仅仅是哨兵1主观的以为服务器不可用, 这个现象称为==主观下线==. 当后面的哨兵也检测到主服务器不可用, 并且数量达到一定值时, 那么哨兵之间就会进行一次投票, 投票的结果是由一个哨兵发起, 进行failove[故障转移] 操作, 切换成功后, 就会通过发布订阅模式, 让各个哨兵把自己监控的从服务器实现切换主机, 这个过程称为==客观下线==





> 测试

我们目前的状态是一主二从 !

1. 配置哨兵配置文件 在存放conf文件中,新建一个 sentinel.conf 文件

```bash
# sentinel monitor 被监控的名称 host 端口 1
sentinel monitor myredis 127.0.0.1 6379 1
```

后面的这个数字 !, 代表主机挂了, salve投票让谁接替成为主机, 票数最多的, 就会成为主机 !



2. 启动哨兵 !

    6.0 版本的redis-sentinel 在src目录 我们可以把它复制到 bin中 ==cp /opt/redis/src/redis-sentinel redis-sentinel==

   ```bash
    ./redis-sentinel sentinel.conf  # 启动 出现下面的图案就说明启动成功了
   56640:X 21 Feb 2022 22:01:01.965 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
   56640:X 21 Feb 2022 22:01:01.965 # Redis version=6.2.6, bits=64, commit=00000000, modified=0, pid=56640, just started
   56640:X 21 Feb 2022 22:01:01.965 # Configuration loaded
   56640:X 21 Feb 2022 22:01:01.966 * Increased maximum number of open files to 10032 (it was originally set to 1024).
   56640:X 21 Feb 2022 22:01:01.966 * monotonic clock: POSIX clock_gettime
                   _._                                                  
              _.-``__ ''-._                                             
         _.-``    `.  `_.  ''-._           Redis 6.2.6 (00000000/0) 64 bit
     .-`` .-```.  ```\/    _.,_ ''-._                                  
    (    '      ,       .-`  | `,    )     Running in sentinel mode
    |`-._`-...-` __...-.``-._|'` _.-'|     Port: 26379
    |    `-._   `._    /     _.-'    |     PID: 56640
     `-._    `-._  `-./  _.-'    _.-'                                   
    |`-._`-._    `-.__.-'    _.-'_.-'|                                  
    |    `-._`-._        _.-'_.-'    |           https://redis.io       
     `-._    `-._`-.__.-'_.-'    _.-'                                   
    |`-._`-._    `-.__.-'    _.-'_.-'|                                  
    |    `-._`-._        _.-'_.-'    |                                  
     `-._    `-._`-.__.-'_.-'    _.-'                                   
         `-._    `-.__.-'    _.-'                                       
             `-._        _.-'                                           
                 `-.__.-'                                               
   
   56640:X 21 Feb 2022 22:01:01.966 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
   56640:X 21 Feb 2022 22:01:01.968 # Sentinel ID is 34272fe8c51720f0b1c1013b616f0fa8f2c7d5d1
   56640:X 21 Feb 2022 22:01:01.968 # +monitor master myredis 127.0.0.1 6379 quorum 1
   56640:X 21 Feb 2022 22:01:01.968 * +slave slave 127.0.0.1:6380 127.0.0.1 6380 @ myredis 127.0.0.1 6379
   56640:X 21 Feb 2022 22:01:01.970 * +slave slave 127.0.0.1:6381 127.0.0.1 6381 @ myredis 127.0.0.1 6379
   
   ```



如果主节点 断开了, 这个时候就会从从机中随机选择一个服务器 ! (这里面有一个投票算法)

哨兵日志:

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221221035370.png" alt="image-20220221221035370" style="zoom:%;" />

如果主机此时回来了, 只能归并到新的主机下, 当做从机, 这就是哨兵模式的规则 !

> 哨兵模式

优点:

1. 哨兵集群, 基于主从复制, 所有的主从配置优点, 它全有
2. 主从可以切换, 故障可以转移, 系统的可用性就会更好
3. 哨兵模式就是主从复制模式的升级, 手动到自动, 更加健壮

缺点:

1. Redis 不好在线扩容的, 集群容量一旦到达上限, 这些扩容就十分麻烦
2. 实现哨兵模式的配置其实是很麻烦的, 里面有很多的选择!



> 哨兵模式的全部配置

```bash
# Example sentinel.conf
 
# 哨兵sentinel实例运行的端口 默认26379
port 26379
 
# 哨兵sentinel的工作目录
dir /tmp
 
# 哨兵sentinel监控的redis主节点的 ip port 
# master-name  可以自己命名的主节点名字 只能由字母A-z、数字0-9 、这三个字符".-_"组成。
# quorum 当这些quorum个数sentinel哨兵认为master主节点失联 那么这时 客观上认为主节点失联了
# sentinel monitor <master-name> <ip> <redis-port> <quorum>
sentinel monitor mymaster 127.0.0.1 6379 1
 
# 当在Redis实例中开启了requirepass foobared 授权密码 这样所有连接Redis实例的客户端都要提供密码
# 设置哨兵sentinel 连接主从的密码 注意必须为主从设置一样的验证密码
# sentinel auth-pass <master-name> <password>
sentinel auth-pass mymaster MySUPER--secret-0123passw0rd
 
 
# 指定多少毫秒之后 主节点没有应答哨兵sentinel 此时 哨兵主观上认为主节点下线 默认30秒
# sentinel down-after-milliseconds <master-name> <milliseconds>
sentinel down-after-milliseconds mymaster 30000
 
# 这个配置项指定了在发生failover主备切换时最多可以有多少个slave同时对新的master进行 同步，
这个数字越小，完成failover所需的时间就越长，
但是如果这个数字越大，就意味着越 多的slave因为replication而不可用。
可以通过将这个值设为 1 来保证每次只有一个slave 处于不能处理命令请求的状态。
# sentinel parallel-syncs <master-name> <numslaves>
sentinel parallel-syncs mymaster 1
 
 
 
# 故障转移的超时时间 failover-timeout 可以用在以下这些方面： 
#1. 同一个sentinel对同一个master两次failover之间的间隔时间。
#2. 当一个slave从一个错误的master那里同步数据开始计算时间。直到slave被纠正为向正确的master那里同步数据时。
#3.当想要取消一个正在进行的failover所需要的时间。  
#4.当进行failover时，配置所有slaves指向新的master所需的最大时间。不过，即使过了这个超时，slaves依然会被正确配置为指向master，但是就不按parallel-syncs所配置的规则来了
# 默认三分钟
# sentinel failover-timeout <master-name> <milliseconds>
sentinel failover-timeout mymaster 180000
 
# SCRIPTS EXECUTION
 
#配置当某一事件发生时所需要执行的脚本，可以通过脚本来通知管理员，例如当系统运行不正常时发邮件通知相关人员。
#对于脚本的运行结果有以下规则：
#若脚本执行后返回1，那么该脚本稍后将会被再次执行，重复次数目前默认为10
#若脚本执行后返回2，或者比2更高的一个返回值，脚本将不会重复执行。
#如果脚本在执行过程中由于收到系统中断信号被终止了，则同返回值为1时的行为相同。
#一个脚本的最大执行时间为60s，如果超过这个时间，脚本将会被一个SIGKILL信号终止，之后重新执行。
 
#通知型脚本:当sentinel有任何警告级别的事件发生时（比如说redis实例的主观失效和客观失效等等），将会去调用这个脚本，
#这时这个脚本应该通过邮件，SMS等方式去通知系统管理员关于系统不正常运行的信息。调用该脚本时，将传给脚本两个参数，
#一个是事件的类型，
#一个是事件的描述。
#如果sentinel.conf配置文件中配置了这个脚本路径，那么必须保证这个脚本存在于这个路径，并且是可执行的，否则sentinel无法正常启动成功。
#通知脚本
# sentinel notification-script <master-name> <script-path>
  sentinel notification-script mymaster /var/redis/notify.sh
 
# 客户端重新配置主节点参数脚本
# 当一个master由于failover而发生改变时，这个脚本将会被调用，通知相关的客户端关于master地址已经发生改变的信息。
# 以下参数将会在调用脚本时传给脚本:
# <master-name> <role> <state> <from-ip> <from-port> <to-ip> <to-port>
# 目前<state>总是“failover”,
# <role>是“leader”或者“observer”中的一个。 
# 参数 from-ip, from-port, to-ip, to-port是用来和旧的master和新的master(即旧的slave)通信的
# 这个脚本应该是通用的，能被多次调用，不是针对性的。
# sentinel client-reconfig-script <master-name> <script-path>
sentinel client-reconfig-script mymaster /var/redis/reconfig.sh
```





# Redis缓存穿透和雪崩

Redis缓存的使用, 极大的提示了应用程序的性能和效率, 特别是数据查询方面. 但同时, 它也带来了一些问题. 其中, 最要害的问题, 就是数据的一致性问题, 从严格意义上讲, 这个问题无解, 如果对数据的一致性要求很高, 那么基于不能使用缓存

另外的一些典型问题就是, 缓存穿透, 缓存雪崩和缓存击穿. 目前, 业界也都有比较流行的解决方案

![image-20220221224414387](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220221224414387.png)



## 缓存穿透(查不到的)

> 概念

缓存穿透的概念很简单, 用户想要查询一个数据, 发现redis内存数据库没有, 也就是缓存中没有, 于是向持久层数据库查询. 发现也没有, 于是本次查询失败. 当用户很多的时候, 缓存都没有命中, 于是都'去请求了持久层数据库. 这会给持久层数据库造成很大的压力, 这时候就相当于出现了缓存穿透



> 解决方案

==布隆过滤器==

对所有可能查询的参数以Hash的形式存储，以便快速确定是否存在这个值，在控制层先进行拦截校验，校验不通过直接打回，减轻了存储系统的压力。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200513215824722.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg3MzIyNw==,size_16,color_FFFFFF,t_70)

==缓存空对象==

一次请求若在缓存和数据库中都没找到，就在缓存中方一个空对象用于处理后续这个请求。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200513215836317.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg3MzIyNw==,size_16,color_FFFFFF,t_70)

 这样做有一个缺陷：存储空对象也需要空间，大量的空对象会耗费一定的空间，存储效率并不高。解决这个缺陷的方式就是设置较短过期时间

即使对空值设置了过期时间，还是会存在缓存层和存储层的数据会有一段时间窗口的不一致，这对于需要保持一致性的业务会有影响。






## 缓存击穿(量太大了,缓存过期)

> 概述

这里需要注意和缓存穿透的区别, 缓存击穿, 是指一个key非常热点, 在不停的扛着大并发, 大并发集中对这一个点进行访问, 当这个key在失效的瞬间, 有大量的请求并发访问, 这类数据一般是热点数据, 由于缓存过期, 会同时访问数据库来查询最新数据,并且回写缓存, 会导致数据库瞬间压力过大



> 解决方案

**设置热点数据永不过期**

从缓存层面来看, 没有设置过期时间, 所以不能出现热点key过期后产生的问题



**加互斥锁**

分布式锁 : 使用分布式锁, 保证对于每个key同时只有一个线程去查询后端服务, 其他线程没有获得分布式锁的权限,因此只需要等待即可. 这种方式将高并发的压力转移到了分布式锁, 因此对分布式锁的考验很大



## 缓存雪崩

> 概念

缓存雪崩,是指在某一个时间段, 缓存集体过期失效. Redis宕机!

产生雪崩的原因之一, 比如在双十二等待时候, 马上就要到双十二零点, 很快就会迎来一波抢购, 这波商品时间比较集中的放入了缓存, 假设缓存一个小时, 那么到了凌晨一点的时候, 这批商品的缓存就都过期了, 而对这批商品的访问查询, 都落到了数据库上, 对数据库而言, 就会产生周期性的压力波峰, 于是所有的请求就会到达存储层, 存储层的调用量就会暴增, 造成存储层也会挂掉的情况

![img](https://img-blog.csdnimg.cn/20200513215850428.jpeg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg3MzIyNw==,size_16,color_FFFFFF,t_70)



> 解决方案

**redis高可用**

这个思想的含义是，既然redis有可能挂掉，那我多增设几台redis，这样一台挂掉之后其他的还可以继续工作，其实就是搭建的集群

**限流降级**

这个解决方案的思想是，在缓存失效后，通过加锁或者队列来控制读数据库写缓存的线程数量。比如对某个key只允许一个线程查询数据和写缓存，其他线程等待。

**数据预热**

数据加热的含义就是在正式部署之前，我先把可能的数据先预先访问一遍，这样部分可能大量访问的数据就会加载到缓存中。在即将发生大并发访问前手动触发加载缓存不同的key，设置不同的过期时间，让缓存失效的时间点尽量均匀。








































​	
