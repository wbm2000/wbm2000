# MyBatisPlus 概述

为什么要学习它呢 ? 

MyBatisPlus 可以节省我们大量的工作时间, 所有的CRUD它都可以自动化完成!

JPA, tk-mapper MyBatisPlus

偷懒的 !

> 简介

是什么 ?  Mybatis 本来就是简化 JDBC操作的

官网:https://baomidou.com/  MyBatisPlus 是简化MyBatis的

![image-20220226170053475](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220226170053475.png)





![image-20220226170417494](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220226170417494.png)



> 特性

- **无侵入**：只做增强不做改变，引入它不会对现有工程产生影响，如丝般顺滑
- **损耗小**：启动即会自动注入基本 CURD，性能基本无损耗，直接面向对象操作
- **强大的 CRUD 操作**：内置通用 Mapper、通用 Service，仅仅通过少量配置即可实现单表大部分 CRUD 操作，更有强大的条件构造器，满足各类使用需求
- **支持 Lambda 形式调用**：通过 Lambda 表达式，方便的编写各类查询条件，无需再担心字段写错
- **支持主键自动生成**：支持多达 4 种主键策略（内含分布式唯一 ID 生成器 - Sequence），可自由配置，完美解决主键问题
- **支持 ActiveRecord 模式**：支持 ActiveRecord 形式调用，实体类只需继承 Model 类即可进行强大的 CRUD 操作
- **支持自定义全局通用操作**：支持全局通用方法注入（ Write once, use anywhere ）
- **内置代码生成器**：采用代码或者 Maven 插件可快速生成 Mapper 、 Model 、 Service 、 Controller 层代码，支持模板引擎，更有超多自定义配置等您来使用
- **内置分页插件**：基于 MyBatis 物理分页，开发者无需关心具体操作，配置好插件之后，写分页等同于普通 List 查询
- **分页插件支持多种数据库**：支持 MySQL、MariaDB、Oracle、DB2、H2、HSQL、SQLite、Postgre、SQLServer 等多种数据库
- **内置性能分析插件**：可输出 SQL 语句以及其执行时间，建议开发测试时启用该功能，能快速揪出慢查询
- **内置全局拦截插件**：提供全表 delete 、 update 操作智能分析阻断，也可自定义拦截规则，预防误操作



# 快速入门

地址:https://baomidou.com/pages/226c21/#初始化工程

使用第三方组件 :

1. 导入对应的依赖
2. 研究依赖如何配置
3. 代码如何编写
4. 提高扩展技术能力



> 步骤

1. 创建数据库 `mybatis_plus`

   ```sql
   CREATE DATABASE `mybatis_plus`CHARACTER SET utf8 COLLATE utf8_general_ci; # 创建数据库
   ```

2. 创建user表

   ```sql
   DROP TABLE IF EXISTS user;  # 判断是否存在user表
   
   CREATE TABLE user(
       id BIGINT(20) NOT NULL COMMENT '主键ID',
       name VARCHAR(30) NULL DEFAULT NULL COMMENT '姓名',
       age INT(11) NULL DEFAULT NULL COMMENT '年龄',
       email VARCHAR(50) NULL DEFAULT NULL COMMENT '邮箱',
       PRIMARY KEY (id)
   );
   
   -- 真实开发中, version(乐观锁), delete(逻辑删除), gmt_create, gmt_modified
   ```

3. 插入数据

   ```sql
   DELETE FROM user;
   
   INSERT INTO user (id, name, age, email) VALUES
   (1, 'Jone', 18, 'test1@baomidou.com'),
   (2, 'Jack', 20, 'test2@baomidou.com'),
   (3, 'Tom', 28, 'test3@baomidou.com'),
   (4, 'Sandy', 21, 'test4@baomidou.com'),
   (5, 'Billie', 24, 'test5@baomidou.com');
   ```

4. 编写项目, 初始化项目 ! 使用SpringBoot初始化 !

