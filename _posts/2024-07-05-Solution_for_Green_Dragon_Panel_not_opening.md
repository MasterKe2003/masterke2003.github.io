---
title: "青龙面板打不开的解决方案"
date: 2024-07-05 14:15:46 +0800
tags: [docker,linux,青龙面板]
---

直奔主题：
> 进入青龙docker容器
```
docker exec -it qinglong bash
```
> 检测依赖文件并修复
```
ql check
```
> 更新并重启青龙
```
ql update
```
> 重启docker容器
```
docker restart qinglong
```

或者使用watchtower自动更新
```
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower -cR qinglong
```