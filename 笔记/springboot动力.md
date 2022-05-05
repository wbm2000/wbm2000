# SpringBoot

# 第1章Spring Boot 框架入门

## 1.1 Spring Boot 简介

  **Spring Boot 是 Spring 家族中的一个全新的框架，它用来简化 Spring 应用程序的创建和 开发过程，也可以说 Spring Boot 能简化我们之前采用 SpringMVC + Spring + MyBatis 框架进行 开发的过程。 在以往我们采用 SpringMVC + Spring + MyBatis 框架进行开发的时候，搭建和整合三大框 架，我们需要做很多工作，比如配置 web.xml，配置 Spring，配置 MyBatis，并将它们整合在 一起等，而 Spring Boot 框架对此开发过程进行了革命性的颠覆，完全抛弃了繁琐的 xml 配 置过程，采用大量的默认配置简化我们的开发过程。 所以采用 Spring Boot 可以非常容易和快速地创建基于 Spring 框架的应用程序，它让编 码变简单了，配置变简单了，部署变简单了，监控变简单了。正因为 Spring Boot 它化繁为 简，让开发变得极其简单和快速，所以在业界备受关注。**



## 1.2 Spring Boot 的特性

-  能够快速创建基于 Spring 的应用程序

-  能够直接使用 java main 方法启动内嵌的 Tomcat 服务器运行 Spring Boot 程序，不需 要部署 war 包文件

-  提供约定的 starter POM 来简化 Maven 配置，让 Maven 的配置变得简单

-  自动化配置，根据项目的 Maven 依赖配置，Spring boot 自动配置 Spring、Spring mvc 等

-  提供了程序的健康检查等功能 ➢ 基本可以完全不使用 XML 配置文件，采用注解配置



## 1.3 Spring Boot 四大核心

### 1.3.1 自动配置

### 1.3.2 起步依赖 

### 1.3.3 Actuator

### 1.3.4 命令行界面





# 第2章Spring Boot 入门案例

### 2.1.1 开发步骤

 **项目名称：001-springboot-first**

1. 创建一个 Module，选择类型为 Spring Initializr 快速构建 一个springboot项目 设置 GAV 坐标及 pom 配置信息

   ![image-20220107202733237](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107202733237.png)

   ![image-20220107204721529](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107204721529.png)

2. 选择 Spring Boot 版本及依赖   

   会根据选择的依赖自动添加起步依赖并进行自动配置

   ![image-20220107205239302](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107205239302.png)

   

3. 项目创建完毕，如下

   <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107205432638.png" alt="image-20220107205432638" style="zoom:80%;" />

   

4. 项目结构

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220107205556106.png" alt="image-20220107205556106" style="zoom:50%;" />



**static：存放静态资源，如图片、CSS、JavaScript 等**

**templates：存放 Web 页面的模板文件** 

**application.properties/application.yml 用于存放程序的各种依赖模块的配置信息，比如 服务 端口，数据库连接配置等**







## 2.2入门案例 

**项目名称：002-springboot-springmvc**



### 2.2.2 创建一个新的 Module，选择类型为 Spring Initializr

![image-20220108125405136](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108125405136.png)

### 2.2.3 指定 GAV 及 pom 配置信息



### 2.2.4 选择 Spring Boot 版本及依赖 

**会根据选择的依赖自动添加起步依赖并进行自动配置**

![image-20220108125554807](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108125554807.png)





### 2.2.5 对 POM.xml 文件进行解释

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.2.1.RELEASE</version> <!-- 这里可以修改版本号 -->
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

    <!--当前项目的 GAV 坐标-->
    <groupId>com.wbm</groupId>
    <artifactId>springboot-springmvc</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <!--maven 项目名称，可以删除-->
    <name>002-springboot-springmvc</name>

    <!--maven 项目描述，可以删除-->
    <description>Demo project for Spring Boot</description>

    <!--maven 属性配置，可以在其它地方通过${}方式进行引用-->
    <properties>
        <java.version>1.8</java.version>
    </properties>


    <dependencies>

        <!--SpringBoot 框架 web 项目起步依赖，通过该依赖自动关联其它依赖，不需要我们一个一个去添加了-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!--SpringBoot 框架的测试起步依赖，例如：junit 测试，如果不需要的话可以删除-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>

    </dependencies>

    <build>
        <plugins>
            <!--SpringBoot 提供的打包编译等插件-->
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
            
        </plugins>
    </build>

