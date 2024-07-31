---
title: 在Ubuntu上使用clash设置透明代理
date: 2024-07-31 23:59:12 +0800
tags: [linux,clash,网络]
---

在这之前我一般都是启动一个服务，然后监听7890端口，局域网内的PC设置一下http代理即可使用，但是最近总发现设置代理之后国内的一些网站打开都变慢了，一点受不了，就找到了一个解决方案。

## Ubuntu配置

### 允许ip转发

```
sudo vim /etc/sysctl.conf
```

找到 `net.ipv4.ip_forward=1` 这一行，取消掉注释。如果没有找到的话直接新增一行也可以的。随后执行

```
sudo sysctl -p
```

使修改生效。

### 配置iptables

依次执行下面的指令，注意注释的部分，修改成自己的网络配置

```
iptables -t nat -N clash
iptables -t nat -N clash_dns

# 这个是fake-ip对应的dns地址，一般不用动
iptables -t nat -A PREROUTING -p tcp --dport 53 -d 198.19.0.0/24 -j clash_dns
iptables -t nat -A PREROUTING -p udp --dport 53 -d 198.19.0.0/24 -j clash_dns
iptables -t nat -A PREROUTING -p tcp -j clash

# 这里需要注意的是，下面两行最后的 192.168.1.21 是当前旁路由的 IP 地址，请根据你自己的实际情况修改
# 如果你自己的旁路由 IP 跟下面的 IP 地址不对的话会造成无法翻墙
iptables -t nat -A clash_dns -p udp --dport 53 -d 198.19.0.0/24 -j DNAT --to-destination 192.168.1.21:53
iptables -t nat -A clash_dns -p tcp --dport 53 -d 198.19.0.0/24 -j DNAT --to-destination 192.168.1.21:53

# 绕过一些内网地址
iptables -t nat -A clash -d 0.0.0.0/8 -j RETURN
iptables -t nat -A clash -d 10.0.0.0/8 -j RETURN
iptables -t nat -A clash -d 127.0.0.0/8 -j RETURN
iptables -t nat -A clash -d 169.254.0.0/16 -j RETURN
iptables -t nat -A clash -d 172.16.0.0/12 -j RETURN
iptables -t nat -A clash -d 192.168.0.0/16 -j RETURN
iptables -t nat -A clash -d 224.0.0.0/4 -j RETURN
iptables -t nat -A clash -d 240.0.0.0/4 -j RETURN

# 注意, 这边的7892对应后续clash配置里的redir-port
iptables -t nat -A clash -p tcp -j REDIRECT --to-ports 7892
```

执行完上面的 iptables 命令之后，就完成了旁路由的路由功能了，但是此时 iptables 并没有永久保存，下次开机上面的配置就会丢失。为了使得重启之后 iptables 命令仍然存在，我们需要安装软件来实现：

```
sudo apt install iptables-persistent
```

安装的过程中会提示你是否需要保存 iptables 配置，直接选是就行。这时候即使电脑重启了也会应用这些路由规则。

如果后面你有需要重新修改 iptables 的配置，那么只需要在执行完 iptables 之后再执行：

```
sudo iptables-save > /etc/iptables/rules.v4
```

即可将最新的 iptables 规则保存下来。

## 修改客户端的旁路由配置

不论是什么系统，若要使用旁路由作为网关，只要修改以下项目：

- 手动配置IP地址（关闭DHCP），主机的IP地址可以是照抄DHCP分配给你的那个，或者在同一网段里自选一个不冲突的，按文中例子是`192.168.1.X`其中X!=1 && X!=21；
- 子网掩码`255.255.255.0`；
- 网关地址`192.168.1.21`，也就是虚拟机旁路由的IP地址；
- DNS配置`198.19.0.1`，如果要填次要DNS，可以填`198.19.0.2`；

我把华为路由器接在了光猫的另一个LAN口（和旁路由平级），这边给一个华为路由器上的参考配置：

![1453701194](https://cdn.jsdelivr.net/gh/MasterKe2003/my_blog_picture/2024%2F07%2F31%2F1722438171.jpg)

[原文地址]: https://unique-ptr.com/archives/117	"(使用VirtualBox)构建Ubuntu下的clash旁路由服务"