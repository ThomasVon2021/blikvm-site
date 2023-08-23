# BLIKVM v1 CM4使用说明

!!! info "BLIKVM CM4 v1评测视频"
    <iframe src="//player.bilibili.com/player.html?aid=896215077&bvid=BV1GA4y1Q7PK&cid=589734284&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

BliKVM v1是一款生产就绪、即插即用的 KVM-over-IP 设备，为专业用户提供了远程服务器或工作站管理的便捷解决方案。 它基于Linux并且完全开源。 借助 BliKVM，您可以轻松打开/关闭电源、重新启动计算机、配置 UEFI/BIOS 设置以及使用模拟大容量存储设备执行操作系统重新安装。 BliKVM 模拟键盘、鼠标和显示器，所有这些都可以通过 Web 浏览器访问，确保无缝的用户体验。 其硬件级访问保证独立于特定的远程端口、协议或服务，使其成为专业人士高度灵活且可靠的远程管理解决方案！

* [BliKVM v1 Datasheet](./Product-Datasheet-BliKVM-v1-RPI-CM4-ZH.md)

## 功能特点
- **视频捕获** (HDMI,最高支持1080P@60Hz输入)
- **键盘转发**
- **鼠标转发**
- **虚拟U盘(重装系统)**
- **ATX** 使用 ATX 功能控制服务器电源
- **全屏模式**
- 通过 **Web UI** 访问
- 支持 **多语言** 切换
- 支持 **WiFi**（可选）
- **OLED** 屏幕
- **实时时钟 (RTC)**  

## **安装要求**
!!! note "如果你购买的是需自己组装的版本（不是plug-n-play版本），你需要自己准备以下设备"
    * 树莓派CM4，最小1Gb RAM.
    * USB-C转USB-A线缆.
    * HDMI线缆.
    * 网线.
    * 电源适配器(5.1V 3A USB-C).

!!! warning "电源适配器"
    在BLIKVM CM4 V2.2版本中，你必须使用USB-C转USB-A线缆进行供电，如果使用USB-C转USB-C线缆可能无法供电。这是这个版本硬件设计的bug，在它后面的版本
    中此问题将会被修复。

## **基础配置**
**1.** 出厂默认配的SD卡已烧录镜像，无需烧录。若您需要重刷系统或者DIY，可参考[烧录镜像到SD卡或者eMMC](./flashing_os.md) 

**2.** 如果您不是plug版本,参考下面的视频和说明进行设备安装:  
1. 用包裹配的螺丝刀打开金属外壳，拆下PCB主板；  
2. 将CM4安装在PCB主板上，注意安装CM4时两排卡槽要对齐，然后将硅胶导热片贴在CM4主芯片上，从而可以使CM4利用金属外壳散热；  
3. 风扇默认不接，外壳散热足够，根据您的CM4版本选择性安装Wi-Fi天线;  
4. 重新安装好PCB主板和金属外壳，即安装完成.  

??? info "完整拆箱和安装视频"
    <iframe src="//player.bilibili.com/player.html?aid=979782888&bvid=BV1944y1K7P3&cid=550216248&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
??? info "Ortimo使用BLIKVM CM4 eMMC版本指导"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/xypeC7Fne6Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**3.** 根据下图接口定义所示，连接被控电脑到BLIKVM上:
![Image title](assets/images/blikcm-cm4-interface.png){width="400"}

* HDMI IN和otg接口必须和被控电脑连接，ATX是可选项。建议在BLIKVM和被控电脑之间最好不要有USB扩展坞，因为在UEFI或BIOS阶段，可能检测不到扩展坞。
BLIKVM CM4版本最高支持1080P60Hz的输入。

* 通过Ethernet将BLIKVM连接到网络，通过PWR IN端口工供电。

**4.** **ATX电源控制连接**
![Image title](assets/images/BLKVM-CM4/ATX-interface.png){width="400"}

为了管理被控计算机的电源，你需要将CN-ATX端口和被控电脑连接。你可以使用提供的ATX线缆(60厘米)或者杜邦线连接到被控电脑的主板上。

![Image title](assets/images/BLKVM-CM4/atx-cable-computer.png){width="400"}

!!! warning "为了兼容网口形式的ATX控制板，v1有专门的ATX扩展包，方便客户直接通过网线和安装到机箱挡板的ATX板连接。"
    ![Image title](assets/images/BLKVM-CM4/v1-atx01.jpg){width="300"}
    ![Image title](assets/images/BLKVM-CM4/v1-atx02.jpg){width="300"}
    ![Image title](assets/images/BLKVM-CM4/v1-atx03.jpg){width="300"}

**5.** 在所有连接线连接好后,对BliKVM进行上电，直到显示屏出现画面，即设备正常启动。

**6.** 仔细阅读[**“第一步”**](./first_steps.md)指南-如何在网络上查找设备、如何登录、更改密码等等。按照上面描述的步骤操作，然后返回本页。
!!! warning "由于BliKVM v1也支持PiKVM OS，若你手上的v1出厂OS为PiKVM，关于web使用说明请[参考文档](https://docs.pikvm.org/)。"

**7.** **尝试使用 Web 界面管理计算机的 BliKVM。** 确保您可以看到图像并且键盘和鼠标都正常工作。如果遇到任何问题，请查看我们的[常见问题](./faq.md)（它非常有用）。如果没有任何帮助，请在我们的[Discord聊天室](https://discord.com/invite/9Y374gUF6C)寻求支持。

**8.** 您可以查看wiki其他的页面，探索BliKVM的更多功能，祝您玩的开心！

## **Wi-Fi天线连接**
!!! info "如你的CM4有Wi-Fi功能，拆开v1的金属盒子，请将包裹中的Wi-Fi天线，安装到CM4的IPX接口，即下图中红框的接口；其中外壳安装天线位置为接口定义图中的11处。"
    ![Image title](assets/images/BLKVM-CM4/v1-wifi-interface.png){width="300"}
    ![Image title](assets/images/BLKVM-CM4/Interface-Layout-Diagram.png)

## ** 支持 1080p60hz HDMI输入**
在V2.2版本中，这里有一个CSI通道切换器。确认切换器在4通道一侧。再其它版本中，移除了此切换器，默认4通道全部使能。  
![Image title](assets/images/BLKVM-CM4/kvm-cm4-switch.png){width="400"}

## **购买链接**
[v1淘宝地址](https://item.taobao.com/item.htm?spm=a1z10.3-c-s.w4002-24390589055.20.cdbf4adf27a7N9&id=668763563893)
