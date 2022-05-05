# springboot

## 1. SpringBoot 介绍

SpringBoot 帮助您创建可以独立运行的、基于 Spring 的生产级应用程序。我们对 Spring 平台和第三方库有自己的看法，所以您可以从最简单的开始。大多数SpringBoot 应用程序只需要很少的 Spring 配置。

您可以使用 SpringBoot 创建 Java 应用程序，通过使用 Java -jar 或更传统的 war 包进行部署启动。我们还提供了一个运行 spring 脚本的命令行工具。

我们的主要目标是:

- 为所有 Spring 开发提供一个非常快速和广泛可访问的入门体验。
- 要有自己独特的见解，但当需求开始偏离默认值时，要迅速离开。
- 提供大类别项目(如嵌入式服务器、安全性、度量、运行状况检查和外部化配置)中常见的一系列非功能特性。
- 不要代码生成，也不需要 XML 配置。

## 2. 系统要求

SpringBoot2.5.3 需要 Java 8，兼容并包括 Java 16。SpringFramework5.3.9 或更高版本也是必需的。

构建工具的版本要求:

| 构建工具 | 版本                  |
| -------- | --------------------- |
| Maven    | 3.5+                  |
| Gradle   | 6.8.x, 6.9.x, and 7.x |

### Servlet 容器

SpringBoot 支持以下嵌入式 servlet 容器:

| 名称         | servlet 版本 |
| ------------ | ------------ |
| Tomcat 9.0   | 4.0          |
| Jetty 9.4    | 3.1          |
| Jetty 10.0   | 4.0          |
| Undertow 2.0 | 4.0          |

您还可以将 Spring Boot 应用程序部署到任何 Servlet 3.1+ 兼容的容器中。

## 3. 安装 SpringBoot

Spring Boot 可以与 Java 开发工具一起使用，也可以作为命令行工具安装。无论哪种方式，您都需要 Java SDK v1.8 或更高版本。在开始之前，您应该使用以下命令检查当前的 Java 安装:

```
$ java -version
```

### 3.1 Java 开发人员的安装说明

您可以以与任何标准 Java 库相同的方式使用 Spring Boot。为此，在类路径中包含适当的 spring-boot-*.jar 文件。Spring Boot 不需要任何特殊的工具集成，所以您可以使用任何 IDE 或文本编辑器。另外，Spring Boot 应用程序没有什么特殊之处，因此您可以像运行其他 Java 程序一样运行和调试 Spring Boot 应用程序。

尽管您可以复制 Spring Boot jar，但我们通常建议您使用支持依赖项管理的构建工具(如Maven或Gradle)。

#### 3.1.1 Maven 安装

Spring Boot 与 Apache Maven 3.3 或更高版本兼容。如果您还没有安装 Maven，可以按照 [Maven .apache.org](Maven .apache.org) 上的说明操作。

在许多操作系统上，Maven 可以与包管理器一起安装。如果你使用 OSX Homebrew，尝试 brew install maven。Ubuntu 用户可以运行 sudo apt-get install maven。使用 Chocolatey 的 Windows 用户可以在一个提升的(管理员)提示符下运行 choco install maven。

译者注：现在使用 IDEA，可以很方便地创建 SpringBoot 项目，不用这么复杂。

Spring Boot 依赖使用 org.springframework.boot groupId。通常，Maven POM 文件继承 spring-boot-starter-parent 项目，并向一个或多个 “starter”声明依赖项。Spring Boot 还提供了一个可选的 Maven 插件来创建可执行的 jar。

#### 3.1.2 Gradle 安装