</project>
```



### 2.2.6 对 SpringBoot 项目结构进行说明

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108130721600.png" alt="image-20220108130721600" style="zoom:%;" />





- **.mvn|mvnw|mvnw.cmd：使用脚本操作执行 maven 相关命令，国内使用较少，可删 除** 
- **.gitignore：使用版本控制工具 git 的时候，设置一些忽略提交的内容** 
- **static|templates：后面模板技术中存放文件的目录** 
- **application.properties：SpringBoot 的配置文件，很多集成的配置都可以在该文件中 进行配置，例如：Spring、springMVC、Mybatis、Redis 等。目前是空的**
-  **Application.java：SpringBoot 程序执行的入口，执行该程序中的 main 方法，SpringBoot 就启动了**



### 2.2.7 创建一个 Spring MVC 的 Spring BootController

 **SpringBootController 类所在包：com.wbm.controller**

**先创建一个controller包, 然后在这个包中创建SpringBootController**

```java
package com.wbm.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class SpringController {

    @ResponseBody
    @RequestMapping("/hello")
    public String hello(){
        return "Hello World";
    }
}
```

**注意：新创建的类一定要位于 Application 同级目录或者下级目录，否则 SpringBoot 加 载不到。**





### 2.2.8 在 IDEA 中右键，运行 Application 类中的 main 方法

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108131807438.png" alt="image-20220108131807438" style="zoom:50%;" />

**通过在控制台的输出，可以看到启动 SpringBoot 框架，会启动一个内嵌的 tomcat，端 口号为 8080，上下文根为空**

**Tomcat started on port(s): 8080 (http) with context path ''**



### 2.2.9 在浏览器中输入 http://localhost:8080/hello 访问

![image-20220108132123864](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108132123864.png)



## 2.3入门案例分析

1.  **Spring Boot 的父级依赖 spring-boot-starter-parent 配置之后，当前的项目就是 Spring Boot 项目**
2. **spring-boot-starter-parent 是一个 Springboot 的父级依赖，开发 SpringBoot 程序都需 要继承该父级项目，它用来提供相关的 Maven 默认依赖，使用它之后，常用的 jar 包依赖可以省去 version 配置** 
3. **Spring Boot 提供了哪些默认 jar 包的依赖，可查看该父级依赖的 pom 文件**
4.  **如果不想使用某个默认的依赖版本，可以通过 pom.xml 文件的属性配置覆盖各个 依赖项，比如覆盖 Spring 版本  5.0.0.RELEASE** 
5. **@SpringBootApplication 注解是 Spring Boot 项目的核心注解，主要作用是开启 Spring 自动配置，如果在 Application 类上去掉该注解，那么不会启动 SpringBoot 程序** 
6. **main 方法是一个标准的 Java 程序的 main 方法，主要作用是作为项目启动运行的入 口** 
7. **@Controller 及 @ResponseBody 依然是我们之前的 Spring MVC，因为 Spring Boot 的里面依然是使用我们的 Spring MVC + Spring + MyBatis 等框架**



## 2.4 Spring Boot 的核心配置文件

 **Spring Boot 的核心配置文件用于配置 Spring Boot 程序，名字必须以 application 开始**



###  2.4.1 核心配置格式 

#####  **.properties 文件（默认采用该文件）**

 在 002-springboot-springmvc 项目基础上，进行修改

**项目名称：003-springboot-port-context-path** 

通过修改 application.properties 配置文件，在修改默认 tomcat 端口号及项目上下文件根 

键值对的 properties 属性文件配置方式

```properties
#设置内嵌 Tomcat 端口号
server.port=9090
#配置项目上下文根
server.servlet.context-path=/wbm
```



**配置完毕之后，启动浏览器测试**

![image-20220108134935189](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108134935189.png)

**页面显示**

http://localhost:9090/wbm/hello

![image-20220108134719701](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108134719701.png)

#####  .yml 文件 

项目名称：**004-springboot-yml**，在 003 项目基础之上 yml 是一种 yaml 格式的配置文件，主要采用一定的空格、换行等格式排版进行配置。

 yaml 是一种直观的能够被计算机识别的的数据序列化格式，容易被人类阅读，yaml 类 似于 xml，但是语法比 xml 简洁很多，值与前面的冒号配置项必须要有一个空格， yml 后 缀也可以使用 yaml 后缀

![image-20220108140304540](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108140304540.png)

注意：当两种格式配置文件同时存在，使用的是.properties 配置文件，为了演示 yml，可以 先将其改名，重新运行 Application，查看启动的端口及上下文根

```yaml
#设置内嵌 Tomcat 端口号
server:
  port: 9999
```

![image-20220108140433584](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108140433584.png)





### 2.4.2 多环境配置 

在实际开发的过程中，我们的项目会经历很多的阶段（开发->测试->上线），每个阶段 的配置也会不同，例如：端口、上下文根、数据库等，那么这个时候为了方便在不同的环境 之间切换，SpringBoot 提供了多环境配置，具体步骤如下



**项目名称：005-springboot-multi-environment**

为每个环境创建一个配置文件，命名必须以 application-环境标识.properties|yml

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108141931935.png" alt="image-20220108141931935" style="zoom:40%;" />





application-cs.properties

```yaml
#测试环境
#配置内嵌 Tomcat 端口号
server.port=8081
#配置项目的上下文根
server.servlet.context-path=/wbm3
```



application-kf.properties

```yaml
#开发环境

#设置内嵌 Tomcat 默认端口号
server.port=8080
#设置项目的上下文根
server.servlet.context-path=/wbm1
```



application-sc.properties

```yaml
#生产环境
#配置内嵌 Tomcat 默认端口号
server.port=80
#配置项目上下文根
server.servlet.context-path=/wbm2
```



在总配置文件 application.properties 进行环境的激活

```yaml
#SpringBoot 的总配置文件
#激活开发环境
#spring.profiles.active=kf
#激活测试环境
#spring.profiles.active=cs
#激活生产环境
spring.profiles.active=sc
```

**等号右边的值和配置文件的环境标识名一致，可以更改总配置文件的配置，重新运行 Application，查看启动的端口及上下文根**

![image-20220108142756698](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220108142756698.png)



**yaml配置差不多这里省略!!!**





### 2.4.3 Spring Boot 自定义配置 

**在 SpringBoot 的核心配置文件中，除了使用内置的配置项之外，我们还可以在自定义配 置，然后采用如下注解去读取配置的属性值**

##### @Value 注解

**项目名称：007-springboot-custom-configuration**

 用于逐个读取 application.properties 中的配置



**案例演示** 

- 在核心配置文件 applicatin.properties 中，添加两个自定义配置项 school.name 和 website。在 IDEA 中可以看到这两个属性不能被 SpringBoot 识别，背景是桔色的

  ![image-20220109215009567](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220109215009567.png)

  ```properties
  school.name=wbm
  website=www.baidu.com
  ```

  application.yml 格式配置文件

  ![image-20220109215134792](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220109215134792.png)

- 在 SpringBootController 中定义属性，并使用@Value 注解或者自定义配置值，并对其方法进行测试

```java
package com.example.springbootcustomconfiguration.controller;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class TestController {

    @Value("${school.name}")
    private String schoolName;

    @Value("${website}")
    private String websit;


    @ResponseBody
    @RequestMapping("/testvalue")
    public String test(){
        return  schoolName+"_________"+websit;
    }

}
```



- 运行 Application，在浏览器中进行测试

  ![image-20220109215243794](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220109215243794.png)





##### @ConfigurationProperties

项目名称：008-springboot-custom-configuration

将整个文件映射成一个对象，用于自定义配置项比较多的情况



**案例演示 **

- application.properties 配置文件

```properties 
school.name=ssm
school.websit=http://www.baidu.com
```



- 在 com.abc.springboot.config 包下创建 ConfigInfo 类，并为该类加上 Component 和 ConfigurationProperties 注解，并在 ConfigurationProperties 注解中添加属性 prefix， 作用可以区分同名配置

```java
package com.example.springbootcustomconfiguration.config;

