# 环境配置

IDEA-2020.2.3    plugins : Spring Assistant ,  Lombok

maven-3.6.3



# HelloWorldApplication

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class HelloWorldApplication {

	public static void main(String[] args) {
		SpringApplication.run(HelloWorldApplication.class, args);
	}

}
```



# HelloWorldController

```java
package com.example.demo;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloWorldController {

    @RequestMapping("/hello")
    public String hello(){
        return "Hello Spring Boot!";
    }

}
```



# 测试

浏览器访问 localhost:8080/hello

8080端口为默认设置

修改的方法：在application.properties文件中添加server.port=8083