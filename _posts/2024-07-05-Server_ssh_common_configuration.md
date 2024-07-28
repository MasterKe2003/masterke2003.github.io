---
title: "服务器ssh常用配置"
date: 2024-07-05 16:38:07 +0800
tags:[ssh,linux]
---

# 密码登录
> 打开配置文件
```
vim /etc/ssh/sshd_config
```
> 允许root认证登录
```
PermitRootLogin yes
```
> 允许密码认证
```
PasswordAuthentication yes
```
> 重启ssh服务
```
systemctl restart sshd
```
# 密钥登录
TODO