import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.stereotype.Controller;
// 这里的school对应者 application.properties 配置文件 中的school  
@ConfigurationProperties(prefix = "school")
@Controller
public class ConfigInfo {
    private String name;
    private String websit;

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getWebsit() {
        return websit;
    }
    public void setWebsit(String websit) {
        this.websit = websit;
    }

}
```



application.yml 配置文件

```yaml
school:
 name: ABC
 websit: http://www.baidu.com
```



在 SpringBootController 中注入 ConfigInfo 配置类 

```java
// 自动注入
@Autowired
private ConfigInfo configInfo;
```

修改 SpringBootController 类中的测试方法

```java
@ResponseBody
@RequestMapping("/test")
public String test(){
    return configInfo.getName()+"________"+configInfo.getWebsit();
}
```



全

```java
package com.example.springbootcustomconfiguration.controller;

import com.example.springbootcustomconfiguration.config.ConfigInfo;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class SpringBootController {

    // 自动注入
    @Autowired
    private ConfigInfo configInfo;

    @ResponseBody
    @RequestMapping("/test")
    public String test(){
        return configInfo.getName()+"________"+configInfo.getWebsit();
    }

}
```



- 运行 Application，在浏览器中进行测试

![image-20220109221326266](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220109221326266.png)





##### 警告解决

- 在 ConfigInfo 类中使用了 ConfigurationProperties 注解后，IDEA 会出现一个警告， 不影响程序的执行 

![image-20220109221507751](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220109221507751.png)

-  点击 open documentnation 跳转到网页，在网页中提示需要加一个依赖，我们将这 个依赖拷贝，粘贴到 pom.xml 文件中

```xml
<!--解决使用@ConfigurationProperties 注解出现警告问题-->
<dependency>
 <groupId>org.springframework.boot</groupId>
 <artifactId>spring-boot-configuration-processor</artifactId>
 <optional>true</optional>
</dependency>
```



##### 中文乱码

如果在 SpringBoot 核心配置文件中有中文信息，会出现乱码： 

-  一般在配置文件中，不建议出现中文（注释除外） 

-  如果有，可以先转化为 ASCII 码

  <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220109223022452.png" alt="image-20220109223022452" style="zoom:50%;" />





## 2.5 Spring Boot 前端使用 JSP 

**项目名称：009-springboot-jsp**

### 2.5.4 在 pom.xml 文件中配置以下依赖项

```xml
<!--引入 Spring Boot 内嵌的 Tomcat 对 JSP 的解析包，不加解析不了 jsp 页面-->
<!--如果只是使用 JSP 页面，可以只添加该依赖-->
<dependency>
 <groupId>org.apache.tomcat.embed</groupId>
 <artifactId>tomcat-embed-jasper</artifactId>
</dependency>
<!--如果要使用 servlet 必须添加该以下两个依赖-->
<!-- servlet 依赖的 jar 包-->
<dependency>
 <groupId>javax.servlet</groupId>
 <artifactId>javax.servlet-api</artifactId>
</dependency>
<dependency>
 <groupId>javax.servlet.jsp</groupId>
 <artifactId>javax.servlet.jsp-api</artifactId>
 <version>2.3.1</version>
</dependency>
<!--如果使用 JSTL 必须添加该依赖-->
<!--jstl 标签依赖的 jar 包 start-->
<dependency>
 <groupId>javax.servlet</groupId>
 <artifactId>jstl</artifactId>
</dependency>
```



### 2.5.5 在 pom.xml 的 build 标签中要配置以下信息

SpringBoot 要求 jsp 文件必须编译到指定的 META-INF/resources 目录下才能访问，否则 访问不到。其实官方已经更建议使用模板技术

````xml
<!--
 SpringBoot 要求 jsp 文件必须编译到指定的 META-INF/resources 目录下才能访问，否则访问
不到。
 其它官方已经建议使用模版技术（后面会课程会单独讲解模版技术）
-->
<resources>
 <resource>
     <!--源文件位置-->
    <directory>src/main/webapp</directory>
    <!--指定编译到 META-INF/resources，该目录不能随便写-->
    <targetPath>META-INF/resources</targetPath>
    <!--指定要把哪些文件编译进去，**表示 webapp 目录及子目录，*.*表示所有文件-->
     <includes>
          <include>**/*.*</include>
     </includes>
 </resource>
</resources>
````



### 2.5.6 在 application.properties 文件配置 Spring MVC 的视图展示为 jsp，这里相当于 Spring MVC 的配置

````properties
#配置 SpringMVC 视图解析器
#其中：/ 表示目录为 src/main/webapp
spring.mvc.view.prefix=/
spring.mvc.view.suffix=.jsp
````

yaml配置

```yaml
#配置 SpringMVC 视图解析器
#其中：/ 表示目录为 src/main/webapp
spring:
 mvc:
 view:
 prefix: /
 suffix: .jsp
