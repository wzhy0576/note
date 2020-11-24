# Passed an object from controller to view

```java
package com.example.demo;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.servlet.ModelAndView;

//MVC模式的控制器
@Controller
public class HelloWorldMvcController {

    @GetMapping("/mvcdemo")
    public ModelAndView hello() {
        //prepare data
        User user = new User();
        user.setName("小明");
        user.setId(1111);
        user.setAge(18);

        //path resources/templates/mvcdemo.html
        ModelAndView modelAndView = new ModelAndView("mvcdemo");
        modelAndView.addObject("user", user);
        return  modelAndView;
    }
}

```

