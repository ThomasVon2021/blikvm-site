# 初步操作

## 首次上电

??? example "可选：设置Wi-Fi连接"
    !!! warning "请阅读以下注意事项" 
        1. 有线以太网连接是最可靠的方式，因此最好使用**有线电缆**。但我们不能阻止您使用无线连接... :)
        2. 确认您使用的版本含有Wi-Fi功能，并且Wi-Fi天线已安装.
    请参考[Wi-Fi连接指南](./wifi.md)，对您的设备进行Wi-Fi设置；
    
**给设备供电。**

!!! warning "在设备完全启动前，请勿关闭电源"


## 访问BliKVM

默认情况下，BliKVM通过DHCP接收动态IP地址。会在BliKVM显示器上显示IP地址。如果您是DIY硬件没有显示器，请使用以下提示：

??? example "在网络中查找BliKVM"
    您可以使用以下方法确定BliKVM的IP地址：

    * **常用方法：** 打开路由器的Web界面，并查找已分配的IP地址列表。具体方法取决于路由器型号。
    * **仅限Linux：** 使用命令 `arp-scan --localnet`。
    * **Linux、MacOS、Windows：** 下载并运行 [Angry IP Scanner](https://angryip.org)。
    * **Windows PowerShell：** 使用命令 `arp -a`。

在下面的示例中，让我们假设您的BliKVM已获得地址 **192.168.0.100**，您已经成功使用上述指示找到了该地址。

??? example "访问BliKVM Web界面"
    在*大多数*网络中，您可以在任何浏览器中使用以下URL访问BliKVM：`http://192.168.0.100/`。Google Chrome（Chromium）、Firefox和Safari与启用0个扩展的情况下效果最佳，如果其中一个可以正常工作而另一个无法正常工作，则可能是浏览器/扩展的问题。建议您使用私密浏览窗口或无痕模式。不支持Internet Explorer和早期版本的Microsoft Edge（非Chromium版本）。

    **默认用户名为 `admin`，密码也为 `admin`。** 登录后，您将获得访问主要功能菜单的权限。使用Web的修改账号密码功能，您可以更改系统设置和密码。

!!! warning "注意当前访问BliKVM web是http，而非https"

??? example "通过SSH访问BliKVM"
    SSH是Linux世界中最常用的远程访问方法。您可以通过SSH访问BliKVM。此方法用于管理设备：

    * **Linux、MacOS：** 打开任何终端应用程序，然后运行：`ssh blikvm@192.168.0.100`。
    * **Windows：** 使用 [PuTTY](https://www.putty.org/) 进行操作。

    **默认的 `blikvm` 用户密码为 `blikvm`。**
    您可以使用`sudo -i`获得root权限。

??? example "可选：更新BliKVM软件"
    这部分不是必需的，仅在您在BliKVM旁边以便恢复它时才应执行，可以参考[更新软件指南](./update.md)完成；


## BliKVM OS终端使用注意事项

一些配置更改都必须在 `root` 用户（即管理员）下进行。

!!! tip "获取root权限"
    * 如果您通过SSH登录，需使用`sudo -i`获得root权限；

v1、v2、v3版本的BliKVM存储卡以只读模式挂载。这样可以在突然停电时保护文件系统免受损坏。要编辑任何文件并进行更改，需要将文件系统重新挂载为读写模式。您可以通过终端是有有ro或rw字样来判断当前系统模式。

!!! tip "启用写入模式"
    * 要启用写入模式，请运行 `rw` 命令。
    * 要禁用写入模式，请运行 `ro` 命令。
    * 如果收到 "Device is busy"（设备忙）的消息，请执行 `reboot` 命令。

-----
## 下一步是什么？
* 使用 [端口转发](./port_forwarding.md) 或 [Tailscale VPN](./tailscale.md) 设置互联网访问。
* 使用左侧的目录导航探索BliKVM的功能。
* 加入我们的 [Discord](https://discord.com/invite/9Y374gUF6C) 与社区和开发人员交流。
* 查看 [GitHub](https://github.com/ThomasVon2021/blikvm) - BliKVM 是一个开源的项目！


-----
## 常见问题和故障排除
如果您有任何问题或遇到问题，请查看 [常见问题](./faq.md)。
真的，它非常有用！我们可能已经为您找到解决方案了 :)

如果需要任何其他帮助和支持，您可以通过 [Discord聊天](https://discord.com/invite/9Y374gUF6C) 与我们联系。