```



### 2.5.7 在 com.example.springboot.controller 包下创建 JspController 类，并 编写代码

```java
package com.example.springbootjsp.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class JspController {
    @GetMapping("/indexjsp")
   public String indexJsp(Model model){
       model.addAttribute("indexJsp","SpringBoot 前端使用 JSP 页面 !!!");
       return "index";
   }
}
```



### 2.5.8 在 src/main 下创建一个 webapp 目录，然后在该目录下新建 index.jsp 页面

如果在webapp目录下右键，没有创建jsp的选项，可以在Project Structure中指定webapp 为 Web Resource Directory

![image-20220110155356211](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110155356211.png)





### 2.5.9 在 jsp 中获取 Controller 传递过来的数据

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>SpringBoot 使用jsp</title>
</head>
<body>
     ${indexJsp} <!-- model里面的 参数 -->
</body>
</html>
```



### 2.5.10 重新运行 Application，通过浏览器访问测试

![image-20220110155540649](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110155540649.png)



# 第3章Spring Boot 框架 Web 开发



## 3.1Spring Boot 集成 MyBatis 

项目名称：010-springboot-web-mybatis

### 3.1.1 案例思路

 通过 SpringBoot +MyBatis 实现对数据库学生表的查询操作 

### 3.1.2 实现步骤

1. 准备数据库

   - 启动系统上的 mySQL 服务器，通过 SQLyong连接

     ![image-20220110160744790](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110160744790.png)

   - 创建新的数据库 springboot，指定数据库字符编码为 utf-8

   - 创建表 t_student 

     ![image-20220110161423018](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110161423018.png)

   - 向表中插入数据

     ![image-20220110161624976](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110161624976.png)

     

2. 创建 010-springboot-web-mybatis 项目

   - 创建一个新的 SpringBoot 的 Module

     <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110161935664.png" alt="image-20220110161935664" style="zoom:50%;" />

   - 选择 SpringBoot 版本以及 web 依赖

     <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110162006480.png" alt="image-20220110162006480" style="zoom:50%;" />



3. 在 pom.xml 中添加相关 jar 依赖

   ```xml
   <!--MyBatis 整合 SpringBoot 的起步依赖-->
   <dependency>
       <groupId>org.mybatis.spring.boot</groupId>
       <artifactId>mybatis-spring-boot-starter</artifactId>
       <version>2.0.0</version>
   </dependency>
   <!--MySQL 的驱动依赖-->
   <dependency>
       <groupId>mysql</groupId>
       <artifactId>mysql-connector-java</artifactId>
   </dependency>
   ```



4. 在 Springboot 的核心配置文件 application.properties 中配 置数据源

   ```properties
   #配置数据库的连接信息
   #注意这里的驱动类有变化
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
   spring.datasource.url=jdbc:mysql://localhost:3306/springboot?useUnicode=true&characterEncoding=UTF-8&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=GMT%2B8
   spring.datasource.username=root
   spring.datasource.password=123456
   ```



5. 开发代码

   - pojo类

     ```java
     package com.example.springbootwebmybatis.pojo;
     
     
     import lombok.AllArgsConstructor;
     import lombok.Data;
     import lombok.NoArgsConstructor;
     
     @Data
     @AllArgsConstructor
     @NoArgsConstructor
     public class Student {
         private int id;
         private String name;
         private int age;
     }
     ```

   - 使用 Mybatis 反向工程生成接口、映射文件以及实体 bean

     ![image-20220110163005424](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110163005424.png)

     - Mapper接口

       ````java
       package com.example.springbootwebmybatis.mapper;
       
       import com.example.springbootwebmybatis.pojo.Student;
       import org.apache.ibatis.annotations.Mapper;
       import org.springframework.stereotype.Controller;
       /**
       在 Mybatis 反向工程生成的 StudentMapper 接口上加一个 Mapper 注解
       @Mapper 作用：mybatis 自动扫描数据持久层的映射文件及 DAO 接口的关系
       */
       @Mapper
       public interface StudentMapper {
           /**
            * 根据学生id获取学生详情
            * @param id
            * @return
            */
           Student queryStudentById (Integer id);
       }
       ````

       

     - xml

       ```xml
       <?xml version="1.0" encoding="UTF-8" ?>
       <!DOCTYPE mapper
               PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
               "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
       
       <mapper namespace="com.example.springbootwebmybatis.mapper.StudentMapper">
           <!--id = 方法名字  parameterType= 参数  resultType= 返回类型  -->
           <select id="queryStudentById" parameterType="int" resultType="com.example.springbootwebmybatis.pojo.Student">
               select *
               from  springboot.t_student
               where id=#{id};
           </select>
       
       </mapper>
       ```

   - 在 service 包下创建 service 接口并编写代码

     ```java
     package com.example.springbootwebmybatis.service;
     
     import com.example.springbootwebmybatis.pojo.Student;
     
     public interface StudentService {
         /**
          * 根据学生id获取学生详情
          * @param id
          * @return
          */
         Student queryStudentById (Integer id);
     }
     ```

   - 在 service.impl 包下创建 service 接口并编写代码

     ```java
     package com.example.springbootwebmybatis.service.impl;
     
     import com.example.springbootwebmybatis.mapper.StudentMapper;
     import com.example.springbootwebmybatis.pojo.Student;
     import com.example.springbootwebmybatis.service.StudentService;
     import org.springframework.beans.factory.annotation.Autowired;
     import org.springframework.stereotype.Service;
     
     @Service
     public class StudentServiceImpl implements StudentService {
     
         @Autowired
         private StudentMapper studentMapper;
     
         @Override
         public Student queryStudentById(Integer id) {
             return studentMapper.queryStudentById(id);
         }
     }
     
     ```

   - 在controller 包下创建 StudentController 并编写代码

     ```java
     package com.example.springbootwebmybatis.controller;
     
     import com.example.springbootwebmybatis.pojo.Student;
     import com.example.springbootwebmybatis.service.StudentService;
     import com.example.springbootwebmybatis.service.impl.StudentServiceImpl;
     import org.springframework.beans.factory.annotation.Autowired;
     import org.springframework.stereotype.Controller;
     import org.springframework.web.bind.annotation.RequestMapping;
     import org.springframework.web.bind.annotation.ResponseBody;
     
     @Controller
     public class StudentController {
     
         @Autowired
         private StudentService students;
     
         @ResponseBody
         @RequestMapping("/test")
         public Object mybatisTest(){
             Student student = this.students.queryStudentById(2);
             return student;
         }
     
     
     
     }
     ```

   - 注意：默认情况下，Mybatis 的 xml 映射文件不会编译到 target 的 class 目录下，所 以我们需要在 pom.xml 文件中配置 resource(在build 标签里面使用)

     ```xml
     <resources>
       <resource>
       <directory>src/main/java</directory>
       <includes>
         <include>**/*.xml</include>
       </includes>
         </resource>
     </resources>
     ```

