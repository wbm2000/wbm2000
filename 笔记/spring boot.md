 

# Spring Boot

## 1. 快速上手SpringBoot 

SpringBoot入门程序开发  SpringBoot是由Pivotal团队提供的全新框架，其设计目的是用来==简化==Spring应用的==初始搭建==以及==开发过程==

### 步骤

1. 创建新模块，选择Spring Initializr，并配置模块相关基础信息

   ![image-20220302132211128](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220302132211128.png)

   

2. 选择当前模块需要使用的技术集

   ![image-20220302132325952](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220302132325952.png)

3. 开发控制器类

   ```java
   @RestController   // Controller注解和ResponseBody注解的结合体 表示这个controller类的 所有String返回值都,只会返回string类型到Model中
   public class HelloController {
       @GetMapping("/hello")
       public String hello(){
           return "Hello Word !";
       }
   }
   ```

4. 运行自动生成的Application类

   ![image-20220302133124443](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220302133124443.png)

5. 运行 

   ![image-20220302133221611](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220302133221611.png)







### 入门案例

**最简SpringBoot程序所包含的基础文件**

- pom.xml文件 

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
      <parent>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-starter-parent</artifactId>
          <version>2.6.4</version>
          <relativePath/> <!-- lookup parent from repository -->
      </parent>
      <groupId>com.wbm</groupId>
      <artifactId>springboot01</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      <name>springboot01</name>
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
  
          <!--SpringBoot启动器-->
          <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-test</artifactId>
              <scope>test</scope>
          </dependency>
          
      </dependencies>
  
      <build>
          <plugins>
              <plugin>
                  <!--SpringBoot插件-->
                  <groupId>org.springframework.boot</groupId>
                  <artifactId>spring-boot-maven-plugin</artifactId>
              </plugin>
          </plugins>
      </build>
  
  </project>
  ```

- Application类

  ```java
  @SpringBootApplication
  public class Springboot01Application {
  
      public static void main(String[] args) {
          SpringApplication.run(Springboot01Application.class, args);
      }
  
  }
  ```



**Spring程序与SpringBoot程序对比**

![image-20220302134157575](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220302134157575.png)





**注意: 基于idea开发SpringBoot程序需要确保联网且能够加载到程序框架结构**





**小结:**

1. 开发SpringBoot程序可以根据向导进行联网快速制作 

2. SpringBoot程序需要基于JDK8进行制作 

3. SpringBoot程序中需要使用何种功能通过勾选选择技术 

4. 运行SpringBoot程序通过运行Application程序入口进行



### 隐藏指定文件/文件夹

![image-20220302140628549](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220302140628549.png)

![image-20220302141040667](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220302141040667.png)























