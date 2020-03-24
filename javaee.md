#### JavaWeb



#### Tomcat

一个web应用服务，web应用服务是运行在服务器主机上的一个服务，作用将可以被客户端访问到的资源存在在web应用服务中，启动服务，客户端可以通过访问该服务来获取资源，除此之外的资源客户端是无法直接访问的，就保证了服务器的安全性

#### Servlet

##### 简介

1. Servlet是Java Web提供的一个开发组件，是Java Web的基石，运行在Web容器中，负责与客户端通信。

2. Servlet是一个接口，该接口的作用的是让一个JavaBean具备处理客户端请求的能力，一个普通JavaBean实现Servlet接口之后，就成为一个控制器，可以处理客户端请求并且做出响应

   ​	

##### 生命周期

1. 当客户端请求浏览器时，首先在web容器中查找该Servlet实例是否存在，如果不存在，通过Xml解析 & 反射机制，调用无参构造创建该Servlet实例（Servlet必须有无参构造），否则直接进入进3步

   

2. 调用init方法，完成对该实例的初始化操作

3. 调用service方法，完成业务逻辑

4. 关闭web容器应用时，调用destroy方法，释放当前Servlet实例占用的资源

##### 生命周期方法

1. 无参构造        只执行一次，创建Servlet实例
2. init                   只执行一次，完成对Servlet实例对初始化操作
3. service           请求一次，执行一次
4. destroy          只执行一次，释放当前Servlet实例占用的资源



##### init

```java
public void init(ServletConfig servletConfig) {
	
}
```

##### ServletConfig

```xml
<servlet>
  <servlet-name>hello</servlet-name>
  <servlet-class>com.sinerry.controller.HelloServlet</servlet-class>
  <init-param>
    <param-name>user</param-name>
    <param-value>sinerry</param-value>
  </init-param>
  <init-param>
    <param-name>pwd</param-name>
    <param-value>123</param-value>
  </init-param>
</servlet>
<servlet-mapping>
  <servlet-name>hello</servlet-name>
  <url-pattern>/hello</url-pattern>
</servlet-mapping>
```



servletConfig获取Servlet相关配置的4个方法

```java
getServletName     		// 获取servlet在web.xml中配置的名字
getInitParameter   		// 获取servlet在web.xml中的初始化参数
getInitParameterNames // 获取所有的初始化参数的名字
getServletContext  		// 获取servlet的上下文，当前servlet对象的管理者
```

##### ServletConfig  vs  ServletContext

ServletConfig是某个Servlet的配置，每个Servlet都有一个ServletConfig，是一个局部对象

ServletContext作用整个web应用，一个web应用只有一个ServletContext，管理所有的Servlet，被多个Servlet共享，是一个全局对象

##### ServletContext

```xml
<context-param>
  <param-name>username</param-name>
  <param-value>admin</param-value>
</context-param>
<context-param>
  <param-name>password</param-name>
  <param-value>123123</param-value>
</context-param>
```



```java
getInitParameter()  		// 获取全局的Servlet初始化参数
getInitParameterNames() // 获取全局所有的初始化参数的名字
getServerInfo()         // 获取当前服务器信息
getContextPath()        // 获取当前Web应用路径
getRealPath()  					// 获取当前工程/资源在web容器中的绝对路径
```



##### Servlet体系层次结构

Servlet接口   <——  GenericServlet抽象类  <—— HttpServlet抽象类   <—— 自定义Servlet类













