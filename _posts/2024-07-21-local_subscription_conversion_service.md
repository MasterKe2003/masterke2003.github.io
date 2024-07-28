---
title: "本地订阅转换服务搭建"
date: 2024-07-21 22:42:01 +0800
tags: [fq,clash]
---

为了防止订阅链接泄露，在本地搭建一个订阅转换服务是必要的。

### 后端项目安装

```bash
docker run -d --restart=always -p 25500:25500 tindy2013/subconverter:latest
```

安装结束后，我们使用以下命令验证安装是否成功：

```bash
curl http://localhost:25500/version
```

如果出现 subconverter vx.x.x backend 则说明容器已经成功运行。

### 前端项目安装

```bash
git clone https://github.com/CareyWang/sub-web.git
```

然后进入该项目文件夹，修改 .env 文件的内容，即如下所示：

```bash
VUE_APP_PROJECT = "https://github.com/CareyWang/sub-web"

VUE_APP_BOT_LINK = "https://t.me/subconverter_discuss"

VUE_APP_BACKEND_RELEASE = "https://github.com/tindy2013/subconverter/actions"

VUE_APP_SUBCONVERTER_REMOTE_CONFIG = "https://raw.githubusercontent.com/tindy2013/subconverter/master/base/config/example_external_config.ini"

# API 后端
VUE APP SUBCONVERTER DEFAULT BACKEND = "http://127.0.0.1:25500"

# 短链接后端
VUE_APP_MYURLS_API = "https://suo.yt/short"

# 文本托管后端
VUE_APP_CONFIG_UPLOAD_API = "https://oss.wcc.best/upload"

# 页面配置
VUE_APP_USE_STORAGE = true 
VUE_APP_CACHE_TTL = 86400
```

然后在项目主目录下，运行以下命令构建并运行该项目：

```bash
docker build -t subweb-local:latest .
docker run -d -p 58080:80 --restart always --name subweb subweb-local:latest
```

使用`http://ip:58080/`访问项目。