5. 导入依赖

   ```xml
    <dependencies>
   
           <!--web 依赖-->
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-web</artifactId>
           </dependency>
   
   
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-test</artifactId>
               <scope>test</scope>
           </dependency>
   
           <!--数据库驱动-->
           <dependency>
               <groupId>mysql</groupId>
               <artifactId>mysql-connector-java</artifactId>
               <version>8.0.18</version>
           </dependency>
   
           <!--lombok 依赖-->
           <dependency>
               <groupId>org.projectlombok</groupId>
               <artifactId>lombok</artifactId>
               <version>1.18.22</version>
           </dependency>
           
           
           <!--mybatis-plus 是自己开发的, 并非官方的 !-->
           <dependency>
               <groupId>com.baomidou</groupId>
               <artifactId>mybatis-plus-boot-starter</artifactId>
               <version>3.3.1.tmp</version>
           </dependency>
   
       </dependencies>
   
   ```

   说明: 我们使用mybatis-plus 可以节省我们大量的代码, 尽量不要同时导入 mybais 和 mybatis-plus ! 版本的差异

6. 连接数据库 ! 这一步和 mybatis 相同 !

   ```yml
   spring:
     datasource:
       url: jdbc:mysql://localhost:3306/mybatis_plus?useUnicode=true&characterEncoding=utf-8&useSSL=true&serverTimezone=Asia/Shanghai
       username: root
       password: 123456
       driver-class-name: com.mysql.cj.jdbc.Driver
   ```

7. ==传统方式pojo-dao-service-controller==

7. 使用了mybatis_plus 之后

   - pojo

     ```java
     @Data
     @AllArgsConstructor
     @NoArgsConstructor
     public class User {
         private int id;
         private String name;
         private  int age;
         private String email;
     }
     ```

     

   - mapper接口

     ```java
     // 在对应的Mapper上面继承基本的类 BaseMapper
     @Mapper
     @MapperScan("com.wbm.mapper")  // 扫描我们的mapper 文件夹
     @Repository  // 代表持久层
     public interface UserMapper extends BaseMapper<User> {
         // 所有的CRUD操作都已经编写完成了
         // 你不需要像以前的配置一大堆文件了
     }
     ```

     

   - 使用

     ```java
     @SpringBootTest
     class MybatisPlusApplicationTests {
     
         @Autowired
         private UserMapper userMapper;
         @Test
         void contextLoads() {
             // 参数是一个 wrapper , 条件构造器, 这里我们先不用 写null
             List<User> userList = userMapper.selectList(null);
             userList.forEach(System.out::println);
         }
     
     }
     ```

   - 运行

     ![image-20220226184043408](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220226184043408.png)

9. 注意点, 我们需要在主启动类上去扫描我们的mapper包下的所有接口 ==@MapperScan("com.wbm.mapper")==



> 思考问题 ?

1. SQL谁帮我们写的 ?  Mybatis-Plus
2. 方法哪里来的 ? Mybatis-Plus 都写好了





> 配置日志

我们所有的sql现在是不可见的, 我们希望知道它是怎么执行的, 所以我们必须要看日志!

```yaml
# 配置日志
mybatis-plus:
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl
```

![image-20220226185218018](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220226185218018.png)

配置完毕日志之后, 后面就可以查看日志了



# CRUD 扩展

## 插入

> insert 插入

一开始的表

![image-20220227180234937](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220227180234937.png)

```JAVA
    // 测试插入
    @Test
    public void testInsert(){
        User user = new User();
        user.setAge(18);
        user.setName("wbmx");
        user.setEmail("2073568608@qq.com");
        int insert = userMapper.insert(user); // 帮我们自动生成id
        System.out.println(insert); // 受影响的行数
        System.out.println(user); //发现id 会自动 会填
    }
```



![image-20220227180527156](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220227180527156.png)



> 数据库插入的id的默认值为: 全局的唯一id



## 主键生成策略

> 默认ASSIGN_ID 全局唯一id

分布式系统唯一id生成:  https://www.cnblogs.com/haoxinyue/p/5208136.html

雪花算法:

snowflake是Twitter开源的分布式ID生成算法，结果是一个long型的ID。其核心思想是：使用41bit作为毫秒数，10bit作为机器的ID（5个bit是数据中心，5个bit的机器ID），12bit作为毫秒内的流水号（意味着每个节点在每毫秒可以产生 4096 个 ID），最后还有一个符号位，永远是0。可以保证几乎全球唯一 !



> 主键自增

我们需要配置主键自增:

1. 实体类字段上 添加 ==@TableId(type = IdType.AUTO)==

2. 数据库字段一定要是自增的 !

   ![image-20220228115530862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228115530862.png)

3. 再次尝试插入即可



> 其余的源码解释

