# Simple-webapplications-using-Spring-boot

<h1>Table of content</h1>

1.Java Spring Boot

2.Features of Spring Boot

3.Why is Spring Framework so popular?

4.Step to build web-application






<h2>Java Spring Boot:-</h2>

Java Spring Framework (Spring Framework) is a popular, open source, enterprise-level framework for creating standalone, production-grade applications that run on the Java Virtual Machine (JVM).
Java Spring Boot (Spring Boot) is a tool that makes developing web application and microservices with Spring Framework faster and easier through three core capabilities:



(I)Autoconfiguration

(II)An opinionated approach to configuration.

(III)The ability to create standalone applications.

These features work together to provide you with a tool that allows you to set up a Spring-based application with minimal configuration and setup.






<h1>Features of Spring Boot:-</h1>

(a)Create stand-alone Spring applications

(b)Embed Tomcat, Jetty or Undertow directly (no need to deploy WAR files)

(c)Provide opinionated 'starter' dependencies to simplify your build configuration

(d)Automatically configure Spring and 3rd party libraries whenever possible

(e)Provide production-ready features such as metrics, health checks, and externalized configuration

(f)Absolutely no code generation and no requirement for XML configuration

<br>


<h2>Why is Spring Framework so popular?</h2>



Spring Framework offers a dependency injection feature that lets objects define their own dependencies that the Spring container later injects into them. This enables developers to create modular applications consisting of loosely coupled components that are ideal for microservices and distributed network applications.

Spring Framework also offers built-in support for typical tasks that an application needs to perform, such as data binding, type conversion, validation, exception handling, resource and event management, internationalization, and more. It integrates with various Java EE technologies such as RMI (Remote Method Invocation), AMQP (Advanced Message Queuing Protocol), Java Web Services, and others. In sum, Spring Framework provides developers with all the tools and features the need to create loosely coupled, cross-platform Java EE applications that run in any environment.



<h1>Step to build web-application</h1>

●Download a ide for java (here i have used eclipse ide).<br>

●There are 2 ways for installing and using springboot's properties in the project:<br>

 Importing springboot through plugin or through downloading a zip file and importing in the ide.
 Downloading a zip file and importing in ide.
 
(1) Search "Spring initializr" on chrome.

(2)Add dependencies and other suitable settings and then generate the zip file.

(3)Import the zip file in your respective ide.

(4)After writing the code in the project, run the main java class which is present in src >>> main >>> java.

(5)Goto chrome and search localhost:8080/login



<h1>Implementations</h1>

<h4>Pom.xml</h4>

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.7.10</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.example</groupId>
	<artifactId>springbootjsp-demo</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>springbootjsp-demo</name>
	<description>Demo project for Spring Boot</description>
	<properties>
		<java.version>1.8</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
<!-- https://mvnrepository.com/artifact/org.apache.tomcat.embed/tomcat-embed-jasper -->
<dependency>
    <groupId>org.apache.tomcat.embed</groupId>
    <artifactId>tomcat-embed-jasper</artifactId>
    <scope>provided</scope>
</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<scope>runtime</scope>
			<optional>true</optional>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>

<h4>main page</h4>

package com.example.springbootjspdemo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.ComponentScan;

@SpringBootApplication
@ComponentScan("com.example.springbootjspdemo")
public class SpringbootjspDemoApplication {

	public static void main(String[] args) {
		SpringApplication.run(SpringbootjspDemoApplication.class, args);
	}

}

<h4>logincontroller page</h4>

package com.example.springbootjspdemo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.ModelMap;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class logincontroller {

	@RequestMapping(value="/login",method=RequestMethod.GET)
	public String loginPage() {
		return "login";
	}
	@RequestMapping(value="/login",method=RequestMethod.POST)
	public String welcomePage(ModelMap model,@RequestParam String username,@RequestParam String password) {
		if(username.equals("abhi123") && password.equals("Abhi")) {
			return "welcome";
		}
		model.put("errorMessage","Enter correct Username or Password ");
		return "login";
	}
}

<h4>Application.Properties</h4>

spring.mvc.view.prefix=/WEB-INF/jsp/
spring.mvc.view.suffix=.jsp

<h4>login.jsp page</h4>

<!DOCTYPE html>
<html lang="en">
<head> 
    
    <title>Login Form</title>
    <style>
        
        .container{
            text-align: center;
            background-color: blue;
            padding: 10px;
            padding-bottom: 15px;
        }
        body{
            font-family: sans-serif;
            font-size: 20px;
            padding-bottom: 10px solid floralwhite;
            margin: 10px;
            border: 1px solid black;
            margin-top: 3%;
            margin-left: 30%;
            margin-right: 30%;
            border-radius: 3px;
        }

        input[type="submit"]{
            font-family: sans-serif;
            background-color: rgb(253, 253, 255);
            padding-left: 30px;
            padding-right: 30px;
            margin: 10px;
        }
        input[type="submit"]:hover{
            background-color:black ;
            cursor: pointer;
        }
        
    </style>
</head>

<body>

	
    <form  method="post">
    <div class="container">
    <h2>Login Form</h2>
    <hr>
    <br>
    <p>Username: <input type="username" name="username"  placeholder="Enter username" required></p>
    <p>Password: <input type="password" name="password"  placeholder="Enter Password" required></p>
    <br>
    <input type="submit" value="submit">
    <br>
    <h2>${errorMessage}</h2>
    <br>
    </div>
    </form>
   
</body> 
</html>

<h4>welcome.jsp page</h4>
<!DOCTYPE html>
<html lang="en">
<head> 
    
    <title>Welcome</title>
    
</head>

<body><h1 style="background-color:DodgerBlue;"><center>Welcome!!!</center></h1>
   
</body> 
</html>