Spring Boot 与 Gradle 6.8、6.9和7.x兼容。如果你还没有安装 Gradle，你可以按照[gradle.org](https://www.cnblogs.com/youcoding/p/gradle.org)上的说明操作。

Spring Boot 依赖项可以通过使用 org.springframework.boot 组声明。通常，您的项目会向一个或多个 “starter” 声明依赖项。Spring Boot 提供了一个有用的 Gradle 插件，可以用来简化依赖声明和创建可执行 jar。

### 3.2 Spring Boot CLI 安装

这个用处不大， 暂不翻译。

具体参考官网：https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started.html#getting-started

## 4. 开发你的第一个 SpringBoot 程序

[spring.io](https://www.cnblogs.com/youcoding/p/spring.io) 网站包含许多使用 Spring Boot 的入门指南。如果你需要解决一个特定的问题，首先检查那里。

您可以通过 [start.spring.io](https://www.cnblogs.com/youcoding/p/start.spring.io)并从依赖项搜索器中选择“Web”启动器来快捷执行以下步骤。这样做将生成一个新的项目结构，以便您可以立即开始编码。更多细节请查看[start.spring.io](https://www.cnblogs.com/youcoding/p/start.spring.io)用户指南。

在我们开始之前，打开终端并运行以下命令，以确保您安装了有效的 Java 和 Maven 版本:

```
$ java -version     命令行
java version "1.8.0_102"
Java(TM) SE Runtime Environment (build 1.8.0_102-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.102-b14, mixed mode)
$ mvn -v   命令行
Apache Maven 3.5.4 (1edded0938998edf8bf061f1ceb3cfdeccf443fe; 2018-06-17T14:33:14-04:00)
Maven home: /usr/local/Cellar/maven/3.3.9/libexec
Java version: 1.8.0_102, vendor: Oracle Corporation
```

### 4.1 使用idea创建springBoot项目

第一步打开idea,点Spring Initializr 创建springBoot项目, 输入想要的名称和对应的jdk版本号, 最后点下一步

![image-20211210132607469](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210132607469.png)



选择springboot版本, 点完成,,然后等几分钟, 他会加载依赖

![image-20211210133012862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210133012862.png)



因为我们现在想要学的版本是2.5.3 那么我们就要修改自己需要的版本

![image-20211210133532353](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210133532353.png)









## Web开发

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210140646859.png" alt="image-20211210140646859" style="zoom:50%;" />







## 1、SpringMVC自动配置概览

Spring Boot provides auto-configuration for Spring MVC that **works well with most applications.(大多场景我们都无需自定义配置)**

The auto-configuration adds the following features on top of Spring’s defaults:

- Inclusion of `ContentNegotiatingViewResolver` and `BeanNameViewResolver` beans.

- - 内容协商视图解析器和BeanName视图解析器

- Support for serving static resources, including support for WebJars (covered [later in this document](https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-spring-mvc-static-content))).

- - 静态资源（包括webjars）

- Automatic registration of `Converter`, `GenericConverter`, and `Formatter` beans.

- - 自动注册 `Converter，GenericConverter，Formatter `

- Support for `HttpMessageConverters` (covered [later in this document](https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-spring-mvc-message-converters)).

- - 支持 `HttpMessageConverters` （后来我们配合内容协商理解原理）

- Automatic registration of `MessageCodesResolver` (covered [later in this document](https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-spring-message-codes)).

- - 自动注册 `MessageCodesResolver` （国际化用）

- Static `index.html` support.

- - 静态index.html 页支持

- Custom `Favicon` support (covered [later in this document](https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-spring-mvc-favicon)).

- - 自定义 `Favicon`  浏览器的小图标

- Automatic use of a `ConfigurableWebBindingInitializer` bean (covered [later in this document](https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-spring-mvc-web-binding-initializer)).

- - 自动使用 `ConfigurableWebBindingInitializer` ，（DataBinder负责将请求数据绑定到JavaBean上）

If you want to keep those Spring Boot MVC customizations and make more [MVC customizations](https://docs.spring.io/spring/docs/5.2.9.RELEASE/spring-framework-reference/web.html#mvc) (interceptors, formatters, view controllers, and other features), you can add your own `@Configuration` class of type `WebMvcConfigurer` but **without** `@EnableWebMvc`.

**不用@EnableWebMvc注解。使用** `**@Configuration**` **+** `**WebMvcConfigurer**` **自定义规则**



If you want to provide custom instances of `RequestMappingHandlerMapping`, `RequestMappingHandlerAdapter`, or `ExceptionHandlerExceptionResolver`, and still keep the Spring Boot MVC customizations, you can declare a bean of type `WebMvcRegistrations` and use it to provide custom instances of those components.

**声明** `**WebMvcRegistrations**` **改变默认底层组件**



If you want to take complete control of Spring MVC, you can add your own `@Configuration` annotated with `@EnableWebMvc`, or alternatively add your own `@Configuration`-annotated `DelegatingWebMvcConfiguration` as described in the Javadoc of `@EnableWebMvc`.

**使用** `**@EnableWebMvc+@Configuration+DelegatingWebMvcConfiguration 全面接管SpringMVC**`



## 2、简单功能分析

#### 2.1、静态资源访问

##### 1、静态资源目录

只要静态资源放在类路径下： resources路径下的 static 或 public 或 resources 或 META-INF\resources 下

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210141958721.png" alt="image-20211210141958721" style="zoom:50%;" />

测试 :    分别在这4个路径下方了4个图片

![image-20211210142242864](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210142242864.png)



访问 ： 当前项目根路径/ + 静态资源名 (localhost:8080/静态资源名.后缀)

localhost:8080/1.png

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210142457713.png" alt="image-20211210142457713" style="zoom:33%;" />

localhost:8080/2.png

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210142524695.png" alt="image-20211210142524695" style="zoom:33%;" />

localhost:8080/3.png

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210142601692.png" alt="image-20211210142601692" style="zoom:33%;" />

localhost:8080/4.png

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210142706255.png" alt="image-20211210142706255" style="zoom:33%;" />

可以看到都访问成功了



- 底层原理:

探究原理之前先测试一下,如果一个controller为4.png, 而静态资源也有一个叫4.png的,那么他会走哪一个(注: 上面已经创建了一个4.png的静态文件)

```java
@RestController // 表示被springBoot接管 并且返回的的值不以跳转文件执行
public class HelloController {
    @RequestMapping("/4.png") 
    public String hello(){
        return "hello";
    }
}
```



下图可以看到他先走的是controller中的 4.png

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210143942761.png" alt="image-20211210143942761" style="zoom: 50%;" />





原理： 静态映射/**。 可以拦截所有请求

请求进来，先去找Controller看能不能处理。不能处理的所有请求又都交给静态资源处理器。

静态资源也找不到,则响应404页面

比如并没有localhost:8080/5.png这个链接,也没有对应的静态资源文件,那么返回的就是404

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210144336930.png" alt="image-20211210144336930" style="zoom:50%;" />









##### 2、静态资源访问前缀

默认无前缀

- 改变默认的静态资源路径

```yaml
spring:   # 原来的是/**      访问静态资源:localhost:8080/静态资源名.后缀
  mvc:
    static-path-pattern: /**

# 修改为 /res/**       访问静态资源:localhost:8080/res/静态资源名.后缀
spring:
  mvc:
    static-path-pattern: /res/**
```

测试:http://localhost:8080/res/1.png

![image-20211210145238862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210145238862.png)



静态资源默认是在,resources路径下的 static 或 public 或 resources 或 META-INF\resources 下,这4个路径下的

我们可以改变默认的静态资源路径, 但是如果我们修改了默认的静态资源路径, 他的默认4个路径就没有用了, 有效的只有自己设置的静态资源路径.



- 底层:

点开 static-locations, 可以看到,跳到了ResourceProperties 的setStaticLocations方法

```java
public void setStaticLocations(String[] staticLocations) {
   this.staticLocations = appendSlashIfNecessary(staticLocations);
}
```



在点开this.staticLocations的  staticLocations  跳到  staticLocations属性

```
private String[] staticLocations = CLASSPATH_RESOURCE_LOCATIONS;
```



点开 CLASSPATH_RESOURCE_LOCATIONS 常量

这就是静态资源的底层  这4个静态资源路径

```java
private static final String[] CLASSPATH_RESOURCE_LOCATIONS = { "classpath:/META-INF/resources/",
      "classpath:/resources/", "classpath:/static/", "classpath:/public/" };
```





- 改变静态路径

自己设置的路径,我们可以像底层一样设置 一个数组, 设置多个静态路径, 也可以设置一个

```yaml
resources:
    static-locations: classpath:/hh/

resources:
    static-locations: [classpath:/hh/]
```



测试:

![image-20211210153354938](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210153354938.png)

http://localhost:8080/res/5.png

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210153416555.png" alt="image-20211210153416555" style="zoom:67%;" />





##### 3、webjar

自动映射 /[webjars](http://localhost:8080/webjars/jquery/3.5.1/jquery.js)/**

https://www.webjars.org/        webjar官网

随便找个jar包测试

```xml
        <dependency>
            <groupId>org.webjars</groupId>
            <artifactId>jquery</artifactId>
            <version>3.5.1</version>
        </dependency>
```

访问地址：http://localhost:8080/webjars/jquery/3.5.1/jquery.js 后面地址要按照依赖里面的包路径

测试: 

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210155000558.png" alt="image-20211210155000558" style="zoom:50%;" />









<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210160448547.png" alt="image-20211210160448547" style="zoom:70%;" />





#### 2.2、欢迎页支持

- 静态资源路径下  index.html

- - 可以配置静态资源路径
  - 但是不可以配置静态资源的访问前缀。否则导致 index.html不能被默认访问

```yaml
spring:
#  mvc:
#    static-path-pattern: /res/**   这个会导致welcome page功能失效  在新版本中被修复了

  resources:
    static-locations: [classpath:/haha/]
```

- controller能处理/index   如果controller中有 index.html, 那么springBoot会优先controller的

  

测试:

在静态文件中添加一个 index.html 

![image-20211210213705813](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210213705813.png)



在controller中添加一个, index.html的controller

```java
@RequestMapping("/index.html")
public String index(){
    return "主页2";
}
```



可以看到是优先于controller的

![image-20211210214021111](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210214021111.png)



#### 2.3、自定义 `Favicon`

favicon.ico 放在静态资源目录下即可。

```ymal
spring:
#  mvc:
#    static-path-pattern: /res/**   依旧会冲突, 在新版本中修复了
```

![image-20211210214905962](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211210214905962.png)



友情提示如果没有显示出来先关闭浏览器, 在重新打开, 因为有缓存





#### 2.4、静态资源配置原理

- SpringBoot启动默认加载  非常多的xxxAutoConfiguration 类（自动配置类）
- SpringMVC功能的自动配置类 WebMvcAutoConfiguration
- 判断这个类是否生效

```java
@Configuration(proxyBeanMethods = false)  
@ConditionalOnWebApplication(type = Type.SERVLET) // 表示这个类必须是servlet, 这个类下面的方法才生效   
@ConditionalOnClass({ Servlet.class, DispatcherServlet.class, WebMvcConfigurer.class }) // 需要有这三个类, 才生效
@ConditionalOnMissingBean(WebMvcConfigurationSupport.class) // 容器中没有这个组件的时候, 才生效
@AutoConfigureOrder(Ordered.HIGHEST_PRECEDENCE + 10)
@AutoConfigureAfter({ DispatcherServletAutoConfiguration.class, TaskExecutionAutoConfiguration.class,
		ValidationAutoConfiguration.class })
public class WebMvcAutoConfiguration {}
```

- 给容器中配了什么。

```java
	@Configuration(proxyBeanMethods = false)
	@Import(EnableWebMvcConfiguration.class) 
	@EnableConfigurationProperties({ WebMvcProperties.class, ResourceProperties.class })
	@Order(0)
	public static class WebMvcAutoConfigurationAdapter implements WebMvcConfigurer {}
```

- 配置文件的相关属性和xxx进行了绑定。WebMvcProperties==**spring.mvc**、ResourceProperties==**spring.resources**



##### 1、配置类只有一个有参构造器

```java
	//有参构造器所有参数的值都会从容器中确定
//ResourceProperties resourceProperties: 获取和spring.resources绑定的所有的值的对象
//WebMvcProperties mvcProperties:   获取和spring.mvc绑定的所有的值的对象
//ListableBeanFactory beanFactory:  获取Spring的beanFactory(bean工厂)
//HttpMessageConverters: 找到所有的HttpMessageConverters
//ResourceHandlerRegistrationCustomizer: 找到 资源处理器的自定义器。=========
//DispatcherServletPath:  DispatcherServlet路径  
//ServletRegistrationBean:   给应用注册Servlet、Filter....
	public WebMvcAutoConfigurationAdapter
       (ResourceProperties resourceProperties, 
        WebMvcProperties mvcProperties,
	    ListableBeanFactory beanFactory,
        ObjectProvider<HttpMessageConverters> messageConvertersProvider,
		ObjectProvider<ResourceHandlerRegistrationCustomizer> resourceHandlerRegistrationCustomizerProvider,
	    ObjectProvider<DispatcherServletPath> dispatcherServletPath,
		ObjectProvider<ServletRegistrationBean<?>> servletRegistrations){
        
		this.resourceProperties = resourceProperties;
		this.mvcProperties = mvcProperties;
		this.beanFactory = beanFactory;
		this.messageConvertersProvider = messageConvertersProvider;
this.resourceHandlerRegistrationCustomizerresourceHandlerRegistrationCustomizerProvider.getIfAvailable();
		this.dispatcherServletPath = dispatcherServletPath;
		this.servletRegistrations = servletRegistrations;
        
		}
```





##### 2、资源处理的默认规则

```java
@Override
public void addResourceHandlers(ResourceHandlerRegistry registry) {
        // 这里的!this.resourceProperties.isAddMappings() 看源码可以看到 private boolean addMappings = true;
       // 也就是说添加判断 为 !true  解释为不是true, 如果不是true就 禁用所有静态资源规则
		if (!this.resourceProperties.isAddMappings()) { 
			logger.debug("Default resource handling disabled");
			return;
		}
         
        // 缓存策略   cache: 
                       //period: 11000  #  配置缓存的时间  SECONDS(秒)单位
	    Duration cachePeriod = this.resourceProperties.getCache().getPeriod();
		CacheControl cacheControl=this.resourceProperties.getCache().getCachecontrol().toHttpCacheControl();
			//webjars的规则
            /** /webjars/** 表示带有/webjars 的请求都会被他拦截, 也会去找所有webjars下的静态资源
                比如上面的http://localhost:8080/webjars/jquery/3.5.1/jquery.js  这个链接 就会被他拦截
            */
            if (!registry.hasMappingForPattern("/webjars/**")) {// 如果是 ! false 就执行
				customizeResourceHandlerRegistration(registry.addResourceHandler("/webjars/**")
                    /** 这里的classpath:/META-INF/resources/webjars/ 就是我们省略的
                        因为他会自动在  /META-INF/resources/webjars/下寻找 静态资源
                        
                        正常链接应该是这样的 
                        localhost:8080/webjars/META-INF/resources/webjars/jquery/3.5.1/jquery.js
                    */
						.addResourceLocations("classpath:/META-INF/resources/webjars/")
                         // cachePeriod 设置的缓存策略 
						.setCachePeriod(getSeconds(cachePeriod)).setCacheControl(cacheControl));
			}
            
        // 静态资源的规则 
        //staticPathPattern 的值默认是 /**    这个可以通过配置修改
        
		String staticPathPattern = this.mvcProperties.getStaticPathPattern();
         
         // 默认条件下  registry.hasMappingForPattern(staticPathPattern) = false
         // !false = true 表示这里会执行
		if (!registry.hasMappingForPattern(staticPathPattern)) {
            // staticPathPattern 表示 /**  表示/** 的链接会被他拦截
			customizeResourceHandlerRegistration(registry.addResourceHandler(staticPathPattern)
            /**如果是/** 的链接他会从这几个静态资源找 , 这里可以通过配置修改 
        getResourceLocations(this.resourceProperties.getStaticLocations())=  
       { "classpath:/META-    INF/resources/", "classpath:/resources/", "classpath:/static/", "classpath:/public/" }; 这默认的4个静态路径找
            */
			.addResourceLocations(getResourceLocations(this.resourceProperties.getStaticLocations()))
            // 缓存策略
			.setCachePeriod(getSeconds(cachePeriod)).setCacheControl(cacheControl));
			}
		}

```



```yml
spring:
#  mvc:
#    static-path-pattern: /res/**

  resources:
    add-mappings: false   禁用所有静态资源规则
```



##### 3、欢迎页的处理规则

```java
        	HandlerMapping：处理器映射。保存了每一个Handler能处理哪些请求。
        @Bean
		public WelcomePageHandlerMapping welcomePageHandlerMapping(ApplicationContext applicationContext,
		FormattingConversionService mvcConversionService, ResourceUrlProvider mvcResourceUrlProvider) {
            
			WelcomePageHandlerMapping welcomePageHandlerMapping = new WelcomePageHandlerMapping(
				new TemplateAvailabilityProviders(applicationContext),
                applicationContext, getWelcomePage(),
			    this.mvcProperties.getStaticPathPattern());
            
			welcomePageHandlerMapping.setInterceptors(getInterceptors(mvcConversionService,
                mvcResourceUrlProvider));
            
			welcomePageHandlerMapping.setCorsConfigurations(getCorsConfigurations());
			return welcomePageHandlerMapping;
		}

    
   /**点开上面的 WelcomePageHandlerMapping 会跳到 WelcomePageHandlerMapping类 的WelcomePageHandlerMapping的
      有参构造器
   */
   WelcomePageHandlerMapping(TemplateAvailabilityProviders templateAvailabilityProviders,
		ApplicationContext applicationContext, Optional<Resource> welcomePage, String staticPathPattern) {
       
       /**
          welcomePage.isPresent()= true  如果也是true的话 才能使用欢迎页
           也就是说 staticPathPattern必须是/** 
           这也就说明了为什么设置
           spring:
              mvc:
                 static-path-pattern: /res/**   会导致欢迎页功能失效的原因
                 如果设置了/res/** , 那么这个if条件就不会执行了
       */
		if (welcomePage.isPresent() && "/**".equals(staticPathPattern)) {
			logger.info("Adding welcome page: " + welcomePage.get());
			setRootViewName("forward:index.html");
		}
		else if (welcomeTemplateExists(templateAvailabilityProviders, applicationContext)) {
			logger.info("Adding welcome page template: index");
			setRootViewName("index");
		}
	}


	
```

##### 4、favicon



## 3、请求参数处理

### 0、请求映射

#### 1、rest使用与原理

- @xxxMapping；
- Rest风格支持（*使用**HTTP**请求方式动词来表示对资源的操作*）

- - *以前：**/getUser*  *获取用户*    */deleteUser* *删除用户*   */editUser*  *修改用户*      */saveUser* *保存用户*

  - *现在： /user*    *GET请求获取用户*    *DELETE请求删除用户*     *PUT请求修改用户*      *POST请求保存用户*

    

##### 测试使用的html表单

**在html表单中, method的值只能设置get和post请求, 不能使用 DELETE  PUT**

```html
测试REST风格；
<form action="/user" method="get">
    <input value="REST-GET 提交" type="submit"/>
</form>

<form action="/user" method="post">
    <input value="REST-POST 提交" type="submit"/>
</form>

<form action="/user" method="DELETE">
    <input value="REST-DELETE 提交" type="submit"/>
</form>

<form action="/user" method="PUT">
    <input value="REST-PUT 提交" type="submit"/>
</form>
```



##### **测试PUT, DELETE  是否有用**

**测试需要的controller**

```java
//    @RequestMapping(value = "/user",method = RequestMethod.GET)
    @GetMapping("/user")
    public String getUser(){
        return "GET-张三";
    }

//    @RequestMapping(value = "/user",method = RequestMethod.POST)
    @PostMapping("/user")
    public String saveUser(){
        return "POST-张三";
    }


//    @RequestMapping(value = "/user",method = RequestMethod.PUT)
    @PutMapping("/user")
    public String putUser(){
        return "PUT-张三";
    }

//    @RequestMapping(value = "/user",method = RequestMethod.DELETE)
    @DeleteMapping("/user")
    public String deleteUser(){
        return "DELETE-张三";
    }
```





**点开delete 提交 返回的是 get请求的 controller, 可以得出 在html表单中, method的值只能设置get和post请求, 不能使用 DELETE  PUT, 如果写了其他的值, 那么他会默认走get请求**

![image-20211211131027082](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211211131027082.png)



![image-20211211131114612](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211211131114612.png)



**想要表单提交delete, 或者put请求就得, 在表单中 设置一个name为 _method的隐藏域, 因为他默认是关闭的, 需要手动开启,我们需要在配置文件中把他设置为 true**

```yml
mvc:
  hiddenmethod:
    filter:
      enabled: true
```



**然后再delete和put 设置一个隐藏域, name这里必须是_method, value是对应的请求名字**

```html
<form action="/user" method="post">
    <input name="_method" type="hidden" value="DELETE">
    <input value="REST-DELETE 提交" type="submit"/>
</form>
<form action="/user" method="post">
    <input name="_method" type="hidden" value="PUT">
    <input value="REST-PUT 提交" type="submit"/>
</form>
```

**源码:**

```java
 // 这个方法是WebMvcAutoConfiguration 第一个方法
    @Bean
	@ConditionalOnMissingBean(HiddenHttpMethodFilter.class)// 如果没有这个类
/** @ConditionalOnProperty(prefix = "spring.mvc.hiddenmethod.filter", name = "enabled" 
     这个注解表示 , 如果这个配置spring.mvc.hiddenmethod.filter.enabled 为true, 这个方法就启动
     matchIfMissing表示默认, false,也就是说默认是关闭的
*/
	@ConditionalOnProperty(prefix = "spring.mvc.hiddenmethod.filter", name = "enabled", matchIfMissing = false)
	public OrderedHiddenHttpMethodFilter hiddenHttpMethodFilter() {
		return new OrderedHiddenHttpMethodFilter();
	}
```



**测试:**

![image-20211211133527355](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211211133527355.png)



Rest原理（表单提交要使用REST的时候）

- 表单提交会带上**_method=PUT**
- **请求过来被**HiddenHttpMethodFilter拦截

- - 请求是否正常，并且是POST

- - - 获取到**_method**的值。
    - 兼容以下请求；**PUT**.**DELETE**.**PATCH**

- - - **原生request（post），包装模式requesWrapper重写了getMethod方法，返回的是传入的值。**
    - **过滤器链放行的时候用wrapper。以后的方法调用getMethod是调用****requesWrapper的。**

```java
public OrderedHiddenHttpMethodFilter hiddenHttpMethodFilter() {
   return new OrderedHiddenHttpMethodFilter();
}
点开 OrderedHiddenHttpMethodFilter, 可以看到这个类继承了HiddenHttpMethodFilter 类
    点开HiddenHttpMethodFilter类 会看到doFilterInternal 方法
    
    
@Override
	protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response, 
                                    FilterChain filterChain)
                                    throws ServletException, IOException {
    
		             HttpServletRequest requestToUse = request;// 这里会拿到我们原生的请求
           /**
            request.getMethod() 获取 表单中的method是什么请求
            判断原生的请求是不是post, 如果是= post 还有另外一个条件判断这个请求是否有错,如果没有错 那么这个if就会执行
            
            */
if ("POST".equals(request.getMethod()) && request.getAttribute(WebUtils.ERROR_EXCEPTION_ATTRIBUTE) == null){
             //request.getParameter(this.methodParam); 获取到_method的值
            // 这时候如果_method的value= delete的话, 那么paramValue这个属性就= delete
			String paramValue = request.getParameter(this.methodParam);
             // StringUtils.hasLength(paramValue) 是否为空
			if (StringUtils.hasLength(paramValue)) {
                // paramValue.toUpperCase(Locale.ENGLISH); 把字母大小写, 转换为大写, 也就是说如果paramValue=delete
                // 他会转换为大写, DELETE
				String method = paramValue.toUpperCase(Locale.ENGLISH);
                // 这里是判断是否为 delete put post这三个的其中一个, 如果是就执行这个if
				if (ALLOWED_METHODS.contains(method)) {
                    // 这里就是把post请求转换为delete的 
					requestToUse = new HttpMethodRequestWrapper(request, method);
				}
			}
		}

		filterChain.doFilter(requestToUse, response);
	}
    
```



**Rest使用客户端工具，**

- 如PostMan直接发送Put、delete等方式请求，无需Filter。



**扩展：如何把_method 这个名字换成我们自己喜欢的。**

![image-20211211145708507](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211211145708507.png)



创建一个config包创建一个配置类

```java

@Configuration(proxyBeanMethods = false)
public class WebConfig {
//自定义filter
    @Bean
    public HiddenHttpMethodFilter hiddenHttpMethodFilter(){
        HiddenHttpMethodFilter methodFilter = new HiddenHttpMethodFilter(); // 创建一个HiddenHttpMethodFilter
        methodFilter.setMethodParam("_m"); // 然后设置表单中的隐藏域 name 的值
        // 表单 <input name="_method" type="hidden" value="DELETE"> 
        // 这个时候就要把 name 的值改为 _m
        return methodFilter;
    }
    
}
```





#### 2、请求映射原理

![image-20211211221155843](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211211221155843.png)

  SpringMVC功能分析都从 org.springframework.web.servlet.DispatcherServlet类的doDispatch（）方法



 doDispatch方法源码

```java
protected void doDispatch(HttpServletRequest request, HttpServletResponse response) throws Exception {
		HttpServletRequest processedRequest = request;
		HandlerExecutionChain mappedHandler = null;
		boolean multipartRequestParsed = false;

		WebAsyncManager asyncManager = WebAsyncUtils.getAsyncManager(request);

		try {
			ModelAndView mv = null;
			Exception dispatchException = null;

			try {
				processedRequest = checkMultipart(request);
				multipartRequestParsed = (processedRequest != request);

				// 找到当前请求使用哪个Handler(controller的方法)处理请求
				mappedHandler = getHandler(processedRequest);
				if (mappedHandler == null) {
					noHandlerFound(processedRequest, response);
					return;
				}
                
                // HandlerMappings  处理器映射  作用是: /什么什么请求, 谁来处理的映射规则

```

![image-20211211223543999](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211211223543999.png)

RequestMappingHandlerMapping : 这个处理器映射保存了所有@RequestMapping和 Handler的映射规则

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211211224455534.png" alt="image-20211211224455534" style="zoom:50%;" />



- SpringBoot自动配置欢迎页的 WelcomePageHandlerMapping 。访问 /能访问到index.html；
- SpringBoot自动配置了默认 的 RequestMappingHandlerMapping

- 请求进来，挨个尝试所有的HandlerMapping看是否有请求信息。

- - 如果有就找到这个请求对应的handler
  - 如果没有就是下一个 HandlerMapping

- 我们需要一些自定义的映射处理，我们也可以自己给容器中放**HandlerMapping**。自定义 **HandlerMapping**



### 1、普通参数与基本注解

#### 1.1、注解：

```java
@PathVariable（路径变量）
@RequestHeader（获取请求头）
@RequestParam（获取请求参数）
@CookieValue（获取cookie值）
@RequestBody（获取请求体[POST]）
@RequestAttribute（获取request域属性）
@MatrixVariable（矩阵变量）
```



```java
@RestController
public class ParameterTestController {

    @GetMapping("/car/{id}/owner/{username}")

                                     // @PathVariable（路径变量） 
    public Map<String,Object> getCar(@PathVariable("id") Integer id,
                                     @PathVariable("username") String name,
                                     /**如果带有PathVariable的注解 是map类型并且键值都是String类型那么他会把所有的 带 PathVariable注解的参数放到这个map集合 */
                                     @PathVariable Map<String,String> pv,
                                     
                                     // @RequestHeader（获取请求头） 
                                     @RequestHeader("User-Agent") String userAgent,
                                     // 跟上面的map 一样的效果
                                     @RequestHeader Map<String,String> header,
                                     // @RequestParam（获取请求参数） 
                                     @RequestParam("age") Integer age,
                                     @RequestParam("inters") List<String> inters,
                                     // 一样的
                                     @RequestParam Map<String,String> param,
                                     // @CookieValue（获取cookie值）
                                     @CookieValue("_ga") String _ga){
        Map<String,Object> map= new HashMap<>();
//        map.put("id",id);
//        map.put("name",name);
//        map.put("pv",pv);
//        map.put("userAgent",userAgent);
//        map.put("header",header);
        map.put("age",age);
        map.put("inters",inters);
        map.put("param",param);
        map.put("_ga",_ga);

    return map;
    }

    // @RequestBody（获取请求体[POST]）
    @PostMapping("/save")
    public Map postMethod(@RequestBody String content){
        Map<String,Object> map = new HashMap<>();
        map.put("content",content);
        return map;
    }



}
```



```java
@Controller
public class RequestController {

    @GetMapping("/goto")
    public String goToPage(HttpServletRequest request){
        request.setAttribute("msg","成功了");
        request.setAttribute("code",200);
        // 因为暂时没有模板引擎, 所以下面写一个
        return "forward:success"; // 转发到 /success请求
    }

    @ResponseBody
    @GetMapping("/success")  // @RequestAttribute（获取request域属性） 
    public Map success(@RequestAttribute("msg") String msg,/**第一种方法*/
                       @RequestAttribute("code") Integer code,
                       /**第二种方法*/
                       HttpServletRequest request){
        Object code1 = request.getAttribute("code");
        Object msg1 = request.getAttribute("msg");

        Map<String , Object> map = new HashMap<>();
        map.put("reqMethod_msg",msg1);
        map.put("annotatio_msg",msg);
        map.put("reqMethod_code",code1);
        map.put("annotatio_code",code);
        return map;
    }


}
```



@MatrixVariable 获取请求参数的矩阵变量

1. 语法  /cars/sell;low=34;brand=byd,audi,yd    带; 的就是矩阵变量

```java
@GetMapping("/cars/sell")
public Map carsSell(@MatrixVariable("low") Integer low,
                    @MatrixVariable("brand") List<String> brand){
    Map<String, Object> map = new HashMap<>();
    map.put("low",low);
    map.put("brand",brand);
    return  map;
}
```



去浏览器测试一下

http://localhost:8080/cars/sell;low=34;brand=byd,audi,yd

如下可以看到报404了, 因为SpringBoot 默认是禁用了矩阵变量的功能

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211213133942840.png" alt="image-20211213133942840" style="zoom:50%;" />



需要手动 : 开启, 开启有两种方法

```java
@Configuration(proxyBeanMethods = false)
public class WebConfig /**implements WebMvcConfigurer */{
    /**
     *  第一种 开启矩阵变量功能的方法  继承WebMvcConfigurer 接口
     *  重写configurePathMatch 方法
     *  创建 UrlPathHelper对象
     *  并且 使用UrlPathHelper 的setRemoveSemicolonContent方法 参数为false 设置为不移除分号后面的参数
     *  在放到 PathMatchConfigurer 类的 setUrlPathHelper方法中 开启矩阵变量
    @Override
    public void configurePathMatch(PathMatchConfigurer configurer) {
        UrlPathHelper urlPathHelper = new UrlPathHelper();
        // 设置为不移除分号后面的参数 这样矩阵变量就可以生效
        urlPathHelper.setRemoveSemicolonContent(false);
        configurer.setUrlPathHelper(urlPathHelper);
    }
    */

    /**
     *  第二种开启矩阵变量的方法
     * */
    @Bean
    public WebMvcConfigurer webMvcConfigurer(){
        return new WebMvcConfigurer(){
            @Override
            public void configurePathMatch(PathMatchConfigurer configurer) {
                    UrlPathHelper urlPathHelper = new UrlPathHelper();
                    // 设置为不移除分号后面的参数 这样矩阵变量就可以生效
                    urlPathHelper.setRemoveSemicolonContent(false);
                    configurer.setUrlPathHelper(urlPathHelper);

        }
        };


    }
```



测试:

http://localhost:8080/cars/sell;low=34;brand=byd,audi,yd

![image-20211213143856137](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211213143856137.png)

如果有两个矩阵变量为age, 那么应该怎么解决一一对应呢

```java
/** boss/1;age=20/2;age=10   如果有两个矩阵变量为age, 那么应该怎么解决一一对应呢
 @MatrixVariable 注解 还有一个参数, 可以设置 这个变量是哪个路径的
*/
@GetMapping("/cars/{bossId}/{empId}")
public Map boos(@MatrixVariable(value = "age",pathVar = "bossId") Integer bossAge,
                @MatrixVariable(value = "age",pathVar = "empId") Integer empAge){
    Map<String, Object> map = new HashMap<>();
    map.put("bossAge",bossAge);
    map.put("empAge",empAge);
    return  map;
}
```



测试:
![image-20211213144058241](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211213144058241.png)





#### 1.2、Servlet API：

WebRequest、ServletRequest、MultipartRequest、 HttpSession、javax.servlet.http.PushBuilder、Principal、InputStream、Reader、HttpMethod、Locale、TimeZone、ZoneId



**ServletRequestMethodArgumentResolver  以上的部分参数**







#### 1.3、复杂参数：

**Map**、**Model（map、model里面的数据会被放在request的请求域,  往 MAp , Model放东西相当于调用了request.setAttribute）、**Errors/BindingResult、

**RedirectAttributes（ 重定向携带数据）**、**ServletResponse（response）**、SessionStatus、UriComponentsBuilder、ServletUriComponentsBuilder

```java
Map<String,Object> map,  Model model, HttpServletRequest request 都是可以给request域中放数据，
使用 request.getAttribute(); 获取
```



```java
@GetMapping("/params")  // 往 map 和 model  放东西 都是给请求域放的
public  String testParam(Map<String ,Object> map,
                         Model model,
                         HttpServletRequest request,
                         HttpServletResponse response){

    map.put("hello","world,wbm");
    model.addAttribute("world","hello, wbm");
    request.setAttribute("message","Hello,World");

    Cookie cookie = new Cookie("c1","wbm");// 创建一个cookie key是c1 , 值是wbm
    response.addCookie(cookie);// 添加一个Cookie
   //  cookie.setDomain("localhost"); // 设置 cookie为 本机作用域   其他属性默认
    return "forward:success"; // 转发到 /success请求

}



  @ResponseBody
@GetMapping("/success") //  required = false  设置参数不一定需要 带这个参数
public Map success(@RequestAttribute(value = "msg", required = false) String msg,//**第一种方法*//*
                   @RequestAttribute(value = "code", required = false) Integer code,
                   //**第二种方法*//
                   HttpServletRequest request){

    // 获取请求域的数据
      Object hello = request.getAttribute("hello");
      Object world = request.getAttribute("world");
      Object message = request.getAttribute("message");

      // 添加到map
      Map<String , Object> map = new HashMap<>();
      map.put("hello",hello);
      map.put("world",world);
      map.put("message",message);

    // 返回出去
    return map;
}
```



测试 :  下图可以看到获取到了

http://localhost:8080/params

![image-20211218153141084](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218153141084.png)









<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218215415085.png" alt="image-20211218215415085" style="zoom:50%;" />

![image-20211218215514143](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218215514143.png)

![image-20211218215609343](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218215609343.png)



进入这个方法 判断解析器是什么类型 可以看到  获取的是 MapMethodProcessor 解析器

![image-20211218222126601](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218222126601.png)

然后会跳到 解析参数的方法

![image-20211218220611076](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218220611076.png)

进入这个方法

![image-20211218222414739](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218222414739.png)



在进入

![image-20211218222544444](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218222544444.png)



点开

![image-20211218222651995](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218222651995.png)



找到getModel 这个方法

```java
public ModelMap getModel() {
   if (useDefaultModel()) {
      return this.defaultModel; 
   }
   else {
      if (this.redirectModel == null) {
         this.redirectModel = new ModelMap();
      }
      return this.redirectModel;
   }
}
```



this.defaultModel; 是 ModelAndViewContainer 这个的属性

```java
private final ModelMap defaultModel = new BindingAwareModelMap();
```



可以得出 Map的参数, 会返回 mavContainer.getModel() , 最后为 BindingAwareModelMap这个类,  这个类不仅是Model还是Map





然后返回到 判断第二个参数  , 第一个参数是Map, 第二个是 Model

![image-20211218223721692](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218223721692.png)

跟上面一样的操作



进入判断解析器的方法

![image-20211218223820001](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218223820001.png)



判断  可以看到 返回的是 ModelMethodProcessor 解析器 , Map类型的解析器是 MapMethodProcessor 解析器

![image-20211218223917480](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218223917480.png)



然后跟上面差不多

最后发现, 这两个解析器, 都是调用 mavContainer.getModel()  这个方法

![image-20211218224622112](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218224622112.png)



**Map、Model类型的参数**，会返回 mavContainer.getModel（）；---> BindingAwareModelMap 是Model 也是Map

**mavContainer**.getModel(); 获取到值的



可以看到 ages 的0(Map)和1(Model)号参数 都是BindingAwareModelMap @6955

![image-20211218225106901](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211218225106901.png)





#### 1.4、自定义对象参数：

可以自动类型转换与格式化，可以级联封装。

测试需要的类

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Person {
    
    private String userName;
    private Integer age;
    private Date birth;
    private Pet pet;
    
}
```



```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Pet {
    private String name;
    private String age;
}
```



在index页面添加

```html
测试封装POJO；
<form action="/saveuser" method="post"> 
    姓名： <input name="userName" value="zhangsan"/> <br/>  // value 表示默认值
    年龄： <input name="age" value="18"/> <br/>
    生日： <input name="birth" value="2019/12/10"/> <br/>
    宠物姓名：<input name="pet.name" value="阿猫"/><br/>
    宠物年龄：<input name="pet.age" value="5"/>
    <input type="submit" value="保存"/>
</form>
```



进入首页

![image-20211219230509271](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211219230509271.png)

点保存, 会跳到saveuser页面

![image-20211219230614388](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211219230614388.png)





**数据绑定, 页面提交的请求数据(无论是 Get, 还是Post), 都可以和对象属性进行绑定**



### 2、POJO封装过程

- **自定义参数是用 ServletModelAttributeMethodProcessor来解析的**



### 3、参数处理原理

- HandlerMapping中找到能处理请求的Handler,所谓的Handler就是我们说的能处理的那个Controller的xxx方法, springBoot把详细信息封装到了Handler中
- 为当前Handler 找一个适配器 (HandlerAdapter)  **RequestMappingHandlerAdapter**

- 适配器执行目标方法并确定方法参数的每一个值



#### 1、HandlerAdapter

![image-20211215135350787](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211215135350787.png)

0 - 支持方法上标注@RequestMapping 的适配器

1 - 支持函数式编程的适配器

上面两种是用的最多的

xxxx



#### 2、执行目标方法

```java
// Actually invoke the handler.
// 这个在 DispatcherServlet类 -- doDispatch方法中
mv = ha.handle(processedRequest, response, mappedHandler.getHandler());
```

```java
mav = invokeHandlerMethod(request, response, handlerMethod); //执行目标方法
```

```java
// ServletInvocableHandlerMethod 在这个类中   
// 在这里打断点使用dug 进入这个执行方法
Object returnValue = invokeForRequest(webRequest, mavContainer, providedArgs);// 真正执行的方法

    // 进入了这个方法
    public Object invokeForRequest(NativeWebRequest request, @Nullable ModelAndViewContainer mavContainer,
			Object... providedArgs) throws Exception {
      // 这里是确定参数值
		Object[] args = getMethodArgumentValues(request, mavContainer, providedArgs);
		if (logger.isTraceEnabled()) {
			logger.trace("Arguments: " + Arrays.toString(args));
		}
		return doInvoke(args);
	}
```

#### 3、参数解析器-HandlerMethodArgumentResolver

参数解析器有26个

确定将要执行的目标方法的每一个参数的值是什么;

SpringMVC目标方法能写多少种参数类型。取决于参数解析器

如果标注着@PathVariable 这个注解的  springboot就使用  PathVariableMethodArgumentResolver 这个解析器 也是下图的 下标2 

![image-20211215141057567](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211215141057567.png)





![image-20211215141507630](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211215141507630.png)



- supportsParameter方法的作用: 是判断当前解析器是否支持解析这种参数
- 支持就调用 resolveArgument方法(解析方法)



#### 4、返回值处理器

![image-20211215142359811](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211215142359811.png)



#### 5 .如何确定目标方法每一个参数的值

在这个类中 InvocableHandlerMethod

```java
protected Object[] getMethodArgumentValues(NativeWebRequest request, @Nullable ModelAndViewContainer mavContainer,
      Object... providedArgs) throws Exception {

   MethodParameter[] parameters = getMethodParameters();// 获取参数详细信息
   if (ObjectUtils.isEmpty(parameters)) {// 判断这个 参数是不是为空
      return EMPTY_ARGS;
   }

   Object[] args = new Object[parameters.length];//  parameters.length 参数的长度 
    
   for (int i = 0; i < parameters.length; i++) {
      MethodParameter parameter = parameters[i];
      parameter.initParameterNameDiscovery(this.parameterNameDiscoverer);
      args[i] = findProvidedArgument(parameter, providedArgs);
      if (args[i] != null) {
         continue;
      }
      if (!this.resolvers.supportsParameter(parameter)) {// 判断当前解析器支不支持这种参数类型
         throw new IllegalStateException(formatArgumentError(parameter, "No suitable resolver"));
      }
      try {
         args[i] = this.resolvers.resolveArgument(parameter, mavContainer, request, this.dataBinderFactory);
      }
      catch (Exception ex) {
         // Leave stack trace for later, exception may actually be resolved and handled...
         if (logger.isDebugEnabled()) {
            String exMsg = ex.getMessage();
            if (exMsg != null && !exMsg.contains(parameter.getExecutable().toGenericString())) {
               logger.debug(formatArgumentError(parameter, exMsg));
            }
         }
         throw ex;
      }
   }
   return args;
}
```





##### 5.1、挨个判断所有参数解析器那个支持解析这个参数

```java
	@Nullable
	private HandlerMethodArgumentResolver getArgumentResolver(MethodParameter parameter) {
		HandlerMethodArgumentResolver result = this.argumentResolverCache.get(parameter);
		if (result == null) {
			for (HandlerMethodArgumentResolver resolver : this.argumentResolvers) {
				if (resolver.supportsParameter(parameter)) {
					result = resolver;
					this.argumentResolverCache.put(parameter, result);
					break;
				}
			}
		}
		return result;
	}
```

##### 5.2、解析这个参数的值

```java
调用各自 HandlerMethodArgumentResolver 的 resolveArgument 方法即可
```

##### 5.3、自定义类型参数 封装POJO

**ServletModelAttributeMethodProcessor  这个参数处理器支持**

 **是否为简单类型。**

```java
public static boolean isSimpleValueType(Class<?> type) {
		return (Void.class != type && void.class != type &&
				(ClassUtils.isPrimitiveOrWrapper(type) ||
				Enum.class.isAssignableFrom(type) ||
				CharSequence.class.isAssignableFrom(type) ||
				Number.class.isAssignableFrom(type) ||
				Date.class.isAssignableFrom(type) ||
				Temporal.class.isAssignableFrom(type) ||
				URI.class == type ||
				URL.class == type ||
				Locale.class == type ||
				Class.class == type));
    // 判断是不是这些简单类型
	}

```





```java
	
@Override
	@Nullable
	public final Object resolveArgument(MethodParameter parameter,
                                        @Nullable ModelAndViewContainermavContainer,
			                            NativeWebRequest webRequest,
                                        @Nullable WebDataBinderFactory binderFactory) throws Exception {
        
     Assert.state(mavContainer != null, "ModelAttributeMethodProcessor requires ModelAndViewContainer");
	Assert.state(binderFactory != null, "ModelAttributeMethodProcessor requires WebDataBinderFactory");

	String name = ModelFactory.getNameForParameter(parameter);
	ModelAttribute ann = parameter.getParameterAnnotation(ModelAttribute.class);
	if (ann != null) {
		mavContainer.setBinding(name, ann.binding());
	}

	Object attribute = null;
	BindingResult bindingResult = null;

	if (mavContainer.containsAttribute(name)) {
		attribute = mavContainer.getModel().get(name);
	}
	else {
		// Create attribute instance
		try {
			attribute = createAttribute(name, parameter, binderFactory, webRequest);
		}
		catch (BindException ex) {
			if (isBindExceptionRequired(parameter)) {
				// No BindingResult parameter -> fail with BindException
				throw ex;
			}
			// Otherwise, expose null/empty value and associated BindingResult
			if (parameter.getParameterType() == Optional.class) {
				attribute = Optional.empty();
			}
			bindingResult = ex.getBindingResult();
		}
	}

	if (bindingResult == null) {
		// Bean property binding and validation;
		// skipped in case of binding failure on construction.
		WebDataBinder binder = binderFactory.createBinder(webRequest, attribute, name);
		if (binder.getTarget() != null) {
			if (!mavContainer.isBindingDisabled(name)) {
				bindRequestParameters(binder, webRequest);
			}
			validateIfApplicable(binder, parameter);
			if (binder.getBindingResult().hasErrors() && isBindExceptionRequired(binder, parameter)) {
				throw new BindException(binder.getBindingResult());
			}
		}
		// Value type adaptation, also covering java.util.Optional
		if (!parameter.getParameterType().isInstance(attribute)) {
			attribute = binder.convertIfNecessary(binder.getTarget(), parameter.getParameterType(), parameter);
		}
		bindingResult = binder.getBindingResult();
	}

	// Add resolved attribute and BindingResult at the end of the model
	Map<String, Object> bindingResultModel = bindingResult.getModel();
	mavContainer.removeAttributes(bindingResultModel);
	mavContainer.addAllAttributes(bindingResultModel);

	return attribute;
}
```



### 

**WebDataBinder binder = binderFactory.createBinder(webRequest, attribute, name);**

**WebDataBinder :web数据绑定器，他的作用是将请求参数的值绑定到指定的JavaBean里面**

**WebDataBinder 利用它里面的 Converters 将请求数据转成指定的数据类型。再次封装到JavaBean中**



**GenericConversionService：在设置每一个值的时候，找它里面的所有converter那个可以将这个数据类型（request带来参数的字符串）转换到指定的类型（JavaBean -- Integer）**

**byte -- > file**



大概原理, 是先获取 post 请求的参数的值,  然后创建 一个空的 Person类, 因为他返回类型是Person类, 所以创建了空的Person

然后 比如设置age的值, 通过反射得到age这个属性的 类型, 因为request的参数是字符串类型,  那么**WebDataBinder 利用它里面的 Converters 将请求数据转成指定的数据类型。再次封装到JavaBean中**





@FunctionalInterface**public interface** Converter<S, T>

### ![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1603337871521-25fc1aa1-133a-4ce0-a146-d565633d7658.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_39%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)





![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1603338486441-9bbd22a9-813f-49bd-b51b-e66c7f4b8598.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_44%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)





未来我们可以给WebDataBinder里面放自己的Converter；

**private static final class** StringToNumber<T **extends** Number> **implements** Converter<String, T>  意思是 把String类型 , 转换成自己要的类型





如果想 宠物 这个属性, 就这样写   宠物： <input name="pet" value="啊猫,3"/> value中利用, 隔开,  啊猫表示Pe类的name属性, 3 表示Pet的age属性 那么就要自定义Converter了

```html
<form action="/saveuser" method="post">
    姓名： <input name="userName" value="zhangsan"/> <br/>
    年龄： <input name="age" value="18"/> <br/>
    生日： <input name="birth" value="2019/12/10"/> <br/>
<!--    宠物姓名：<input name="pet.name" value="阿猫"/><br/>-->
<!--    宠物年龄：<input name="pet.age" value="5"/>-->
    宠物： <input name="pet" value="啊猫,3"/>
    <input type="submit" value="保存"/>
</form>
```



**自定义 Converter**

```java


            
           @Override
            public void addFormatters(FormatterRegistry registry) {
                registry.addConverter(new Converter<String, Pet>() {

                    @Override
                    public Pet convert(String source) {
                        // 啊猫,3
                        if(!StringUtils.isEmpty(source)){
                            Pet pet = new Pet();
                            String[] split = source.split(",");
                            pet.setName(split[0]);
                            pet.setAge(Integer.parseInt(split[1]));
                            return pet;
                        }
                        return null;
                    }
                });
            }
        };
    }
```





#### 6、目标方法执行完成

将所有的数据都放在 **ModelAndViewContainer**；包含要去的页面地址View。还包含Model数据。

![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1603272018605-1bce3142-bdd9-4834-a028-c753e91c52ac.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_16%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

#### 7、处理派发结果

**processDispatchResult**(processedRequest, response, mappedHandler, mv, dispatchException);

renderMergedOutputModel(mergedModel, getRequestToExpose(request), response);





```java
InternalResourceView：
@Override
	protected void renderMergedOutputModel(
			Map<String, Object> model, HttpServletRequest request, HttpServletResponse response) throws Exception {	

// Expose the model object as request attributes.
	exposeModelAsRequestAttributes(model, request);

	// Expose helpers as request attributes, if any.
	exposeHelpers(request);

	// Determine the path for the request dispatcher.
	String dispatcherPath = prepareForRendering(request, response);

	// Obtain a RequestDispatcher for the target resource (typically a JSP).
	RequestDispatcher rd = getRequestDispatcher(request, dispatcherPath);
	if (rd == null) {
		throw new ServletException("Could not get RequestDispatcher for [" + getUrl() +
				"]: Check that the corresponding file exists within your web application archive!");
	}

	// If already included or response already committed, perform include, else forward.
	if (useInclude(request, response)) {
		response.setContentType(getContentType());
		if (logger.isDebugEnabled()) {
			logger.debug("Including [" + getUrl() + "]");
		}
		rd.include(request, response);
	}

	else {
		// Note: The forwarded resource is supposed to determine the content type itself.
		if (logger.isDebugEnabled()) {
			logger.debug("Forwarding to [" + getUrl() + "]");
		}
		rd.forward(request, response);
	}
}
```





```java
暴露模型作为请求域属性
// Expose the model object as request attributes.
		exposeModelAsRequestAttributes(model, request);
```



```java
protected void exposeModelAsRequestAttributes(Map<String, Object> model,
			HttpServletRequest request) throws Exception {

    //model中的所有数据遍历挨个放在请求域中
		model.forEach((name, value) -> {
			if (value != null) {
				request.setAttribute(name, value);
			}
			else {
				request.removeAttribute(name);
			}
		});
	}
```









## 4、数据响应与内容协商

![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1606043749073-2573e24a-9ea9-459e-ad94-a433e1082624.png)



### 1、响应JSON

#### 1.1、jackson.jar+@ResponseBody

想要字符串或者对象, 响应JSON 必须想要jackson.jar和 @ResponseBody注解

需要导入 web的 starter

    <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
因为web场景自动引入了json场景

````java
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-json</artifactId>
      <version>2.3.4.RELEASE</version>
      <scope>compile</scope>
    </dependency>
````

json场景中 又有其他需要的jar包

<img src="https://cdn.nlark.com/yuque/0/2020/png/1354552/1605151090728-f7c60e6f-d0c0-4541-bfa3-8cc805dfd5d6.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_21%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10" alt="image.png" style="zoom:50%;" />



就会给前端自动返回json数据；





##### 1、返回值解析器

![image-20211221150825070](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211221150825070.png)



在这他利用所有的返回值处理器来 处理返回值

ServletInvocableHandlerMethod类中的 123行

```java
try {
   this.returnValueHandlers.handleReturnValue(
         returnValue, getReturnValueType(returnValue), mavContainer, webRequest);
}
```



关键的方法

```java
@Override   // 处理返回值方法
public void handleReturnValue(@Nullable Object returnValue, MethodParameter returnType,
      ModelAndViewContainer mavContainer, NativeWebRequest webRequest) throws Exception {
    /**先把返回值(returnValue)拿到, 返回值的类型(returnType)也拿到, 然后
    第一步找那个处理器能处理
    */
   HandlerMethodReturnValueHandler handler = selectHandler(returnValue, returnType);// 1
   if (handler == null) {
      throw new IllegalArgumentException("Unknown return value type: " + returnType.getParameterType().getName());
   }
    // 找到返回值处理器以后, 处理
   handler.handleReturnValue(returnValue, returnType, mavContainer, webRequest);
}
```

进入selectHandler方法  上面的标注1的

```java
@Nullable
private HandlerMethodReturnValueHandler selectHandler(@Nullable Object value, MethodParameter returnType) {
   boolean isAsyncValue = isAsyncReturnValue(value, returnType);// 判断是不是一个异步返回值
   for (HandlerMethodReturnValueHandler handler : this.returnValueHandlers) { // 遍历所有的返回值处理器
      if (isAsyncValue && !(handler instanceof AsyncHandlerMethodReturnValueHandler)) {
         continue;
      }
      if (handler.supportsReturnType(returnType)) {// 判断那个处理器能处理
         return handler;
      }
   }
   return null;
}
```



```java
	// RequestResponseBodyMethodProcessor  	类中的方法
@Override
	public void handleReturnValue(@Nullable Object returnValue, MethodParameter returnType,
			ModelAndViewContainer mavContainer, NativeWebRequest webRequest)
			throws IOException, HttpMediaTypeNotAcceptableException, HttpMessageNotWritableException {
	mavContainer.setRequestHandled(true);
	ServletServerHttpRequest inputMessage = createInputMessage(webRequest);
	ServletServerHttpResponse outputMessage = createOutputMessage(webRequest);

	// Try even with null return value. ResponseBodyAdvice could get involved.
    // 使用消息转换器进行写出操作  
	writeWithMessageConverters(returnValue, returnType, inputMessage, outputMessage);
}
```





##### 2、返回值解析器原理

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211221154254719.png" alt="image-20211221154254719" style="zoom:83%;" />



- 1、返回值处理器判断是否支持这种类型返回值 supportsReturnType方法

- 2、如果supportsReturnType方法返回值为true,处理器会调用 handleReturnValue 进行处理

- 3、RequestResponseBodyMethodProcessor 可以处理返回值标了@ResponseBody 注解的。

  - 利用 MessageConverters 进行处理 将数据写为json

    1.  内容协商（浏览器默认会以请求头的方式告诉服务器他能接受什么样的内容类型）

       ```java
       // 浏览器默认会以请求头的方式告诉服务器他能接受什么样的内容类型 
       text/html,application/xhtml+xml,application/xml;q=0.9,
       image/avif,image/webp,image/apng,*/*;q=0.8,// 可以看到这里有一个*/* // 如果浏览器所有的类型服务器都不能支持,那么这时候就看 服务器支持什么类型了 0.9优先于0.8
       application/signed-exchange;v=b3;q=0.9 
       
       ```

       ![image-20211222160205104](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211222160205104.png)

       ![image-20211222160834544](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211222160834544.png)

    2. 服务器最终根据自己自身的能力，决定服务器能生产出什么样内容类型的数据，

       ![image-20211222160901414](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211222160901414.png)

       ```java
       // AbstractMessageConverterMethodProcessor 类
       
       MediaType selectedMediaType = null;
       MediaType contentType = outputMessage.getHeaders().getContentType();
       boolean isContentTypePreset = contentType != null && contentType.isConcrete();
       if (isContentTypePreset) {
          if (logger.isDebugEnabled()) {
             logger.debug("Found 'Content-Type:" + contentType + "' in response");
          }
          selectedMediaType = contentType;
       }
       else {
          HttpServletRequest request = inputMessage.getServletRequest();
          List<MediaType> acceptableTypes = getAcceptableMediaTypes(request);// 浏览器会告诉服务器支持那些类型
           // 服务器支持的类型
          List<MediaType> producibleTypes = getProducibleMediaTypes(request, valueType, targetType);
       
          if (body != null && producibleTypes.isEmpty()) {
             throw new HttpMessageNotWritableException(
                   "No converter found for return value of type: " + valueType);
          }
           // 最后会协商, 也就是匹配服务器能使用那些类型
          List<MediaType> mediaTypesToUse = new ArrayList<>();
          for (MediaType requestedType : acceptableTypes) {
             for (MediaType producibleType : producibleTypes) {
                if (requestedType.isCompatibleWith(producibleType)) {
                   mediaTypesToUse.add(getMostSpecificMediaType(requestedType, producibleType));
                }
             }
          }
       ```

     3. SpringMVC会挨个遍历所有容器底层的 HttpMessageConverter ，看谁能处理？

        ​        <img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211222162334924.png" alt="image-20211222162334924" style="zoom:50%;" />

         HttpMessageConverter 方法, 判断支不支持pes对象以json类型读出来, 还有一个是写出去

  ​               1. 得到MappingJackson2HttpMessageConverter可以将对象写为json

  ​               2. 利用MappingJackson2HttpMessageConverter将对象转为json再写出去。





#### 1.2、SpringMVC到底支持哪些返回值

```tex
ModelAndView
Model
View
ResponseEntity 
ResponseBodyEmitter
StreamingResponseBody
HttpEntity
HttpHeaders
Callable
DeferredResult
ListenableFuture
CompletionStage
WebAsyncTask
有 @ModelAttribute注解 且为对象类型的
标注 @ResponseBody 注解 的   会被RequestResponseBodyMethodProcessor；解析器处理

```



#### 1.3、HTTPMessageConverter原理



##### 1、MessageConverter规范

![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605163447900-e2748217-0f31-4abb-9cce-546b4d790d0b.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_19%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

HttpMessageConverter(消息转换器)的作用: 看是否支持将 此 Class类型的对象，转为MediaType类型的数据。

例子：Person对象转为JSON。或者 JSON转为Person





##### 2. 默认的MessageConverter

![image-20211222163758912](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211222163758912.png)

0 - 只支持Byte类型的

1 - String     String有两个但是 字符编码不同  

2 - String

3 - Resource

4 - ResourceRegion

5 - DOMSource.class    SAXSource.**class**     StAXSource.**class **  StreamSource.**class**   Source.**class**

6 - MultiValueMap

7 - **true** 

**8 - true**

**9 - 支持注解方式xml处理的。**



最终 MappingJackson2HttpMessageConverter  把对象转为JSON（利用底层的jackson的objectMapper转换的）

![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605164243168-1a31e9af-54a4-463e-b65a-c28ca7a8a2fa.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_34%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)







### 2、内容协商

根据客户端接收能力不同，返回不同媒体类型的数据。

#### 1、引入xml依赖

```java
<dependency>
            <groupId>com.fasterxml.jackson.dataformat</groupId>
            <artifactId>jackson-dataformat-xml</artifactId>
</dependency>
```



#### 2、postman分别测试返回json和xml

只需要改变请求头中Accept字段。Http协议中规定的，告诉服务器本客户端可以接收的数据类型。

![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605173127653-8a06cd0f-b8e1-4e22-9728-069b942eba3f.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_33%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)



#### 3、开启浏览器参数方式内容协商功能

为了方便内容协商，开启基于请求参数的内容协商功能。

```yml
spring:
  mvc: 
    contentnegotiation:
      favor-parameter: true  #开启请求参数内容协商模式
```



发请求： http://localhost:8080/test/person?format=json

[http://localhost:8080/test/person?format=](http://localhost:8080/test/person?format=json)xml    这样控制类型



![image-20211222224759439](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211222224759439.png)

确定客户端接收什么样的内容类型；

1、Parameter策略优先确定是要返回json数据（获取请求头中的format的值）

![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605231074299-25f5b062-2de1-4a09-91bf-11e018d6ec0e.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_18%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

2、最终进行内容协商返回给客户端json即可。



#### 4、内容协商原理

- 1、判断当前响应头中是否已经有确定的媒体类型。MediaType

- **2、获取客户端（PostMan、浏览器）支持接收的内容类型。（获取客户端Accept请求头字段）【因为xml的优先级比较高所以在不强制要求那种类型的情况下, application/xml 暂时优先, 因为这里就支持两种 json和xml】**

  ```xml
  text/html,application/xhtml+xml,application/xml;q=0.9, // 0.9优先级高 
  image/avif,image/webp,image/apng,*/*;q=0.8,  
  application/signed-exchange;v=b3;q=0.9
  ```

- - **contentNegotiationManager 内容协商管理器 默认使用基于请求头的策略**

    ![image.png](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605230462280-ef98de47-6717-4e27-b4ec-3eb0690b55d0.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_15%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

    - - **HeaderContentNegotiationStrategy  确定客户端可以接收的内容类型** 

    - ![image.png](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605230546376-65dcf657-7653-4a58-837a-f5657778201a.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_28%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

- 3、遍历循环所有当前系统的 **MessageConverter**，看谁支持操作这个对象（Person）
- 4、找到支持操作Person的converter，把converter支持的媒体类型统计出来。

- 5、客户端需要【application/xml】。服务端能力【10种、json、xml】
-   ![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605173876646-f63575e2-50c8-44d5-9603-c2d11a78adae.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_20%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

- 6、进行内容协商的最佳匹配媒体类型
- 7、用 支持 将对象转为 最佳匹配媒体类型 的converter。调用它进行转化 

![image.png](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605173657818-73331882-6086-490c-973b-af46ccf07b32.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_18%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)



```java


MediaType selectedMediaType = null;
// 判断当前的响应头中是否已经有确定的媒体类型. MediaType
MediaType contentType = outputMessage.getHeaders().getContentType();
boolean isContentTypePreset = contentType != null && contentType.isConcrete();
// 如果有确定的媒体类型 就又之前确认的
if (isContentTypePreset) {
   if (logger.isDebugEnabled()) {
      logger.debug("Found 'Content-Type:" + contentType + "' in response");
   }
   selectedMediaType = contentType;
}

else {
    
   HttpServletRequest request = inputMessage.getServletRequest();
    // 获取客户端(浏览器或者其他应用)可接收 支持的内容类型
   List<MediaType> acceptableTypes = getAcceptableMediaTypes(request);
    // 获取服务器支持的内容类型
   List<MediaType> producibleTypes = getProducibleMediaTypes(request, valueType, targetType);

   if (body != null && producibleTypes.isEmpty()) {
      throw new HttpMessageNotWritableException(
            "No converter found for return value of type: " + valueType);
   }
   List<MediaType> mediaTypesToUse = new ArrayList<>();
   for (MediaType requestedType : acceptableTypes) { // 遍历浏览器可以接收的类型
      for (MediaType producibleType : producibleTypes) { // 服务器能输出的类型
         if (requestedType.isCompatibleWith(producibleType)) {// 有没有浏览器匹配服务器产出的类型
             // 如果有的话, 这里是确定最终使用的类型
            mediaTypesToUse.add(getMostSpecificMediaType(requestedType, producibleType));
         }
      }
   }
```

导入了jackson处理xml的包，xml的converter就会自动进来

```java
// 在这个WebMvcConfigurationSupport类
// 判断 jackson处理xml的类是否存在
jackson2XmlPresent = ClassUtils.isPresent("com.fasterxml.jackson.dataformat.xml.XmlMapper", classLoader);

// 如果存在 就会吧  xml的converter添加进去
if (jackson2XmlPresent) {
			Jackson2ObjectMapperBuilder builder = Jackson2ObjectMapperBuilder.xml();
			if (this.applicationContext != null) {
				builder.applicationContext(this.applicationContext);
			}
			messageConverters.add(new MappingJackson2XmlHttpMessageConverter(builder.build()));
		}
```





#### 5、自定义 MessageConverter

**实现多协议数据兼容。json、xml、x-guigu**

**0、**@ResponseBody 响应数据出去 调用 **RequestResponseBodyMethodProcessor** 处理

1、Processor 处理方法返回值。通过 **MessageConverter** 处理

2、所有 **MessageConverter** 合起来可以支持各种媒体类型数据的操作（读、写）

3、内容协商找到最终的 **messageConverter**；



SpringMVC的什么功能。一个入口给容器中添加一个  WebMvcConfigurer

```java
/**
   1. 浏览器发起请求直接返回xml   因为这个时候他定义了需要返回xml[application/xml]  这个时候就会被 jacksonXmlConverter处理
   2. 如果是ajax请求, 返回json 因为这个时候他定义了需要返回json[application/json]  这个时候就会被 jacksonJsonConverter处理
   3. 如果是自定义的发起请求, 返回自定义协议数据 [application/x-wbm]  这个时候就要创建 XXXCOnverter
   步骤:
     1. 添加自定义的MessageConverter进系统底层
     2. 系统底层就会统计出所有MessageConverter能操作那些类型
     3. 客户端内容协商[wbm--wbm](意思是 服务器和客户端(浏览器等), 服务器支持wbm, 客户端也支持  )
  

*/ 


@Bean
    public WebMvcConfigurer webMvcConfigurer(){
        return new WebMvcConfigurer() {
            /** 在 WebMvcConfigurer 中 实现extendMessageConverters 方法  
            */

            @Override
            public void extendMessageConverters(List<HttpMessageConverter<?>> converters) {
                    converters.add(new WbmConverter()); // 把我们自定义的Converter添加进去  
            }
        }
    }
```

自定义的Converter

```java
package com.wbm.converter;

import com.wbm.bean.Person;
import org.springframework.http.HttpInputMessage;
import org.springframework.http.HttpOutputMessage;
import org.springframework.http.MediaType;
import org.springframework.http.converter.HttpMessageConverter;
import org.springframework.http.converter.HttpMessageNotReadableException;
import org.springframework.http.converter.HttpMessageNotWritableException;

import java.io.IOException;
import java.io.OutputStream;
import java.nio.charset.StandardCharsets;
import java.util.List;


/**
 * 自定义的Converter
 */

public class WbmConverter implements HttpMessageConverter<Person> {

    // 能不能把 Person类型(因为这里泛型是Person) 读成某种类型
    @Override
    public boolean canRead(Class<?> clazz, MediaType mediaType) {
        return false;
    }

    // 能不能把 Person类型(因为这里泛型是Person) 写成某种类型
    @Override
    public boolean canWrite(Class<?> clazz, MediaType mediaType) {
        return clazz.isAssignableFrom(Person.class); // 如果类型为  Person类型 就返回true
    }


    /**
     * 服务器要统计所有MessageConverter 都能写出哪些内容类型, getSupportedMediaTypes方法 就是告诉springmvc这个MessageConverter
     *   能操作我们自定义类型 application/x-wbm 类型
     * @return
     */
    @Override
    public List<MediaType> getSupportedMediaTypes() {
        return MediaType.parseMediaTypes("application/wbm");
    }

    @Override
    public Person read(Class<? extends Person> clazz, HttpInputMessage inputMessage) throws IOException, HttpMessageNotReadableException {
        return null;
    }

    @Override
    public void write(Person person, MediaType contentType, HttpOutputMessage outputMessage) throws IOException, HttpMessageNotWritableException {
            // 自定义协议数据写出, 相当于 名字;18;生日;宠物
        String data= person.getUserName()+";"+person.getAge()+";"+person.getBirth()+";"+person.getPet();
        // 写出去
        OutputStream body = outputMessage.getBody();
       body.write(data.getBytes());
    }
}
```



测试:

在Postman中输入: localhost:8080/test/per 

然后把类型 改为自定义的类型 wbm 

![image-20211224212105798](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211224212105798.png)





如果在  format 这里指定为 wbm类型 会报错

http://localhost:8080/test/per?format=wbm

![image-20211224212342216](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211224212342216.png)





如果想  format 这里指定为 wbm类型 有两种方法

第一种: 在 webMvcConfigurer方法 中 实现 configureContentNegotiation (翻译为:配置内容协商)方法

```java
@Bean
public WebMvcConfigurer webMvcConfigurer() {
    return new WebMvcConfigurer() {
        
        @Override
        public void configureContentNegotiation(ContentNegotiationConfigurer configurer) {
            // 调用 ContentNegotiationConfigurer 的mediaType 方法, 第一个参数是 : format=的参数 , 第二个是类型 application/json 等 或者自定义的
            configurer.mediaType("xio", MediaType.parseMediaType("application/wbm"));
        }
    };

}
```



测试 :

![image-20211224214424176](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211224214424176.png)



第二种: yml 配置

```yml
spring:
    mvc:
      contentnegotiation:
        media-types: # format  参数设置
         gg: application/wbm  # gg表示 format=的参数  指定application/wbm这个的类型
```



![image-20211224214802732](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211224214802732.png)







## 5、视图解析与模板引擎

视图解析：**SpringBoot默认不支持 JSP，需要引入第三方模板引擎技术实现页面渲染。**

### 1、视图解析

![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1606043749039-cefbf687-4feb-441d-bad8-c6d933248d3c.png)

#### 1、视图解析原理流程

1、目标方法处理的过程中，所有数据都会被放在 **ModelAndViewContainer 里面。包括数据和视图地址**

**2、方法的参数是一个自定义类型对象（从请求参数中确定的），把他重新放在** **ModelAndViewContainer** 

**3、任何目标方法执行完成以后都会返回 ModelAndView（****数据和视图地址****）。**

**4、****processDispatchResult  处理派发结果（页面改如何响应）**

- 1、**render**(**mv**, request, response); 进行页面渲染逻辑

- - 1、根据方法的String返回值得到 **View** 对象【定义了页面的渲染逻辑】

- - - 1、所有的视图解析器尝试是否能根据当前返回值得到**View**对象
    - 2、得到了  **redirect:/main.html** --> Thymeleaf new **RedirectView**()

- - - 3、ContentNegotiationViewResolver 里面包含了下面所有的视图解析器，内部还是利用下面所有视图解析器得到视图对象。
    - 4、view.render(mv.getModelInternal(), request, response);   视图对象调用自定义的render进行页面渲染工作

- - - - **RedirectView 如何渲染【重定向到一个页面】**
      - **1、获取目标url地址**

- - - - **2、****response.sendRedirect(encodedURL);**





**视图解析：**

- - **返回值以 forward: 开始： new InternalResourceView(forwardUrl); -->  转发****request.getRequestDispatcher(path).forward(request, response);** 
  - **返回值以** **redirect: 开始：** **new RedirectView() --》 render就是重定向** 

- - **返回值是普通字符串： new ThymeleafView（）--->** 





自定义视图解析器+自定义视图； **大厂学院。**









![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605680247945-088b0f17-185c-490b-8889-103e8b4d8c07.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_16%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605679959020-54b96fe7-f2fc-4b4d-a392-426e1d5413de.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_23%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)



![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605679471537-7db702dc-b165-4dc6-b64a-26459ee5fd6c.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_17%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)



![img](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605679913592-151a616a-c754-4da3-a2c1-91dc0230a48d.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_22%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)

### 2、模板引擎-Thymeleaf

#### 1、thymeleaf简介

Thymeleaf is a modern server-side Java template engine for both web and standalone environments, capable of processing HTML, XML, JavaScript, CSS and even plain text.

**现代化、服务端Java模板引擎**



#### 2、基本语法

##### 1、表达式

| 表达式名字 | 语法   | 用途                               |
| ---------- | ------ | ---------------------------------- |
| 变量取值   | ${...} | 获取请求域、session域、对象等值    |
| 选择变量   | *{...} | 获取上下文对象值                   |
| 消息       | #{...} | 获取国际化等值                     |
| 链接       | @{...} | 生成链接                           |
| 片段表达式 | ~{...} | jsp:include 作用，引入公共页面片段 |



##### 2、字面量

文本值: **'one text'** **,** **'Another one!'** **,…**数字: **0** **,** **34** **,** **3.0** **,** **12.3** **,…**布尔值: **true** **,** **false**

空值: **null**

变量： one，two，.... 变量不能有空格

##### 3、文本操作

字符串拼接: **+**

变量替换: **|The name is ${name}|** 



##### 4、数学运算

运算符: + , - , * , / , %



##### 5、布尔运算

运算符:  **and** **,** **or**

一元运算: **!** **,** **not** 





##### 6、比较运算

比较: **>** **,** **<** **,** **>=** **,** **<=** **(** **gt** **,** **lt** **,** **ge** **,** **le** **)**等式: **==** **,** **!=** **(** **eq** **,** **ne** **)** 



##### 7、条件运算

If-then: **(if) ? (then)**

If-then-else: **(if) ? (then) : (else)**

Default: (value) **?: (defaultvalue)** 



##### 8、特殊操作

无操作： _



#### 3、设置属性值-th:attr

设置单个值

```html
<form action="subscribe.html" th:attr="action=@{/subscribe}">
  <fieldset>
    <input type="text" name="email" />
    <input type="submit" value="Subscribe!" th:attr="value=#{subscribe.submit}"/>
  </fieldset>
</form>
```

设置多个值

```html
<img src="../../images/gtvglogo.png"  th:attr="src=@{/images/gtvglogo.png},title=#{logo},alt=#{logo}" />
```



以上两个的代替写法 th:xxxx

```java
<input type="submit" value="Subscribe!" th:value="#{subscribe.submit}"/>
<form action="subscribe.html" th:action="@{/subscribe}">
```



所有h5兼容的标签写法

https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#setting-value-to-specific-attributes



#### 4、迭代

```html
<tr th:each="prod : ${prods}">
        <td th:text="${prod.name}">Onions</td>
        <td th:text="${prod.price}">2.41</td>
        <td th:text="${prod.inStock}? #{true} : #{false}">yes</td>
</tr>
```



```java
<tr th:each="prod,iterStat : ${prods}" th:class="${iterStat.odd}? 'odd'">
  <td th:text="${prod.name}">Onions</td>
  <td th:text="${prod.price}">2.41</td>
  <td th:text="${prod.inStock}? #{true} : #{false}">yes</td>
</tr>
```



#### 5、条件运算

```html
<a href="comments.html"
th:href="@{/product/comments(prodId=${prod.id})}"
th:if="${not #lists.isEmpty(prod.comments)}">view</a>
```



```html
<div th:switch="${user.role}">
  <p th:case="'admin'">User is an administrator</p>
  <p th:case="#{roles.manager}">User is a manager</p>
  <p th:case="*">User is some other thing</p>
</div>
```



#### 6、属性优先级

![image.png](https://cdn.nlark.com/yuque/0/2020/png/1354552/1605498132699-4fae6085-a207-456c-89fa-e571ff1663da.png?x-oss-process=image%2Fwatermark%2Ctype_d3F5LW1pY3JvaGVp%2Csize_44%2Ctext_YXRndWlndS5jb20g5bCa56GF6LC3%2Ccolor_FFFFFF%2Cshadow_50%2Ct_80%2Cg_se%2Cx_10%2Cy_10)





### 3、thymeleaf使用

#### 1、引入Starter

```xml
         <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>
```

在html 加上命名空间
<html lang="en" xmlns:th="http://www.thymeleaf.org">

#### 2、自动配置好了thymeleaf

```java
@Configuration(proxyBeanMethods = false)
@EnableConfigurationProperties(ThymeleafProperties.class)
@ConditionalOnClass({ TemplateMode.class, SpringTemplateEngine.class })
@AutoConfigureAfter({ WebMvcAutoConfiguration.class, WebFluxAutoConfiguration.class })
public class ThymeleafAutoConfiguration { }
```



自动配好的策略

- 1、所有thymeleaf的配置值都在 ThymeleafProperties
- 2、配置好了 **SpringTemplateEngine** 

- **3、配好了** **ThymeleafViewResolver** 
- 4、我们只需要直接开发页面

```java
// 默认的 templates 目录跟后缀
public static final String DEFAULT_PREFIX = "classpath:/templates/";// 表示在类路径的templates目录

public static final String DEFAULT_SUFFIX = ".html";  //xxx.html       html 后缀的
```



3. #### 页面开发

   写一个controller
   
   ```java
   @Controller
   public class ViewController {
   
       @GetMapping("/view/hello")
       public String hello(Model model){
           // model中的数据会被放在请求域中 request.setAttribute("a",hh)
           model.addAttribute("hello","你");
           model.addAttribute("like","http://www.baidu.com");
           return "hello";// 表示跳转到thymeleaf目录的 hello.html
       }
   }
   ```
   
   
   
   在写一个对应的 hello.html页面

   ```html
   <!DOCTYPE html>
   <!--xmlns:th="http://www.thymeleaf.org" thymeleaf的命名空间-->
   <html lang="en" xmlns:th="http://www.thymeleaf.org">
   <head>
       <meta charset="UTF-8">
       <title>Title</title>
   </head>
   <body>
   <h1 th:text="${hello}">哈哈</h1>
   
   <h2>
        <a th:href="${like}">跳转到百度</a> <br/>
        <a th:href="@{like}">跳转到百度</a>
   </h2>
   
   </body>
   </html>
   ```
   
   如果只访问这个页面是这样的, 因为没有对应的 like值, 所以不是超链接, 只是一个文本
   
   ![image-20220102132054105](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102132054105.png)



使用controller 访问

http://localhost:8080/view/hello

是这样的, 可以看到两个超链接出来了

![image-20220102132707108](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102132707108.png)



跳转第一个百度

可以看到成功 跳到百度了

![image-20220102132852035](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102132852035.png)



第二个 百度, 可以看到他, 跳到的是http://localhost:8080/view/like 

![image-20220102132958916](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102132958916.png)

可以得出, 

href="${like}" 的 ${like} 里面的值如果是一个链接, 点他会跳到这个链接

href="@{like}  的 @{like} 他会跳到  http://localhost:8080/view/ 这个目录下的  @xxx(like) 链接



把like改为uu

```html
<a th:href="@{uu}">跳转到百度</a>
```

![image-20220102133558467](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102133558467.png)

就会变成 http://localhost:8080/view/uu



如果在uu 的全面在加一个/

```html
<a th:href="@{/uu}">跳转到百度</a>
```

他会跳转到http://localhost:8080/uu

![image-20220102134141408](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102134141408.png)











### 4、构建后台管理系统

#### 1、项目创建

需要导入中心依赖thymeleaf、web-starter、devtools、lombok



#### 2、静态资源处理

自动配置好，我们只需要把所有静态资源放到 static 文件夹下

#### 3、路径构建

th:action="@{/login}" 

#### 4、模板抽取

th:insert/replace/include   



#### 5、页面跳转

```java
    @PostMapping("/login")
    public String main(User user, HttpSession session, Model model){

        if(StringUtils.hasLength(user.getUserName()) && "123456".equals(user.getPassword())){
            //把登陆成功的用户保存起来
            session.setAttribute("loginUser",user);
            //登录成功重定向到main.html;  重定向防止表单重复提交
            return "redirect:/main.html";
        }else {
            model.addAttribute("msg","账号密码错误");
            //回到登录页面
            return "login";
        }

    }
```



#### 6、数据渲染

```java
    @GetMapping("/dynamic_table")
    public String dynamic_table(Model model){
        //表格内容的遍历
        List<User> users = Arrays.asList(new User("zhangsan", "123456"),
                new User("lisi", "123444"),
                new User("haha", "aaaaa"),
                new User("hehe ", "aaddd"));
        model.addAttribute("users",users);

        return "table/dynamic_table";
    }

        <table class="display table table-bordered" id="hidden-table-info">
        <thead>
        <tr>
            <th>#</th>
            <th>用户名</th>
            <th>密码</th>
        </tr>
        </thead>
        <tbody>
        <tr class="gradeX" th:each="user,stats:${users}">
            <td th:text="${stats.count}">Trident</td>
            <td th:text="${user.userName}">Internet</td>
            <td >[[${user.password}]]</td>
        </tr>
        </tbody>
        </table>
```



# 