```java
public enum IdType{
    private final int key;
    AUTO(0),  // 数据库 id 自增
    NONE(1),  // 未设置主键
    INPUT(2),  // 手动输入
    ASSIGN_ID(3), // 默认的全局id
    ASSIGN_UUID(4); //   如果使用IdType.ASSIGN_UUID策略，并重新自动生成排除中划线的UUID作为主键。主键类型为String，对应MySQL的表分段为VARCHAR（32）
    
    public int getKey() {
        return this.key;
    }
    
    IdType(int key) {
        this.key = key;
    }
}

```



## 更新操作

```java
//测试更新
@Test
public void upData(){
    // 通过条件自动拼接动态sql
    User user = new User(12L,"wbm",18,"1935047906@qq.com");
    // 注意, updateById 但是参数是一个 对象!
    int i = userMapper.updateById(user);
    System.out.println(i);
    System.out.println(user);
}
```

一开始的表

![image-20220228130103505](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228130103505.png)

修改后的表

![image-20220228130130633](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228130130633.png)



## 自动填充

创建时间, 修改时间 ! 这些个操作都是自动化完成的, 我们不需要手动更新!

阿里巴巴开发手册 : 所有的数据库表 : gmt_create, gmt_modified 几乎所有的表都要配置上 ! 而且需要自动化

> 方式一: 数据库级别 (工作中是不允许修改数据库的)

1. 在表中新增字段 create_time(创建时间), update_time(更新时间)   默认==CURRENT_TIMESTAMP== 表示当前时间

   ![image-20220228132458521](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228132458521.png)

2. 再次测试插入方法, 我们需要先把实体类同步 !

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class User {
    // 对应数据库中的主键 (uuid , 自增id, 雪花算法, redis, zookeeper !)
    @TableId(type = IdType.INPUT)
    private Long id;
    private String name;
    private  int age;
    private String email;
    private Date createTime;
    private Date updateTime;
}

 //测试更新
    @Test
    public void upData(){
        User user = new User();
        user.setId(12L);
        user.setAge(18);
        user.setName("lqt");
        user.setEmail("2308121831@qq.com");
        int i = userMapper.updateById(user);
        System.out.println(i);
        System.out.println(user);
    }

```

![image-20220228133626560](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228133626560.png)'

![image-20220228133710278](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228133710278.png)







> 方式二 : 代码级别

1. 删除数据库的默认值, 更新操作

   ![image-20220228133938230](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228133938230.png)

2. 实体类字段属性上需要增加注解

   ```java
   @Data
   @AllArgsConstructor
   @NoArgsConstructor
   public class User {
       // 对应数据库中的主键 (uuid , 自增id, 雪花算法, redis, zookeeper !)
       @TableId(type = IdType.AUTO)
       private Long id;
       private String name;
       private  int age;
       private String email;
   
       // 字段添加填充内容
       @TableField(fill = FieldFill.INSERT) // 跟默认时间差不多
       private Date createTime;
       @TableField(fill = FieldFill.INSERT_UPDATE)// 一开始是默认时间,修改了会更新时间
       private Date updateTime;
   }
   
   ```

3. 编写处理器来处理这个注解即可

   ```java
   @Slf4j
   @Component // 一定不要忘记把处理器加到 ioc容器中
   public class MyMetaObjectHandler implements MetaObjectHandler {
   
       // 插入时的填充策略
       @Override
       public void insertFill(MetaObject metaObject) {
           log.info("start insert fill ....");
           /**
            *  setFieldValByName(String fieldName,  // 字段名
            *                    Object fieldVal,  // 需要插入的字段字
            *                    MetaObject metaObject) // 要给那个数据处理
            */
           this.setFieldValByName("createTime",new Date(),metaObject); // 每次增加操作, 都会带上一个当前时间
           this.setFieldValByName("updateTime",new Date(),metaObject); // 更新操作 一创建也会带上一个当前时间
       }
   
       // 更新时的填充策略
       @Override
       public void updateFill(MetaObject metaObject) {
           log.info("start update fill ....");
           this.setFieldValByName("updateTime",new Date(),metaObject); // 当更新某个列时, 会把更新时间修改为, 更新的当前时间
       }
   }
   ```

4. 测试插入

   测试之前的表

   ![image-20220228140350785](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228140350785.png)

   我们修改 id为1的

   ```java
       //测试更新
       @Test
       public void upData(){
           User user = new User();
           user.setId(1L);
           user.setAge(180);
           user.setName("hqy");
           user.setEmail("2308121831@qq.com");
           int i = userMapper.updateById(user);
           System.out.println(i);
           System.out.println(user);
       }
   ```

   ![image-20220228140548568](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228140548568.png)

   ![image-20220228140614709](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228140614709.png)





## 乐观锁

在面试过程中, 我们经常会被问到乐观锁, 悲观锁 ! 这个其实很简单 !

> 乐观锁: 顾名思义十分乐观, 它总是以为不会出现问题, 无论干什么都不去上锁 ! 如果出现了问题, 再次更新值测试

> 悲观锁: 顾名思义十分悲观, 它总是认为不会出现问题, 无论干什么都会上锁 ! 在去操作

- 取出记录时，获取当前 version
- 更新时，带上这个 version
- 执行更新时， set version = newVersion where version = oldVersion
- 如果 version 不对，就更新失败

```Sql
乐观锁: 1, 先查询, 获得版本号, version=1
-- 线程A
   update user set name="wbm" 
   where id = 2 and version=1       -- 当执行之后version自动加1
   
