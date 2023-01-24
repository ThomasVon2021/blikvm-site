# BLIKVM PCIe

## **介绍**

![main1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_main1.png){width="500"}
BLIKVM PCIe是一款基于树莓派CM4的IPKVM扩展卡，可以安装到PC或者服务器的PCIe插槽，完美运行PiKVM项目。主要功能有：HDMI视频采集，键盘鼠标控制，ATX开关机控制，PoE供电，OLED屏幕显示，
串口终端调试和RTC时钟功能。此PCIe卡配有全高和半高的挡板。 BLIKVM PCIe版本支持blikvm和pikvm的系统镜像。

## **安装要求**
!!! note "你需要下面的设备"
    * 树莓派CM4(如果你只订购了PCIe卡).
    * PoE供电设备或5V/3A USB供电设备.
    * CR1220 纽扣电池.

## **快速安装说明**
**1.** [如果你购买的是需要自己组装的版本，烧录系统镜像参考请点击此处 ](./flashing_os.md)   
**2.组装 BLIKVM** 参考的 [说明文档](./BLIKVM-PCIe-installation-zh.md)
??? info "Geerling的测试视频"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/cVWF3u-y-Zg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    
??? info "Craft Computing: Never Pay For IPMI Again - BliKVM Review"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/Wn5UXY4W6E0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## **产品特性**
!!! note "硬件接口清单"
    ![BLIKVM_PCIe_main-define](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_main-define.png){width="300"}
    ![BLIKVM_PCIe_main-back](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_main-back.png){width="300"}

!!! note "**HDMI IN**"
    使用东芝的TC358743作为HDMI的桥接芯片，同时支持视频和音频采集，支持视频输入最高分辨率为1080P60Hz。

!!! note "**USB-PC**"
    BLIKVM PCIe卡提供了2个USB的接口，用户可以根据自己需要选择。

!!! note "**POWER-IN**"
    当使用PoE供电时，改接口不需要被使用。当不使用PoE供电时，连接该接口的电源适配器，推荐为5V/3A。

!!! note "**以太网口-PoE**"
    - Gigabit Ethernet port
    - **标准:** IEEE 802.3af PoE
    - **输入电压:** 37-57 V DC
    - **输出电压:** 5 V DC/2.4 A

!!! note "**ATX接口**"
    改接口通过杜邦线链接被控计算机主板的电源控制接口。ATX功能可以开启或者重启被控计算机。
    
!!! note "**OLED显示屏**"
    显示屏分辨率为128x64，主芯片为SSD1306。通过改屏幕可以展示BLIKVM的CPU的温度、IP地址、启动时间等信息。

!!! note "**风扇**"
    风扇默认设置工作温度为60摄氏度，与树莓派CM4的通过GPIO12链接。

!!! note "**BOOT**"
    Fit jumper to disable eMMC Boot
    通过该短接口可以使用PCIe卡对eMMC版本的CM4进行镜像烧录。

!!! note "**实时时钟 (RTC)**"
    时钟芯片为PCF8563，与树莓派CM4的通信方式为I2C。RTC工作需要再安装CR1220电池后。

!!! note "**串口**"
    Connect the serial port to debug your Raspberry Pi CM4.
    可以通过改串口登陆设备进行调试，一般在在网络链接故障等情况下使用。

## **配件**

![BLIKVM_PCIe_main-back](assets/images/BLIKVM-PCIe/accessories.png){width="400"}
!!! note "**HDMI EDID模拟器**"
    如果被控计算机不能正确的输出HDMI图像，可以使用此设备进行测试。安装在被控设备的HDMI输出接口上，然后再通过HDMI线连接到BLIKVM。

!!! note "**VGA转HDMI模块**"
    当被控计算机不是HDMI输出接口，而是VGA输出接口，请使用该模块完成VGA转HDMI信号转换。

!!! note "**USB转TTL模块**"
    Connect your computer usb interface with the serial port of BLIKVM to debug your Raspberry Pi CM4.
    通过改模块，可以连接BLIKVM PCIe卡的串口，然后使用串口进入设备进行调试。

!!! note "**风扇**"
    Use a cooling fan to cool the Raspberry Pi CM4, but installing a fan will make the product thicker than a standard
    PCIe add-in card.
    使用风扇对树莓派CM4进行降温，但安装风扇后会使BLIKVM PCIe卡的厚度厚于标准的PCIe卡厚度。

## **尺寸**

![dimension1](assets/images/BLIKVM-PCIe/dimension.png){width="400"}

## **测试视频 **
??? info "BLIKVM PCIe版本实测视频，软件使用PiKVM"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/0SEGeLFV-Wk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## **发货清单**

| BLIKVM only PCIe卡版本 | 1    |
|---------------------| ---- |
| BLIKVM PCIe卡        | 1    |
| 风扇                  | 1    |
| OLED显示屏             | 1    |
| USB转TTL模块           | 1    |
| HDMI EDID模拟器        | 1    |
| VGA转HDMI模块          | 1    |
| 32G Micro SD card   | 1    |
| HDMI线 0.5m          | 1    |
| HDMI 直通头            | 1    |
| 千兆网线 1m             | 1    |
| USB-A转USB-C线 1m     | 2    |
| USB杜邦线 0.4m         | 1    |
| WiFi天线              | 1    |
| 杜邦线 8pin 母对母 40cm   | 1    |
| 杜邦线 8pin 母对公 40cm   | 1    |
| 金属散热片               | 1    |
| 十字套筒                | 1    |
| 十字螺丝刀               | 1    |

| BLIKVM PCIe 到手即用版本 | 1    |
|--------------------| ---- |
| BLIKVM PCIe卡       | 1    |
| CM4 102000         | 1    |
| 风扇                 | 1    |
| OLED显示屏            | 1    |
| USB转TTL模块          | 1    |
| HDMI EDID模拟器       | 1    |
| VGA转HDMI模块         | 1    |
| 32G Micro SD card  | 1    |
| HDMI线 0.5m         | 1    |
| HDMI 直通头           | 1    |
| 千兆网线 1m            | 1    |
| USB-A转USB-C线 1m    | 2    |
| USB杜邦线 0.4m        | 1    |
| WiFi天线             | 1    |
| 杜邦线 8pin 母对母 40cm  | 1    |
| 杜邦线 8pin 母对公 40cm  | 1    |
| 金属散热片              | 1    |
| 十字套筒               | 1    |
| 十字螺丝刀              | 1    |
备注：由于树莓派CM4一直紧缺，到手即用版本中CM4版本可能会更换为eMMC版本，此中情况下将不带SD卡。