6. 启动 Application 应用，浏览器访问测试运行

   ![image-20220110201902987](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110201902987.png)













### 3.1.3 DAO 其它开发方式

1. 在 运 行 的 主 类 上 添 加 注 解 包 扫 描 @MapperScan("com.example.springbootwebmybatis.mapper") 

   - 注释掉 StudentMapper 接口上的@Mapper 注解

   ![image-20220110202042421](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110202042421.png)

   - 在运行主类 Application 上加@MapperScan("com.example.springbootwebmybatis.mappe")

     - ```java
       @MapperScan("com.example.springbootwebmybatis.mapper")
       @SpringBootApplication
       public class Application {
       
           public static void main(String[] args) {
               SpringApplication.run(Application.class, args);
           }
       
       }
       ```

     - 或 

       ```java
       
       //Mybatis 提供的注解：扫描数据持久层的 mapper 映谢配置文件,DAO 接口上就不用加@Mapper
       //basePackages 通常指定到数据持久层包即可
       @MapperScan(basePackages = "com.abc.springboot.mapper")
       @SpringBootApplication
       public class Application {
       
           public static void main(String[] args) {
               SpringApplication.run(Application.class, args);
           }
       
       }
       ```

   - 运行测试

     ![image-20220110202644995](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110202644995.png)



2. 将接口和映射文件分开

   **项目名称：011-springboot-web-mybatis**

   因为 SpringBoot 不能自动编译接口映射的 xml 文件，还需要手动在 pom 文件中指定， 所以有的公司直接将映射文件直接放到 resources 目录下

   - 在 resources 目录下新建目录 mapper 存放映射文件，将 StudentMapper.xml 文件移 到 resources/mapper 目录下

     ![image-20220110205650829](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110205650829.png)

   - 在 application.properties 配置文件中指定映射文件的位置，这个配置只有接口和映 射文件不在同一个包的情况下，才需要指定

     ```properties
     # 指定 Mybatis 映射文件的路径
     mybatis.mapper-locations=classpath:mapper/*.xml
     ```

     测试:

     ![image-20220110205832307](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220110205832307.png)



## 3.2Spring Boot 事务支持

 Spring Boot 使用事务非常简单，底层依然采用的是 Spring 本身提供的事务管理

- 在入口类中使用注解 @EnableTransactionManagement 开启事务支持 

- 在访问数据库的 Service 方法上添加注解 @Transactional 即可



### 3.2.1 案例思路

通过 SpringBoot +MyBatis 实现对数据库学生表的更新操作，在 service 层的方法中构建 异常，查看事务是否生效

该项目是在 上面项目 的基础上添加新增方法，在新增方法中进行案例的演示

@Transactional 注解相信大家并不陌生，平时开发中很常用的一个注解，它能保证方法内多个数据库操作要么同时成功、要么同时失败。使用@Transactional注解时需要注意许多的细节，不然你会发现@Transactional总是莫名其妙的就失效了。



### 3.2.2 实现步骤

1. 现在StudentMapper中添加实现对数据库学生表的更新操作的方法

   - mapper

     ```java
     package com.example.springbootwebmybatis.mapper;
     
     import com.example.springbootwebmybatis.pojo.Student;
     import org.apache.ibatis.annotations.Mapper;
     import org.springframework.stereotype.Controller;
     
     @Mapper
     public interface StudentMapper {
         /**
          * 根据学生id获取学生详情
          * @param id
          * @return
          */
         Student queryStudentById (Integer id);
     
     
         /**
          * 根据学生标识更新学生信息
          * @param student
          * @return
          */
         int modifyStudentById(Student student);
     
     
     }  
     ```

     

   - xml

     ```xml
     <?xml version="1.0" encoding="UTF-8" ?>
     <!DOCTYPE mapper
             PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
             "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
     
     <mapper namespace="com.example.springbootwebmybatis.mapper.StudentMapper">
         <!--id = 方法名字  parameterType= 参数  resultType= 返回类型  -->
         <select id="queryStudentById" parameterType="int" resultType="com.example.springbootwebmybatis.pojo.Student">
             select *
             from  springboot.t_student
             where id=#{id};
         </select>
     
             <!--因为增删改 返回的都是int类型 所以这里可以省略掉返回值的参数 -->
         <update id="modifyStudentById"   parameterType="com.example.springbootwebmybatis.pojo.Student" >
             update springboot.t_student
             set name=#{name},age=#{age}
             where id=#{id};
         </update>
     </mapper>
     ```



