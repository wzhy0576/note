# Controller

```java
package com.example.demo;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;

//MVC模式的控制器
@Controller
public class HelloWorldMvcController {

    @RequestMapping("/helloworld")
    public String helloWorld(Model model) throws Exception {
        model.addAttribute("mav", "Hello, 我现在是MVC结构！");
        //返回视图 resources/templates/example/hello.html
        return "example/hello";
    }
}

```



# View

```HTML
package com.example.demo;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;

//MVC模式的控制器
@Controller
public class HelloWorldMvcController {

    @RequestMapping("/helloworld")
    public String helloWorld(Model model) throws Exception {
        model.addAttribute("mav", "Hello, 我现在是MVC结构！");
        //返回视图 resources/templates/example/hello.html
        return "example/hello";
    }
}
```

path:

resources/templates/example/hello.html



# 测试

浏览器访问 localhost:8080/helloworld