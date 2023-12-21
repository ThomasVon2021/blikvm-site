# **BliKVM v4 Allwinner**

![](assets/images/v4/BliKVM-v4-front.png){width="300"}
![](assets/images/v4/BliKVM-v4-back.png){width="300"}  
BliKVM v4是一款生产就绪、即插即用的 KVM-over-IP 设备，为专业用户提供了**远程服务器或工作站管理**的便捷解决方案。 它基于Linux并且完全开源。 借助 BliKVM，您可以轻松**打开/关闭电源、重新启动计算机、配置 UEFI/BIOS 设置以及使用模拟大容量存储设备执行操作系统重新安装**。 BliKVM 模拟键盘、鼠标和显示器，所有这些都可以通过 Web 浏览器访问，确保无缝的用户体验。 **其硬件级访问保证独立于特定的远程端口、协议或服务**，使其成为专业人士高度灵活且可靠的远程管理解决方案！

* [BliKVM V4 Datasheet](./Datasheet-BliKVM-v4.md)

??? info "Craft Computing: Goodbye IPMI - Blicube BliKVM V4 测评"
    <iframe src="//player.bilibili.com/player.html?aid=410062899&bvid=BV1cG411k7Cs&cid=1374719019&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

## 功能特点
- **视频捕获** (HDMI,最高支持4K@30Hz输入)
- **键盘转发**
- **鼠标转发**
- **虚拟U盘(重装系统)**
- **HDMI视频环出**
- **ATX** 使用 ATX 功能控制服务器电源
- **全屏模式**
- 通过 **Web UI** 访问
- 支持 **多语言** 切换
- 支持 **PoE & DC**
- 支持 **WiFi**
- **串口** 控制台端口
- 1.33英寸 **彩色** 屏幕
- **实时时钟 (RTC)**  

??? info "HDMI支持的分辨率类型"
    ![](assets/images/v4/v4-hdmi.jpg){width="300"}  

## **安装要求**
!!! note "除v4套件外，您还需自备以下设备"
    * 电源适配器（5V 3A, USB-C端口或12V 2ADC端口）,若你计划使用PoE供电，或者所的被控计算机USB口有充足的供电能力，则也不需要单独的电源适配器；
    * HDMI 线缆(至少一根)，若您同时需要使用HDMI环出接口，则需要2根；
    * 网线（结合您需求自备）,使用ATX开关机功能需一根，使用网线上网功能需一根；
    * USB-C转USB-A线缆一根（用于鼠标和键盘数据传输）.

!!! warning "终端升级注意！"
    在升级前，需执行下面命令，否则apt-get update 和 apt-get upgrade后镜像会无法启动
    ```
    apt-mark hold linux-dtb-edge-sunxi64 linux-image-edge-sunxi64
    ```
!!! info "BliKVM v4 拆箱，连接，使用参考视频"
    <iframe src="//player.bilibili.com/player.html?aid=488438623&bvid=BV1NN41127g9&cid=1195577253&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

## **安装步骤**
**1.** 打开v4套件包装，根据下面所示的连接示意图，将BliKVM和被控计算机连接起来；
![](assets/images/v4/v4-Connection-Diagram.png)

**ATX连接**
请参考[ATX连接指南](./atx.md)。

**2.** 在所有连接线连接好后,对BliKVM进行上电，直到显示屏出现画面，即设备正常启动。

**3.** 仔细阅读[**“第一步”**](./first_steps.md)指南-如何在网络上查找设备、如何登录、更改密码等等。按照上面描述的步骤操作，然后返回本页。

**4.** **尝试使用 Web 界面管理计算机的 BliKVM。** 确保您可以看到图像并且键盘和鼠标都正常工作。如果遇到任何问题，请查看我们的[常见问题](./faq.md)（它非常有用）。如果没有任何帮助，请在我们的[Discord聊天室](https://discord.com/invite/9Y374gUF6C)寻求支持。

**5.** 您可以查看wiki其他的页面，探索BliKVM的更多功能，祝您玩的开心！

## **视频模式**
v4最高支持4K30Hz的视频输入，传输分辨率默认为1920x1080。

## **发货清单**

| BLIKVM v4 Allwinner版本            | 1    |
| -------------------------------------- | ---- |
| BLIKVM v4               | 1    |
| WiFi天线               | 1    |
| ATX适配板               | 1    |
| ATX杜邦线缆 8pin 母对母 60cm | 1    |
| ATX杜邦线缆 8pin 母对公 60cm | 1    |
| 1U安装挂耳             | 2   |
| M2.5x5螺丝               | 8   |
| 硅胶防撞粒              | 1   |

## **通过5V端口访问串行控制台**

5V端口可以同时用于供电和串行控制台访问，默认波特率为115200。BliKVM v4内部有一个基于CH341的USB到UART转换器，它连接到[mCore-H616 SoC](https://linux-sunxi.org/H616)的UART0，所以你可以将PC的USB端口连接到5V端口，无需外部UART和USB-C到杜邦适配器。

!!! warning "PC USB端口电流输出"
    尝试使用5V端口时要小心，因为单独的PC USB端口可能无法提供3A（5V），这是板卡工作的要求。可以同时使用12V 2A DC端口供电和5V端口进行串行通信，无需[USB分线器板](https://wiki.blicube.com/blikvm/en/usb-splitter-guide/)。或者使用分线器板分离出VCC引脚，并使用单独的5V 3A电源为5V端口的VCC引脚供电。同样，当BliKVM通电时从12V 2A DC端口断开电缆时，要确保先从5V端口断开电缆（因为在12V 2A电源断开后，除非使用了分线器，否则5V端口将成为BliKVM v4的电源）。

当你将USB电缆连接到BliKVM v4的5V端口时，你应该在主机内核日志中看到类似这样的内容（如果你使用的是基于Linux的操作系统）:
    ```
    usb 1-1.2: new full-speed USB device number 12 using xhci_hcd
    usb 1-1.2: New USB device found, idVendor=1a86, idProduct=7523, bcdDevice=81.34
    usb 1-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
    usb 1-1.2: Product: USB Serial
    ch341 1-1.2:1.0: ch341-uart converter detected
    usb 1-1.2: ch341-uart converter now attached to ttyUSB0
    ```

然后，可以使用[GNU screen](https://www.gnu.org/software/screen/)或[TIO](https://github.com/tio/tio)访问此端口:
    ```
    tio /dev/ttyUSB0
    mangopimcore login: blikvm
    # ...
    ```

如果你需要检查通过UART0接收了多少数据，可以通过查看通过proc公开的计数器来实现（当从外部主机发送数据时，如果内置的USB到UART转换器工作正常，rx计数器应该会增加）：
    ```
    root@mangopimcore:~# grep '0: uart' /proc/tty/driver/serial
    0: uart:16550A mmio:0x05000000 irq:284 tx:20306 rx:40 pe:1 RTS|DTR
    ```

## **购买链接**
[v4淘宝地址](https://item.taobao.com/item.htm?spm=a1z10.3-c-s.w4002-24390589055.12.25da4adfmEV9JL&id=730202747005)