2. 在 StudentService 接口中添加更新学生方法 , 并且在 StudentServiceImpl 接口实现类中对更新学生方法进 行实现，并构建一个异常，同时在该方法上加@Transactional 注解

   - 接口

     ```java
     package com.example.springbootwebmybatis.service;
     
     import com.example.springbootwebmybatis.pojo.Student;
     
     public interface StudentService {
         /**
          * 根据学生id获取学生详情
          * @param id
          * @return
          */
         Student queryStudentById (Integer id);
     
         /**
          * 根据学生标识更新学生信息
          * @param student
          * @return
          */
         int modifyStudentById(Student student);
     }
     ```

   - 实现类

     ```java
     package com.example.springbootwebmybatis.service.impl;
     
     import com.example.springbootwebmybatis.mapper.StudentMapper;
     import com.example.springbootwebmybatis.pojo.Student;
     import com.example.springbootwebmybatis.service.StudentService;
     import org.springframework.beans.factory.annotation.Autowired;
     import org.springframework.stereotype.Service;
     import org.springframework.transaction.annotation.Transactional;
     
     @Transactional
     @Service
     public class StudentServiceImpl implements StudentService {
     
         @Autowired
         private StudentMapper studentMapper;
     
         @Override
         public Student queryStudentById(Integer id) {
             return studentMapper.queryStudentById(id);
         }
     
         @Override
         public int modifyStudentById(Student student) {
             return studentMapper.modifyStudentById(student);
         }
     }
     ```



3. 在 StudentController 中添加更新学生的方法

   ```java
   package com.example.springbootwebmybatis.controller;
   
   import com.example.springbootwebmybatis.pojo.Student;
   import com.example.springbootwebmybatis.service.StudentService;
   import com.example.springbootwebmybatis.service.impl.StudentServiceImpl;
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.stereotype.Controller;
   import org.springframework.web.bind.annotation.RequestMapping;
   import org.springframework.web.bind.annotation.ResponseBody;
   
   @Controller
   public class StudentController {
   
       @Autowired
       private StudentService students;
   
       @ResponseBody
       @RequestMapping("/test")
       public Object mybatisTest(){
           Student student = this.students.queryStudentById(1);
           return student;
       }
   
   
       @ResponseBody
       @RequestMapping("/up")
       public Object mybatisUp(){
           int count=0;
   
           try {
               Student student = new Student();
               student.setId(1);
               student.setAge(20);
               student.setName("wbm");
               count=students.modifyStudentById(student);
               if (count==1) {
                   System.out.println("修改成功");
               }else {
                   System.out.println("失败");
               }
           } catch (Exception e) {
               e.printStackTrace();
           }
           return count;
       }
   
   
   
   }
   ```



4. 在Application类上加@EnableTransactionManagement 开启事务支持

   @EnableTransactionManagement 可选，但是业务方法上必须添加@Transactional 事务才生效

   ![image-20220111153717200](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220111153717200.png)

   

5. 测试

   - 先使用查看语句看看

     ![image-20220111154020699](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220111154020699.png)

   - 使用更新

   ![image-20220111153837284](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220111153837284.png)

   ![image-20220111153857675](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220111153857675.png)

   - 在次查看

     发现成功修改

     ![image-20220111154315291](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220111154315291.png)

   - 数据库

     ![image-20220111154354947](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220111154354947.png)

  



6. 注释掉 StudentServiceImpl 上的@Transactional 测试

   测试:

   ![image-20220111155731109](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220111155731109.png)



## 3.3 Spring Boot 下的 Spring MVC

**Spring Boot 下的 Spring MVC 和之前的 Spring MVC 使用是完全一样的，主要有以下注解** 

### 3.3.1 @Controller Spring MVC 的注解，处理 http 请求 



### 3.3.2 @RestController Spring 4 后新增注解@ResponseBody

**是@Controller 注解功能的增强 是 @Controller 与@ResponseBody 的组合注解 如果一个 Controller 类添加了@RestController，那么该 Controller 类下的所有方法都相当 于添加了@ResponseBody 注解 用于返回字符串或 json 数据**



### 3.3.3 @RequestMapping（常用）

 **支持 Get 请求，也支持 Post 请求**



### 3.3.4 @GetMapping 

**RequestMapping 和 Get 请求方法的组合 只支持 Get 请求 Get 请求主要用于查询操作**



###  **3.3.5 @PostMapping**

 **RequestMapping 和 Post 请求方法的组合 只支持 Post 请求 Post 请求主要用户新增数据**



###  **3.3.6 @PutMapping** 

**RequestMapping 和 Put 请求方法的组合 只支持 Put 请求 Put 通常用于修改数据**



###  **3.3.7 @DeleteMapping** 

**RequestMapping 和 Delete 请求方法的组合 只支持 Delete 请求 通常用于删除数据**



### 3.3.8 综合案例 

项目名称：013-springboot-springmvc 项目集成

 springmvc 项目作用：演示常见的 SpringMVC 注解

1. 创建一个 MVCController，里面使用上面介绍的各种注解 接收不同的请求

   ```java
   package com.example.springbootspringmvc.controller;
   
   
   import org.springframework.web.bind.annotation.*;
   
   //RestController 注解相当于加了给方法加了@ResponseBody 注解，所以是不能跳转页面的，只能返回字符串或者 json 数据
   @RestController
   public class MVCController {
   
       @GetMapping(value = "/get")
       public String get() {
           return "@GetMapping 注解,通常查询时使用";
       }
       @PostMapping(value = "/post")
       public String add() {
           return "@PostMapping 注解，通常新增时使用";
       }
       @PutMapping(value = "/put")
       public String modify() {
           return "@PutMapping 注解，通常更新数据时使用";
       }
       @DeleteMapping(value = "/delete")
       public String remove() {
           return "@DeleteMapping 注解，通常删除数据时使用";
       }
   }
   ```

2. 启动应用，在浏览器中输入不同的请求进行测试

 但是浏览器输入地址，默认发送的只能是 get 请求

![image-20220112150006547](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112150006547.png)

可以看到put是404

![image-20220112150038396](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112150038396.png)



3. Http 接口请求工具 Postman 介绍

   因为通过浏览器输入地址，默认发送的只能是 get 请求，通过 Postman 工具，可以模拟 发送不同类型的请求，并查询结果，在安装的时候，有些机器可能会需要安装 MicroSort .NET Framework

   ![image-20220112150325414](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112150325414.png)

