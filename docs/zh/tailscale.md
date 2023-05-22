# **Tailscale VPN**

[Tailscale](https://tailscale.com/)可以用于将您的主机和BliKVM在公网下进行访问。这是一个方便且免费的组网工具，用于组织小型VPN网络。本文档提供了一个示例，用于通过互联网访问您的BliKVM，但您也可以使用Zerotier或者其它VPN。以下是一个基本支持的示例，遇到任何问题可以去Tailscale官网查找。

## **BliKVM安装Tailscale**
首先确认当前系统是读写权限，若是只读系统使用`rw`命令使系统可写，使用下面命令进行[安装](https://tailscale.com/download):
```
curl -fsSL https://tailscale.com/install.sh | sh
```
!!! warning "有一些地区如中国，有可能会因为网络原因无法顺利下载，请正确配置网络"

## **使BliKVM加入到你的Tailscale局域网中**
在官网注册你的tailscale账户，并在设置中生成你自己的keys，在BliKVM终端上，使用下面命令，即可将BliKVM加入到tailscale生成的局域网中。
```
sudo tailscale up --authkey=your-auth-key --accept-routes
```
若一切顺利，你在BliKMV终端运行`ip addr show tailscale0`，即可查看到tailscale0生成的虚拟局域网的ip地址，一个例子如下：
```
3: tailscale0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1280 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/none
    inet 100.126.223.28/32 scope global tailscale0
       valid_lft forever preferred_lft forever
    inet6 fd7a:115c:a1e0:ab12:4843:cd96:627e:df1c/128 scope global
       valid_lft forever preferred_lft forever
    inet6 fe80::8955:99dc:4e7d:b08b/64 scope link stable-privacy
       valid_lft forever preferred_lft forever
```
其中100.126.223.28就是可以用来在主机上访问BliKVM web界面的UI地址。

## **主机安装Tailscale**
将Tailscale[下载](https://tailscale.com/download)并安装到您的控制主机上，登录对应的账户，然后您可以在Tailscale的[控制界面](https://login.tailscale.com/admin/machines)，查看您的两台机器是否都在线，如果都在线，即可使用下面地址，在您的控制主机上访问BliKVM
```
http://<tailscale_kvm_ip>
```

