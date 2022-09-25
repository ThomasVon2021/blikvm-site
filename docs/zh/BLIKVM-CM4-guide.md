# BLIKVM CM4 version 使用说明

!!! info "BLIKVM CM4 360度 视频"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/2av-JFFkF6I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## **安装要求**
!!! note "如果你购买的是需自己组装的版本（不是plug-n-play版本），你需要自己准备以下设备"
    * 树莓派CM4，最小1Gb RAM.
    * MicroSD card (至少16Gb, class 10 recommended).
    * USB-C转USB-A线缆.
    * HDMI线缆.
    * 网线.
    * 电源适配器(5.1V 3A USB-C).

!!! warning "电源适配器"
    在BLIKVM CM4 V2.2版本中，你必须使用USB-C转USB-A线缆进行供电，如果使用USB-C转USB-C线缆可能无法供电。这是这个版本硬件设计的bug，在它后面的版本
    中此问题将会被修复。

## **基础配置**
**1.** [烧录镜像到SD卡或者eMMC](./flashing_os.md) 

**2.组装 BLIKVM** 参考下面的视频和说明进行设备安装:

??? info "完整拆箱和安装视频"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/aehOawHklGE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
??? info "Geerling测试视频"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/3OPd7svT3bE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  
??? info "Ortimo使用BLIKVM CM4 eMMC版本指导"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/xypeC7Fne6Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
**3.** 根据下图接口定义所示，连接被控电脑到BLIKVM上:
![Image title](assets/images/blikcm-cm4-interface.png){width="400"}

* HDMI IN和otg接口必须和被控电脑连接，ATX是可选项。建议在BLIKVM和被控电脑之间最好不要有USB扩展坞，因为在UEFI或BIOS阶段，可能检测不到扩展坞。
BLIKVM CM4版本最高支持1080P60Hz的输入。

* 通过Ethernet将BLIKVM连接到网络，通过PWR IN端口工供电。

## **ATX电源控制连接**
![Image title](assets/images/BLKVM-CM4/ATX-interface.png){width="400"}

为了管理被控计算机的电源，你需要将CN-ATX端口和被控电脑连接。你可以使用提供的ATX线缆(60厘米)或者杜邦线连接到被控电脑的主板上。

![Image title](assets/images/BLKVM-CM4/atx-cable-computer.png){width="400"}

## **硬件参数**
![Image title](assets/images/BLKVM-CM4/blikvm-cm4-hardware-features.png)

* 1、HDMI采集（支持音频）
* 2、ATX控制 (开机/关机，重启,电源和硬盘指示灯)
* 3、USB3.0端口两个
* 4、USB-C OTG接口（用于鼠标和数传控制）
* 5、RTC时钟
* 6、以太网口
* 7、呼吸灯
* 8、SD卡槽
* 9、电源指示灯
* 10、显示屏
* 11、短接烧录镜像接口
* 12、USB-C电源输入接口
* 13、风扇
* 14、CM4模组接口

## ** 支持 1080p60hz HDMI输入**
在V2.2版本中，这里有一个CSI通道切换器。确认切换器在4通道一侧。再其它版本中，移除了此切换器，默认4通道全部使能。

![Image title](assets/images/BLKVM-CM4/kvm-cm4-switch.png){width="400"}
你使用的PiKVM镜像版本不同，当发现不支持1080P60Hz的输入时，请按照下面说明，进行检查和配置
1、 使用下列命令，打开edid文件:
```
rw
vim /etc/kvmd/tc358743-edid.hex
```
删除原文件中的内容，将下列内容写到tc358743-edid.hex文件中.
```
00FFFFFFFFFFFF0031D8888800888888
1C150103800000780AEE91A3544C9926
0F50543FCD0001000101010101010101
010101010101011D007251D01E206E28
5500C48E2100001E8C0AD08A20E02D10
103E9600138E2100001E000000FC0050
694B564D0A20202020202020000000FD
003B3D0F2E0F1E0A202020202020013C
02031E434F041303021211012021A23C
3D3E1F1066030C00300080E2007F8C0A
D08A20E02D10103E9600C48E21000018
8C0AD08A20E02D10103E9600138E2100
00189729A0D051842230509816009A01
11000018000000000000000000000000
00000000000000000000000000000000
0000000000000000000000000000001C
```
2、增加CSI 4通道配置
编辑/boot/config.txt, 找到 "dtoverlay=tc358743" 改为 "dtoverlay=tc358743,4lane=1"
```
vim /boot/config.txt
ro
```
Now,你可以测试1080P60Hz的视频输入了。