4. 使用 Postman 对其它请求类型做个测试

   - put

     ![image-20220112150414489](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112150414489.png)

   - post

   ![image-20220112150452959](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112150452959.png)

   - delete

     ![image-20220112150526001](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220112150526001.png)



## 3.4Spring Boot 实现 RESTful

### 3.4.1 认识 RESTFul

**REST（英文：Representational State Transfer，简称 REST）**

一种互联网软件架构设计的风格，但它并不是标准，它只是提出了一组客户端和服务器 交互时的架构理念和设计原则，基于这种理念和原则设计的接口可以更简洁，更有层次，REST 这个词，是 Roy Thomas Fielding 在他 2000 年的博士论文中提出的。

 任何的技术都可以实现这种理念，如果一个架构符合 REST 原则，就称它为 RESTFul 架 构 

比如我们要访问一个 http 接口：http://localhost:8080/boot/order?id=1021&status=1 

采用 RESTFul 风格则 http 地址为：http://localhost:8080/boot/order/1021/1





### 3.4.2 Spring Boot 开发 RESTFul

Spring boot 开发 RESTFul 主要是几个注解实现

1. @**PathVariable**

   获取 url 中的数据 

   **该注解是实现 RESTFul 最主要的一个注解**

   

2. @**PostMapping**

   接收和处理 Post 方式的请求

   

3. @**DeleteMapping**

   接收 delete 方式的请求，可以使用 GetMapping 代替

   

4. @**PutMapping**

   接收 put 方式的请求，可以用 PostMapping 代替

   

5. @**GetMapping**

   接收 get 方式的请求



### 3.4.3 案例：使用 RESTful 风格模拟实现对学生的增删改查操作

项目名称：014-springboot-restful 

该项目集成了 MyBatis、spring、SpringMVC，通过模拟实现对学生的增删改查操作