-- 线程B    当两条线程同时修改一个数据的时候 B 也获取version的值 =1 当想要修改的时候,  因为线程A 操作成功了version 变成了2, 这样就会操作失败, 
   update user set name="wbm" 
   where id = 2 and version=1       -- 当执行之后version自动加1
```



> 测试一下MyBatisPlus的乐观锁插件

1. 给数据库值增加 version 

   ![image-20220228162830264](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228162830264.png)

   ![image-20220228162950232](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228162950232.png)

2. 我们需要实体类追加对应的字段

   ```java
   @Data
   @AllArgsConstructor
   @NoArgsConstructor
   public class User {
       // 对应数据库中的主键 (uuid , 自增id, 雪花算法, redis, zookeeper !)
       @TableId(type = IdType.AUTO)
       private Long id;
       private String name;
       private  int age;
       private String email;
   
       // 字段添加填充内容
       @TableField(fill = FieldFill.INSERT)
       private Date createTime;
       @TableField(fill = FieldFill.INSERT_UPDATE)
       private Date updateTime;
       
       @Version // 乐观锁version注解
       private Integer version;
   }
   ```

3. 注册组件

   ```java
   @EnableTransactionManagement // 开启事务
   @Configuration // 代表是一个配置类
   public class MyBatisPlusConfig {
   
       // 注册乐观锁
       @Bean
       public MybatisPlusInterceptor mybatisPlusInterceptor() {
           MybatisPlusInterceptor interceptor = new MybatisPlusInterceptor();
           interceptor.addInnerInterceptor(new OptimisticLockerInnerInterceptor());
           return interceptor;
       }
   
   
   }
   ```

4. 测试

   成功案例

   ```java
   @Test
   // 测试乐观锁成功案例
   public void testOptimisticLocker(){
       // 1. 查询用户信息
       User user = userMapper.selectById(1);
   
       // 2. 修改用户信息
       user.setName("xxxxxxx");
       user.setAge(188888);
   
       // 3. 更新操作
       int i = userMapper.updateById(user);
       System.out.println(i);
       System.out.println(user);
   
   }
   ```

   ![image-20220228164345489](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228164345489.png)

   可以看到version 变成2了

   

5. 测试乐观锁失败案例

```java
// 测试乐观锁失败案例 多线程下
@Test
public void testOptimisticLocker2(){
   // 线程1
    User user = userMapper.selectById(1);
    user.setName("hqy");
    user.setAge(021);
    // 线程2 
    User user2 = userMapper.selectById(1);
    user2.setName("wbm");
    user2.setAge(022);
   // 当线程2 先执行 的时候 version +1
    userMapper.updateById(user2);
   // 线程1 当判断 version 的值以后 发现不对 就执行失败了
    userMapper.updateById(user); // 如果没有乐观锁就会覆盖插队线程的值!

}
```

```bash
# 查询 user id为1 的列
==>  Preparing: SELECT id,name,age,email,create_time,update_time,version FROM user WHERE id=?
==> Parameters: 1(Integer)
<==    Columns: id, name, age, email, create_time, update_time, version
<==        Row: 1, xxxxxxx, 188888, 2308121831@qq.com, 2022-02-28 13:21:59, 2022-02-28 16:41:52, 2
<==      Total: 1

