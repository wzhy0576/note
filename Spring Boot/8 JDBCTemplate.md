# Prepare Database

**Ubuntu 18.04 server** with ip 106.15.102.20

**Docker mysql 8.0.22** user admin password 123456 with appropriate permissions to user database book



# application.properties

```properties
spring.datasource.url=jdbc:mysql://106.15.102.20/book?useUnicode=true&characterEncoding=utf-8&serverTimezone=UTC&useSSL=true
spring.datasource.username=admin
spring.datasource.password=123456
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```



# User Bean

```java
package com.example.demo;

import lombok.Data;
import org.springframework.jdbc.core.RowMapper;
import java.sql.ResultSet;
import java.sql.SQLException;

@Data
public class User implements RowMapper<User> {
    private int id;
    private String username;
    private String password;

    @Override
    public User mapRow(ResultSet resultSet, int id) throws SQLException {
        User user = new User();
        user.setId(resultSet.getInt("id"));
        user.setUsername(resultSet.getString("username"));
        user.setPassword(resultSet.getString("password"));
        return user;
    }

}
```





# CRUD Test

```java
package com.example.demo;

import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.jdbc.core.BeanPropertyRowMapper;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.test.context.junit4.SpringRunner;

import java.util.List;

@SpringBootTest
@RunWith(SpringRunner.class)
public class UserControllerTest {
    @Autowired
    private JdbcTemplate jdbcTemplate;

    @Test
    // create table
    public void createUserTable() throws Exception {
        String sql = "CREATE TABLE user(\n" +
                "id int(10) PRIMARY KEY AUTO_INCREMENT,\n" +
                "username varchar(100) DEFAULT NULL,\n" +
                "password varchar(100) DEFAULT NULL\n" +
                ") ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;\n";
        jdbcTemplate.execute(sql);
    }

    @Test
    // add user
    public void saveUser() throws Exception {
        String sql = "INSERT INTO user (USERNAME, PASSWORD) VALUES ('xiaoming','123456')";
        int successRows = jdbcTemplate.update(sql);
        System.out.println(successRows);
    }

    @Test
    // find user
    public void getUserByName() throws Exception {
        String name = "xiaoming";
        String sql = "SELECT * FROM user WHERE username = ?";
        List<User> list = jdbcTemplate.query(sql, new User(), new Object[]{name});
        for (User user : list) {
            System.out.println(user);
        }
    }

    @Test
    // find all
    public void getAllUser() throws Exception {
        String sql = "SELECT * FROM user";
        List<User> list = jdbcTemplate.query(sql, new BeanPropertyRowMapper(User.class));
        for (User user : list) {
            System.out.println(user);
        }
    }

    @Test
    // update user
    public void updateUserPassword() throws Exception {
        Integer id = 1;
        String newPassword = "999999";
        String sql = "UPDATE user SET password = ? WHERE id = ?";
        int successRow = jdbcTemplate.update(sql, newPassword, id);
        System.out.println(successRow);
    }

    @Test
    // delete user
    public void deleteUser() throws Exception {
        String sql = "DELETE FROM user WHERE id = ?";
        int rows = jdbcTemplate.update(sql, 1);
        System.out.println(rows);
    }
    
}
```