1. pom.xml 文件添加内容如下

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
       <modelVersion>4.0.0</modelVersion>
       <parent>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-parent</artifactId>
           <version>2.5.8</version>
           <relativePath/> <!-- lookup parent from repository -->
       </parent>
       <groupId>com.example</groupId>
       <artifactId>springboot-restful</artifactId>
       <version>0.0.1-SNAPSHOT</version>
       <name>014-springboot-restful</name>
       <description>Demo project for Spring Boot</description>
       <properties>
           <java.version>1.8</java.version>
       </properties>
       <dependencies>
   
           <!--web场景依赖-->
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-web</artifactId>
           </dependency>
   
           <!--mysql驱动-->
           <dependency>
               <groupId>mysql</groupId>
               <artifactId>mysql-connector-java</artifactId>
               <scope>runtime</scope>
           </dependency>
   
           <!--mybatis 依赖-->
           <dependency>
               <groupId>com.github.kaixinzyw</groupId>
               <artifactId>mybatis-spring-boot-fast-mapper</artifactId>
               <version>2.0.1</version>
           </dependency>
   
           <dependency>
               <groupId>org.projectlombok</groupId>
               <artifactId>lombok</artifactId>
               <optional>true</optional>
           </dependency>
   
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-test</artifactId>
               <scope>test</scope>
           </dependency>
   
   
       </dependencies>
   
       <build>
   
           <resources>
   
               <!--将Java代码下的xml编译到class下面去-->
               <resource>
                   <directory>src/main/java</directory>
                   <includes>
                       <include>**/*.xml</include>
                   </includes>
               </resource>
   
               <resource>
                   <directory>src/main/resources</directory>
                   <includes>
                       <include>**/*.*</include>
                   </includes>
               </resource>
   
               <resource>
                   <directory>src/main/webapp</directory>
                   <targetPath>META-INF/resources</targetPath>
                   <includes>
                       <include>**/ *.*</include>
                   </includes>
               </resource>
   
           </resources>
   
   
           <plugins>
   
               <!--mybatis 代码自动生成插件-->
               <plugin>
                   <groupId>org.mybatis.generator</groupId>
                   <artifactId>mybatis-generator-maven-plugin</artifactId>
                   <version>1.3.6</version>
                   <configuration>
                       <!--配置文件的位置-->
                       <configurationFile>StudentMapper.xml</configurationFile>
                       <verbose>true</verbose>
                       <overwrite>true</overwrite>
                   </configuration>
               </plugin>
               
               <plugin>
                   <groupId>org.springframework.boot</groupId>
                   <artifactId>spring-boot-maven-plugin</artifactId>
                   <version>2.5.8</version>
                   <configuration>
                       <excludes>
                           <exclude>
                               <groupId>org.projectlombok</groupId>
                               <artifactId>lombok</artifactId>
                           </exclude>
                       </excludes>
                   </configuration>
               </plugin>
   
   
           </plugins>
       </build>
   
   </project>
   
   ```

2. application.yml 核心配置文件

   ```yaml
   spring:
     datasource:
       driver-class-name: com.mysql.cj.jdbc.Driver
       url: jdbc:mysql://localhost:3306/springboot?useUnicode=true&characterEncoding=utf-8&useSSL=false&serverTimezone=GMT
       username: root
       password: 123456
   ```

3. 通过逆向工程生成 DAO

   ![image-20220116222442503](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220116222442503.png)

   - mapper

     ```java
     package com.example.springbootrestful.mapper;
     
     import com.example.springbootrestful.pojo.Student;
     import org.apache.ibatis.annotations.Mapper;
     
     import java.awt.*;
     import java.util.List;
     
     @Mapper
     public interface StudentMapper {
         //根据ID查询学生
         Student getStudentById(int id);
     
         // 查看全部学生
         List<Student> getStudents();
     
         // 修改学生的信息
         int upStudent(Student student);
     
         // 添加一个学生
         int addStudent(Student student);
     
         // 通过id删除学生
         int deleteById(Integer id);
     
     
     }
     ```

   - mapper.xml

     ```xml
     <?xml version="1.0" encoding="UTF-8" ?>
     <!DOCTYPE mapper
             PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
             "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
     <mapper namespace="com.example.springbootrestful.mapper.StudentMapper">
     
         <!--查看某一个学生的信息-->
         <select id="getStudentById"  resultType="com.example.springbootrestful.pojo.Student">
             select *
             from springboot.t_student
             where id=#{id};
         </select>
     
         <!--查看全班的信息-->
         <select id="getStudents"  resultType="com.example.springbootrestful.pojo.Student">
             select *
             from springboot.t_student
         </select>
         
         
         <!--修改某个学生的信息-->
         <update id="upStudent">
             update springboot.t_student
             set  name=#{name},age=#{age}
             where id=#{id};
     
         </update>
     
     
         <!--添加一个学生
           因为id是自增的, 所以这里不用添加id
         -->
         <insert id="addStudent">
             insert into springboot.t_student (name,age)
             values (#{name},#{age});
         </insert>
     
     
         <!--通过id删除学生-->
         <delete id="deleteById" >
             delete
             from springboot.t_student
             where id=#{id};
         </delete>
     
     
     </mapper>
     ```

4.  创建service层

    ![image-20220116222700105](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220116222700105.png)

    - 接口

      ```java
      package com.example.springbootrestful.service;
      
      import com.example.springbootrestful.pojo.Student;
      import org.springframework.stereotype.Service;
      
      import java.util.List;
      
      
      public interface StudentService {
      
          //根据ID查询用户
          Student getStudentById(int id);
      
          // 查看全部用户
          List<Student> getStudents();
      
          // 修改学生的信息
          int upStudent(Student student);
      
          // 添加一个学生
          int addStudent(Student student);
      
          // 通过id删除学生
          int deleteById(Integer id);
      }
      ```

    - 实现类

      ```java
      package com.example.springbootrestful.service.impl;
      
      
      import com.example.springbootrestful.mapper.StudentMapper;
      import com.example.springbootrestful.pojo.Student;
      import com.example.springbootrestful.service.StudentService;
      import org.springframework.beans.factory.annotation.Autowired;
      import org.springframework.stereotype.Service;
      
      import java.util.List;
      
      @Service
      public class StudentServiceImpl implements StudentService {
      
          @Autowired
          private StudentMapper studentMapper;
      
      
          @Override
          public Student getStudentById(int id) {
              return studentMapper.getStudentById(id);
          }
      
          @Override
          public List<Student> getStudents() {
              return studentMapper.getStudents();
          }
      
          @Override
          public int upStudent(Student student) {
              return studentMapper.upStudent(student);
          }
      
          @Override
          public int addStudent(Student student) {
              return studentMapper.addStudent(student);
          }
      
          @Override
          public int deleteById(Integer id) {
              return studentMapper.deleteById(id);
          }
      }
      ```

5.  controller层

    ```java
    package com.example.springbootrestful.controller;
    
    
    import com.example.springbootrestful.mapper.StudentMapper;
    
    import com.example.springbootrestful.pojo.Student;
    import io.swagger.models.auth.In;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.ResponseBody;
    
    @Controller
    public class RESTController {
    
        @Autowired
        private StudentMapper studentService;
    
    
        /**
         * 查看全班同学的信息
         * @return
         */
        @ResponseBody
        @GetMapping(value = "/select")
        public Object  selectStudents(){
            return studentService.getStudents();
        }
    
        /**
         * 通过id 查询某个学生的全部信息
         * @param id
         * @return
         */
        @ResponseBody
        @GetMapping(value = "/select/{id}") // select/1  这样的形式
        public Object  selectStudentById(@PathVariable("id") Integer id){
             return studentService.getStudentById(id);
        }
    
    
        @ResponseBody
        @GetMapping("/up/{id}/{name}/{age}")
        public String upStudent(@PathVariable("id") Integer id,
                                @PathVariable("name") String name,
                                @PathVariable("age") Integer age){
            Student student = new Student();
            student.setId(id);
            student.setName(name);
            student.setAge(age);
    
            int i = studentService.upStudent(student);
            if (i==1) {
                return "修改成功";
            }
            return "修改失败";
        }
    
    
        @ResponseBody
        @GetMapping("/add/{name}/{age}")
        public String addStudent(@PathVariable("name") String name,
                                @PathVariable("age") Integer age){
            Student student = new Student();
            student.setName(name);
            student.setAge(age);
    
            int i = studentService.addStudent(student);
            if (i==1) {
                return "修改成功";
            }
            return "修改失败";
        }
    
    
        @ResponseBody
        @GetMapping("/delete/{id}")
        public String deleteStudent(@PathVariable("id") Integer id){
            Student student = new Student();
            student.setId(id);
    
            int i = studentService.deleteById(id);
            if (i==1) {
                return "删除成功";
            }
            return "删除失败";
        }
    
    
    
    }
    ```



### 3.4.4 RESTful 原则 

- 增 post 请求、删 delete 请求、改 put 请求、查 get 请求

- 请求路径不要出现动词

  例如：查询订单接口 /boot/order/1021/1（推荐） 

  /boot/queryOrder/1021/1（不推荐）

- 分页、排序等操作，不需要使用斜杠传参数

  例如：订单列表接口

  /boot/orders?page=1&sort=desc

  一般传的参数不是数据库表的字段，可以不采用斜杠






## 3.5 Spring Boot 集成 Redis





## 3.6 Spring Boot 集成 Dubbo

阿 里 巴 巴 提 供 了 dubbo 集 成 springBoot 开 源 项 目 ， 可 以 到 GitHub 上 https://github.com/alibaba/dubbo-spring-boot-starter 查看入门教程