# 如果 version = 2 就修改成功, 这时候的 version确实是=2
==>  Preparing: UPDATE user SET name=?, age=?, email=?, create_time=?, update_time=?, version=? WHERE id=? AND version=?
#  修改成功 并且返回 
==> Parameters: wbm(String), 18(Integer), 2308121831@qq.com(String), 2022-02-28 13:21:59.0(Timestamp), 2022-02-28 16:50:53.325(Timestamp), 3(Integer), 1(Long), 2(Integer)
# 返回1 表示成功
<==    Updates: 1

# 这时候在修改 线程1 发现 version不是2 是3
==>  Preparing: UPDATE user SET name=?, age=?, email=?, create_time=?, update_time=?, version=? WHERE id=? AND version=?
==> Parameters: hqy(String), 17(Integer), 2308121831@qq.com(String), 2022-02-28 13:21:59.0(Timestamp), 2022-02-28 16:50:53.336(Timestamp), 3(Integer), 1(Long), 2(Integer
# 返回0 表示修改失败
<==    Updates: 0

```



## 查询操作

```java
// 查询操作
@Test
public void testSelectById(){
    User user = userMapper.selectById(1L);
    System.out.println(user);
}


// 查询多个用户
@Test
public void testSelectById2(){
    // Arrays 数组工具类
    List<User> users = userMapper.selectBatchIds(Arrays.asList(1, 2, 3));
    users.forEach(System.out::println);
}



// 条件查询 Map     where ?=? and ?=?  
@Test
public  void  testSelectById3(){
    HashMap<String,Object> map = new HashMap<>();
    // 自定义要查询
    map.put("age",18);
    map.put("email","2073568608@qq.com");
    // map 的类型需要 String,Object 否则报错
    userMapper.selectByMap(map);
}
```





## 分页查询

分页在网站使用的十分之多 !

1. 原始的 limit 进行分页
2. pageHelper 第三方插件
3. MyBatisPlus 其实也内置了分页插件 !

> 如何使用

1. 配置拦截器组件即可

   ```java
   @Bean
   public MybatisPlusInterceptor mybatisPlusInterceptor() {
       MybatisPlusInterceptor mybatisPlusInterceptor = new MybatisPlusInterceptor();
       //添加乐观锁
       mybatisPlusInterceptor.addInnerInterceptor(new OptimisticLockerInnerInterceptor());
       
       //添加分页
       mybatisPlusInterceptor.addInnerInterceptor(new PaginationInnerInterceptor(DbType.MYSQL));
       return mybatisPlusInterceptor;
   }
   ```

2. 直接使用Page对象即可

   ```java
   // 测试分页查询
    @Test
    public void testPaginationInner(){
        // 参数1 : 当前页
        // 参数2 :页面大小
        // 使用了分页插件之后, 所有的分页操作也变得简单了
        Page<User> objectPage = new Page<>(1, 5);
        userMapper.selectPage(objectPage,null);
        objectPage.getRecords().forEach(System.out::println); 
    }
   ```



## 删除操作

基本的删除操作

```java
// 测试删除
@Test
public void testDelete(){
    int i = userMapper.deleteById(12); // 根据id删除列
    System.out.println(i);


}

// 测试批量删除
@Test
public void testDelete2(){
   userMapper.deleteBatchIds(Arrays.asList(6,7,8,9,10,11));
}


// 通过map删除
@Test
public void testDelete3(){
    HashMap<String, Object> map = new HashMap<>();
    map.put("name","wbm");
    map.put("email","2073568608@qq.com");
     userMapper.deleteByMap(map);
}
```

在工作中会遇到一些问题 : 逻辑删除



## 逻辑删除

> 物理删除 : 从数据库中直接移除

> 逻辑删除 : 在数据库中没有被移除, 而是通过一个变量让它失效 !  

管理员可以查看被删除的纪录, 防止数据的丢失, 类似于回收站 !

测试一下 : 

1. 在数据表中添加一个deleted 字段

   ![image-20220228215902692](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228215902692.png)



2. 实体类中增加属性 ==高版本不需要配置 只需要注解就好了==

   ```java
   @Data
   @AllArgsConstructor
   @NoArgsConstructor
   public class User {
       // 对应数据库中的主键 (uuid , 自增id, 雪花算法, redis, zookeeper !)
       @TableId(type = IdType.AUTO)
       private Long id;
       private String name;
       private  int age;
       private String email;
       
       @TableLogic // 逻辑删除 注解
       private int deleted;
       
       // 字段添加填充内容
       @TableField(fill = FieldFill.INSERT)
       private Date createTime;
       
       @TableField(fill = FieldFill.INSERT_UPDATE)
       private Date updateTime;
       
       @Version // 乐观锁version注解
       private Integer version;
   
   }
   ```

3. 配置

   ```yaml
   mybatis-plus:
     # 配置逻辑删除
     global-config:
       db-config:
         logic-delete-value: 1    #删除为1
         logic-not-delete-value: 0  # 没有删除为0
   ```

4. 测试一下删除

   ```java
   // 测试删除
   @Test
   public void testDelete(){
       int i = userMapper.deleteById(1); // 走的是更新操作, 并不是删除操作
       System.out.println(i);
   }
   ```

   ==纪录依旧在数据库, 但是值已经变化了==

   ![image-20220228221235871](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228221235871.png)

5. 在查询一下 id为1的列

   ```java
   // 查询操作
   @Test
   public void testSelectById(){
       User user = userMapper.selectById(1);
       System.out.println(user);
   }
   ```

   查询的时候 会自动过滤被逻辑删除的字段

   ![image-20220228221945246](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228221945246.png)



## 添加构造器

十分重要 : Wrapper

我们写一些复杂的sql就可以使用它来替代 !

表

![image-20220228230031251](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228230031251.png)

1. 多个条件 比如 ==查询name 不为空的用户, 并且邮箱不为空的, 年龄大于 21岁的==

   ```java
   @Test
   void contextLoads() {
      // 查询name 不为空的用户, 并且邮箱不为空的, 年龄大于 21岁的
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       // 链式编程
       wrapper
               .isNotNull("name")  // name不为空
               .isNotNull("email") // email 不为空
               .ge("age",21);  // age 大于 21
   
       userMapper.selectList(wrapper).forEach(System.out::println);
   }
   ```

   ![image-20220228230227855](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228230227855.png)

2. 只能 查询一列 数据的方法

   ```java
   @Test
   public void test2(){
       // 查询名字 等于 wbm 的  selectOne 这个方法只能查询一列, 不能像 上面的 age 大于 21 这样会查出多列的数据
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       wrapper.eq("name","wbm"); // 查询一个数据, 出现多个结果使用 list 或者 map
       userMapper.selectOne(wrapper);
   }
   ```

   ![image-20220228231311806](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228231311806.png)



3.  什么字段 在什么之间  比如: ==查询age在 20 ~ 30 岁之间的用户==

   ```java
   @Test
   public void test3(){
       // 查询年龄在 20 ~ 30 岁之间的用户
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       wrapper.between("age",20,30); // 20 到30岁期间的
       Long count = userMapper.selectCount(wrapper);// 查询结果数
       System.out.println(count);
   
   }
   ```

   ![image-20220228232950833](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228232950833.png)



4. 模糊查询 比如: name 中 不包含 m 的列

   ```java
   // 不包含模糊查询
   @Test
   public void test4(){
       // 查询 name 中
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       wrapper.notLike("name","m"); // name 中 不包含 m 的列
       userMapper.selectMaps(wrapper).forEach(System.out::println);
   }
   ```

   ![image-20220228233938441](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228233938441.png)

5. 模糊查询, 查询 :  name 中包含 m的列

   ```java
   // 模糊查询
   @Test
   public void test4(){
       // 查询 name 中
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       wrapper.like("name","m") ;// name 中 包含 m 的列
       userMapper.selectMaps(wrapper).forEach(System.out::println);
   }
   ```

   ![image-20220228234412660](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228234412660.png)



6. 右包含 : 比如查询 name 第一个 字符是 T的

   ```java
   // 右模糊查询
   @Test
   public void test4(){
       // 查询 name 中
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       wrapper.likeRight("name","T") ;// name 中 第一个字符是 T的
       userMapper.selectMaps(wrapper).forEach(System.out::println);
   }
   ```

   ![image-20220228234816103](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228234816103.png)

7. 左包含 : 比如查询 name 最后一个 字符是 m 的

   ```java
   // 左模糊查询
   @Test
   public void test4(){
       // 查询 name 中
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       wrapper.likeLeft("name","m") ;// name 中 最后一个字符是 m的
       userMapper.selectMaps(wrapper).forEach(System.out::println);
   }
   ```

   ![image-20220228235402448](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220228235402448.png)

8. 子查询

   ```java
   @Test
   public void test5(){
       // 查询 name 中
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       // id 在 子查询中查出来的
       wrapper.inSql("id","select id from user where id <3");
       userMapper.selectObjs(wrapper).forEach(System.out::println);
   }
   ```

   ![image-20220301000132124](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220301000132124.png)

9. 排序

   升序

   ```java
   @Test
   public void test6(){
       // 查询 name 中
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       // 通过id进行排序  orderByAsc方法为升序
       wrapper.orderByAsc("id");
       userMapper.selectList(wrapper).forEach(System.out::println);
   }
   ```

   ![image-20220301000834789](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220301000834789.png)

   降序

   ```java
   @Test
   public void test6(){
       // 查询 name 中
       QueryWrapper<User> wrapper = new QueryWrapper<>();
       // 通过id进行排序  orderByDesc方法为降序
       wrapper.orderByDesc("id");
       userMapper.selectList(wrapper).forEach(System.out::println);
   }
   ```

   ![image-20220301000938297](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220301000938297.png)









## 代码自动生成器

依赖

```xml
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-boot-starter</artifactId>
    <version>3.5.0</version>
</dependency>
<!-- mp自动代码生成-->
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-generator</artifactId>
    <version>3.3.2</version>
</dependency>
<!-- velocity 模板引擎, 默认 -->
<dependency>
    <groupId>org.apache.velocity</groupId>
    <artifactId>velocity-engine-core</artifactId>
    <version>2.3</version>
</dependency>

<!-- freemarker 模板引擎 -->
<dependency>
    <groupId>org.freemarker</groupId>
    <artifactId>freemarker</artifactId>
    <version>2.3.31</version>
</dependency>

<!-- beetl 模板引擎 -->
<dependency>
    <groupId>com.ibeetl</groupId>
    <artifactId>beetl</artifactId>
    <version>3.10.0.RELEASE</version>
</dependency>
```

自动代码

```java
package com.wbm;

import com.baomidou.mybatisplus.annotation.FieldFill;
import com.baomidou.mybatisplus.core.exceptions.MybatisPlusException;
import com.baomidou.mybatisplus.core.toolkit.StringPool;
import com.baomidou.mybatisplus.generator.AutoGenerator;
import com.baomidou.mybatisplus.generator.InjectionConfig;
import com.baomidou.mybatisplus.generator.config.*;
import com.baomidou.mybatisplus.generator.config.po.TableFill;
import com.baomidou.mybatisplus.generator.config.po.TableInfo;
import com.baomidou.mybatisplus.generator.config.rules.NamingStrategy;
import com.baomidou.mybatisplus.generator.engine.FreemarkerTemplateEngine;
import org.apache.commons.lang3.StringUtils;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

// 演示例子，执行 main 方法控制台输入模块表名回车自动生成对应项目目录中
public class CodeGenerator {

    /**
     * <p>
     * 读取控制台内容
     * </p>
     */
    public static String scanner(String tip) {
        Scanner scanner = new Scanner(System.in);
        StringBuilder help = new StringBuilder();
        help.append("请输入" + tip + "：");
        System.out.println(help.toString());
        if (scanner.hasNext()) {
            String ipt = scanner.next();
            if (StringUtils.isNotBlank(ipt)) {
                return ipt;
            }
        }
        throw new MybatisPlusException("请输入正确的" + tip + "！");
    }

    public static void main(String[] args) {
        // 代码生成器
        AutoGenerator mpg = new AutoGenerator();

        // 全局配置
        GlobalConfig gc = new GlobalConfig();
        // 获取当前项目路径
        String projectPath = System.getProperty("user.dir");
        gc.setOutputDir(projectPath + "/src/main/java"); // 设置自动生成目录
        gc.setAuthor("wbm"); // 设置作者
        gc.setOpen(false); // 是否打开文件
        // gc.setSwagger2(true); 实体属性 Swagger2 注解
        mpg.setGlobalConfig(gc); // 把全局配置放入

        // 数据源配置
        DataSourceConfig dsc = new DataSourceConfig();
        dsc.setUrl("jdbc:mysql://localhost:3306/mybatis?useUnicode=true&characterEncoding=utf-8&useSSL=true&serverTimezone=Asia/Shanghai");
        // dsc.setSchemaName("public");
        dsc.setDriverName("com.mysql.cj.jdbc.Driver");
        dsc.setUsername("root");
        dsc.setPassword("123456");
        mpg.setDataSource(dsc);

        // 包配置
        PackageConfig pc = new PackageConfig();
        pc.setModuleName(scanner("模块名"));
        pc.setParent("com.wbm");
        mpg.setPackageInfo(pc);

        // 自定义配置
        InjectionConfig cfg = new InjectionConfig() {
            @Override
            public void initMap() {
                // to do nothing
            }
        };

        // 如果模板引擎是 freemarker
        String templatePath = "/templates/mapper.xml.ftl";
        // 如果模板引擎是 velocity
        // String templatePath = "/templates/mapper.xml.vm";

        // 自定义输出配置
        List<FileOutConfig> focList = new ArrayList<>();
        // 自定义配置会被优先输出
        focList.add(new FileOutConfig(templatePath) {
            @Override
            public String outputFile(TableInfo tableInfo) {
                // 自定义输出文件名 ， 如果你 Entity 设置了前后缀、此处注意 xml 的名称会跟着发生变化！！
                return projectPath + "/src/main/resources/mapper/" + pc.getModuleName()
                        + "/" + tableInfo.getEntityName() + "Mapper" + StringPool.DOT_XML;
            }
        });
        /*
        cfg.setFileCreate(new IFileCreate() {
            @Override
            public boolean isCreate(ConfigBuilder configBuilder, FileType fileType, String filePath) {
                // 判断自定义文件夹是否需要创建
                checkDir("调用默认方法创建的目录，自定义目录用");
                if (fileType == FileType.MAPPER) {
                    // 已经生成 mapper 文件判断存在，不想重新生成返回 false
                    return !new File(filePath).exists();
                }
                // 允许生成模板文件
                return true;
            }
        });
        */
        cfg.setFileOutConfigList(focList);
        mpg.setCfg(cfg);

        // 配置模板
        TemplateConfig templateConfig = new TemplateConfig();

        // 配置自定义输出模板
        //指定自定义模板路径，注意不要带上.ftl/.vm, 会根据使用的模板引擎自动识别
        // templateConfig.setEntity("templates/entity2.java");
        // templateConfig.setService();
        // templateConfig.setController();

        templateConfig.setXml(null);
        mpg.setTemplate(templateConfig);

        // 策略配置
        StrategyConfig strategy = new StrategyConfig();
        strategy.setNaming(NamingStrategy.underline_to_camel);
        strategy.setColumnNaming(NamingStrategy.underline_to_camel);
       // strategy.setSuperEntityClass("你自己的父类实体,没有就不用设置!");
        strategy.setEntityLombokModel(true);
        strategy.setRestControllerStyle(true);
        // 公共父类
        //strategy.setSuperControllerClass("你自己的父类控制器,没有就不用设置!");
        // 写于父类中的公共字段
        strategy.setSuperEntityColumns("id");
        strategy.setInclude(scanner("表名，多个英文逗号分割").split(","));
        strategy.setControllerMappingHyphenStyle(true);
        strategy.setTablePrefix(pc.getModuleName() + "_");
        // 设置逻辑删除的字段
        strategy.setLogicDeleteFieldName("deleted");
        // 设置 乐观锁
        strategy.setVersionFieldName("version");
        // 自动lombok
        strategy.setEntityLombokModel(true);

        // 自动填充配置
        TableFill createTime = new TableFill("create_time", FieldFill.INSERT); // 创建的时间
        TableFill updateTime = new TableFill("update_time", FieldFill.INSERT_UPDATE); // 更新列的时候会,刷新更新时间
        ArrayList<TableFill> list = new ArrayList<>();
        list.add(updateTime);
        list.add(createTime);
        strategy.setTableFillList(list);

        mpg.setStrategy(strategy);
        mpg.setTemplateEngine(new FreemarkerTemplateEngine());
        mpg.execute();
    }

}
```

可以生成多个表

![image-20220301150506525](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220301150506525.png)







