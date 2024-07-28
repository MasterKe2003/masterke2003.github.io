---
title: "certbot配置免费https证书"
date: 2024-07-05 18:28:28 +0800
tags:[https证书,certbot]
---

## 安装certbot
> 更新系统软件包列表
```
sudo apt-get update
```
> 安装certbot
```
sudo apt-get install certbot
```

## 申请泛型域名证书
> 手动DNS验证
```
sudo certbot certonly -d *.masterke.cn --manual --preferred-challenges dns
```

按照提示输入您的邮箱地址，并确认您要申请证书的域名。Certbot会生成一段随机字符，您需要将这段字符作为TXT记录添加到您的域名DNS设置中。通常，这需要在您的域名注册商或DNS管理面板中完成。例如，如果您使用的是_acme-challenge.example.com作为记录名称，您需要添加一个TXT记录，其值为Certbot提供的随机字符。

> 验证DNS记录

在添加TXT记录后，可能需要一些时间才能在全球DNS系统中传播。等待一段时间后再点击回车。

> 查看证书文件

证书文件通常保存在/etc/letsencrypt/live/example.com/目录下。最后将证书正确配置到nginx服务器中。