```sh
docker pull redis
```



```sh
docker run --name Redis -p 6379:6379 -d redis
```



local connect :

```sh
redis-cli
```

```sh
127.0.0.1:6379> set name xiaoming
OK
127.0.0.1:6379> get name
"xiaoming"
# set auth password
127.0.0.1:6379> config set requirepass 123456
```



