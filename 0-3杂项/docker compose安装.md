使用 debian 系统

官网：[docker/compose: Define and run multi-container applications with Docker (github.com)](https://github.com/docker/compose)

# 下载二进制文件

在官网直接下载二进制可执行文件

```
wgat https://github.com/docker/compose/releases/download/v2.29.2/docker-compose-linux-x86_64
```


# 给予权限

```
chmod +x docker-compose-linux-x86_64
```



# 移动至系统目录
```
 sudo mv docker-compose-linux-x86_64 /usr/local/bin/docker-compose
```

# 测试
```
docker-compose --version
```