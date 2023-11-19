# **ZeroTier VPN**

[ZeroTier](https://www.zerotier.com/) 允许通过 NAT 在双方之间安全访问您的 BliKVM。它允许您构建几乎任何类型的现代、安全的多点虚拟化网络。本文提供了一个通过互联网访问您的 BliKVM 的示例，但您也可以使用 Tailscale 或其他 VPN 解决方案。以下是一个基本示例，如需任何特定设置或功能，请参阅[ZeroTier文档](https://docs.zerotier.com/)。

## **在 BliKVM 上安装 ZeroTier**
首先，在 ZeroTier 上准备账户和 VPN 网络，具体操作请参见这里：[创建网络](https://docs.zerotier.com/start)，保存网络 ID 以供以后使用。接下来，使用 SSH 协议连接到 BliKVM 终端，并检查读写权限。如果是只读系统，请使用 `rw` 命令将其设置为可写。
现在使用以下命令安装 ZeroTier 客户端：
```bash
curl -s https://install.zerotier.com | sudo bash
```

!!! warning "请注意，在某些地区，如中国，直接下载 ZeroTier 可能会受到网络限制的影响。请相应配置您的网络。"

## **将 BliKVM 添加到您的 ZeroTier 网络**
在 BliKVM 终端上，使用以下命令将 BliKVM 添加到您的 ZeroTier 网络（使用 ZeroTier 网络 ID，例如 d5e04297a16fa690）：
```
sudo zerotier-cli join d5e04297a16fa690
```
如果一切顺利，您可以在 BliKVM 终端上运行 ip addr show zerotier 网络设备（名称以 zt 开头）以查看 ZeroTier 为虚拟网络分配的 IP 地址。以下是一个示例输出：
```
3: zt6ovrlscs: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 2800 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether d6:e4:eb:ae:db:64 brd ff:ff:ff:ff:ff:ff
    inet 172.25.96.75/16 brd 172.25.255.255 scope global zt6ovrlscs
       valid_lft forever preferred_lft forever
    inet6 fe80::d4e4:ebff:feae:db64/64 scope link 
       valid_lft forever preferred_lft forever
```
IP 地址，例如 172.25.96.75，可用于从主机机器访问 BliKVM Web 界面。

## **在客户计算机上安装 ZeroTier**
转到下载页面，在 ZeroTier 网站上安装 ZeroTier 到控制主机。加入您的 ZeroTier 网络 ID，然后您可以检查您的网络页面，验证两台机器是否在线。检查它们是否被授权连接到网络（Auth? 列）。一旦它们在线，您可以使用以下地址从控制主机机器访问 BliKVM：
```
http://<zerotier_kvm_ip>
```