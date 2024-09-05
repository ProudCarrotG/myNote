[QingdaoU/OnlineJudge: Open source online judge based on Vue, Django and Docker. | 青岛大学开源 Online Judge | QQ群 496710125 | admin@qduoj.com (github.com)](https://github.com/QingdaoU/OnlineJudge)

文档 [Quickstart (qduoj.com)](https://opensource.qduoj.com/#/en/guide/quickstart)

# clone 仓库
```
git clone -b $vx.x.x$ https://github.com/QingdaoU/OnlineJudgeDeploy.git

```

> $vx.x.x$ 对应不同的版本，需要前往官网查看对应版本



# 使用 docker-compose 管理

```
cd OnlineJudgeDeploy

#启动容器
docker compose up -d   
```


要**关闭**通过 docker compose up -d 启动的所有容器和服务，可以使用以下命令：
```
docker compose down
```

这个命令会停止并删除由 docker compose up 启动的所有容器、网络和卷 12。如果你只想停止容器而不删除它们，可以使用：
```
docker compose stop
```

这样，容器会**停止运行**，但不会被删除，你可以稍后使用 docker compose start 重新启动它们。

> !!! `docker compose down` 命令会删除数据，是个**危险**操作!!!
> 如需要暂停，使用 `docker compose stop`