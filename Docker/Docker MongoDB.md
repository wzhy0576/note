```sh
sudo docker pull mongo
```



```sh
sudo docker run -e MONGO_INITDB_USERNAME=root -e MONGO_INITDB_PASSWORD=123456 -p 27017:27017 --name MongoDB -d mongo
```



```sh
docker exec -it MongoDB mongo admin
```



```sh
# 创建一个名为 admin，密码为 123456 的用户。
>  db.createUser({ user:'admin',pwd:'123456',roles:[ { role:'userAdminAnyDatabase', db: 'admin'},"readWriteAnyDatabase"]});
```



```sh
# 尝试使用上面创建的用户信息进行连接。
> db.auth('admin', '123456')
```



关于远程登录的配置，不知道有没有用

https://www.jianshu.com/p/b8c69964a307



more information :

https://www.runoob.com/docker/docker-install-mongodb.html

https://hub.docker.com/_/mongo