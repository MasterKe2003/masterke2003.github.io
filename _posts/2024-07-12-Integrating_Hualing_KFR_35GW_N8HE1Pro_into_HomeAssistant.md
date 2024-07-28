---
title: "华凌空调接入HA"
date: 2024-07-12 13:25:23 +0800
tags:[HomeAssistant,智能家居,空调]
---

## 背景

今年夏天格外的热，在网上观望了一下，最后买了这台网红小空调，型号是华凌KFR-35GW/N8HE1Pro。在这观望的期间还学到一个经验：空调安装外机一定要抽真空，不然制冷效果会大打折扣，而且因为现在的制冷液是可燃的，如果空气没有抽干的话，还有可能发生爆炸。

然后这台空调是支持智能控制的，准备折腾一下将其接入homeassistant，以便于远程控制。

## 过程

### 安装homeassistant

我是使用docker进行安装的，一行命令就可以搞定

```
docker run -d \
  --name homeassistant \
  --privileged \
  --restart=unless-stopped \
  -e TZ=Asia/Shanghai \
  -v /home/homeassistant:/config \
  --network=host \
  homeassistant/home-assistant
```

### 安装midea_ac_lan

github地址：https://github.com/georgezhao2010/midea_ac_lan

复制到homeassistant的custom_components目录下，然后重启homeassistant。

### 配置midea_ac_lan

1. 打开 Home Assistant 的配置菜单，找到“设备与服务”
2. 点击设备与服务页面最上方的“集成”这一项，之后点击集成页面右下角的“添加集成”，搜索“Midea AC LAN”
3. 之后点击查找出来的 Midea AC LAN 组件，会问你选择什么模式，一般的话选择 Auto 自动模式添加就可以了,我是在自动模式下遇到了一些问题，后来在[midea-ac-py](https://github.com/mill1000/midea-ac-py?tab=readme-ov-file#getting-device-info)这个项目中找到一个获取参数的办法，然后选择手动添加的，可以使用msmart-ngmidea-discover的命令获取设备信息：

```
pip install msmart-ng
msmart-ng discover
```

把对应的参数填进去就可以添加成功了。

## OVER

最后把卡片添加到主页就行了。