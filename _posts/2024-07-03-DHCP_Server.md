---
title: "配置DHCP服务器"
date: 2024-07-03 22:42:57 +0800
tags: [dhcp服务器,linux]
---

## 事前准备
- 开启电脑虚拟网卡【右下角网络-以太网-更改适配器设置-启用】
- virtualBox中centos7虚拟机挂载桌面文件CentOS-7-x86_64-DVD-1611.iso
- virtualBox中【工具】选择手动配置网卡，配置如下

```
ipv4:172.168.8.254
网络掩码:255.255.255.0
```
记得点击应用，然后启动虚拟机

## centos7虚拟机连接网络

> 右上角关机按钮 --> 有线设置 --> 右下角设置 --> ipv4 --> 配置如下

```
地址：172.168.81.1
网络掩码：255.255.255.0
网关：172.168.8.254
```

## 挂载磁盘

```
mkdir  /mnt/cdrom
mount  -r /dev/cdrom  /mnt/cdrom
cd  /etc/yum.repos.d
mkdir bac
mv *.repo bac
vim your_name.repo
```
按i输入下面：

```
[local]
name=local
baseurl=file:///mnt/cdrom
gpgcheck=0
enable=1
```

按esc然后冒号wq保存退出
输入```yum list ```检查是否配置成功

## 安装并启动dhcp

```
yum install dhcp
vim /etc/dhcp/dhcpd.conf
```

输入下面内容

```
subnet 172.168.8.0 netmask 255.255.255.0 {
  range 172.168.8.100 192.168.1.110;
  option routers 172.168.8.254;
  option broadcast-address 172.168.8.255;
  default-lease-time 600;
  max-lease-time 7200;
}
```

按esc然后冒号wq保存退出

`systemctl start dhcpd`启动dhcp服务

> 没有内容输出的话就是启动成功了，如果有错误信息的话可以使用`systemctl status dhcpd`查看报错信息，大概率是配置文件编写错误，仔细核对。

## 检验是否配置成功

> 将small虚拟机链接到仅主机的网卡上并且启动

```ip addr```查看地址，如果有了172.168.8.100的地址的话说明配置成功
但是可能还没有分配地址
```nmtui```重新激活网卡或者```systemctl restart network```
再次查看应该已经完成

> 根据网卡地址配置静态ip

返回centos虚拟机，再次编辑配置文件`vim /etc/dhcp/dhcpd.conf`，添加如下内容：

```
subnet 172.168.8.0 netmask 255.255.255.0{
  range 172.168.8.188 172.168.8.189;
  host test{
    hardware ethernet 08:00:27:3c:0e:1a;
    fixed-address 172.168.8.188;
}
}
```

保存退出后`systemctl restart dhcpd`重新启动dhcp服务
返回centos-small虚拟机，输入`nmtui`重新激活网卡，发现ip地址变成fixed-address 中指定的192.168.1.188;

> 超级作用域

```
shared-network supper {
  subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.1 192.168.1.101;
  option routers 192.168.1.254;
}

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.100 192.168.2.110;
  option routers 192.168.2.254;
}
```