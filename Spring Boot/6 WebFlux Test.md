# key word

Mono

Flux

ResponseEntity

Postman



# an Controller for User Bean

```java
package com.example.demo;

import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import reactor.core.publisher.Flux;
import reactor.core.publisher.Mono;

import javax.annotation.PostConstruct;
import java.util.HashMap;
import java.util.Map;
import java.util.stream.Collectors;

@RestController
@RequestMapping(path = "/user")
public class UserController {
    Map<Long, User> users = new HashMap<>();

    @PostConstruct
    public void init() throws Exception {
        users.put(Long.valueOf(1), new User(1, "xiaoming", 18));
        users.put(Long.valueOf(2), new User(2,"lihua",19));
    }

    // localhost:8080/user/1
    @GetMapping("/{id}")
    public Mono<User> getUser(@PathVariable long id) {
        return Mono.justOrEmpty(users.get(id));
    }

    @GetMapping("/list")
    public Flux<User> getAll() {
        return Flux.fromIterable(users.entrySet().stream()
        .map(entry->entry.getValue())
        .collect(Collectors.toList()));
    }

    @PostMapping("")
    public Mono<ResponseEntity<String>> addUser(User user) {
        users.put(user.getId(), user);
        return Mono.just(new ResponseEntity<String>("添加成功",HttpStatus.CREATED));
    }

    @PutMapping("/{id}")
    public Mono<ResponseEntity<User>> putUser(@PathVariable long id, User user) {
        user.setId(id);
        users.put(id, user);
        return Mono.just(new ResponseEntity<User>(user, HttpStatus.CREATED));
    }

    @DeleteMapping("/{id}")
    public Mono<ResponseEntity<String>> deleteUser(@PathVariable long id) {
        users.remove(id);
    return Mono.just(new ResponseEntity<String>("删除成功", HttpStatus.ACCEPTED));
    }
}

```



# test tool

Postman

