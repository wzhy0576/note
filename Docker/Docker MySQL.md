# 环境 Ubuntu18.04 server



```sh
sudo docker pull mysql
```



-e MYSQL_ROOT_PASSWORD=123456   设置root用户密码

```sh
docker run --name mysql -e MYSQL_ROOT_PASSWORD=123456 -p 3306:3306 -d mysql
```



进入MySQL容器,连接MySQL

```sh
docker exec -it mysql /bin/bash
mysql -h localhost -u root -p
```



创建admin用户

```sh
CREATE USER 'admin'@'%' IDENTIFIED BY '123456';
```



为admin用户授予远程访问权限

```sh
ALTER USER 'admin'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
```



授予admin用户使用所有数据库中所有表的权限

```sql
GRANT ALL ON *.* TO 'admin'@'%';
```



刷新授权信息

```sql
FLUSH　PRIVILEGES;
```



验证外部连接

```sh
mysql -h [IP] -u admin -p
```

