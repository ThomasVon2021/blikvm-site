# BliKVM Hat 使用说明
## **介绍**

!!! info "BliKVM Hat 360度 视频"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/SdpmMojDbGA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
BliKVM Hat版本是基于树莓派4B制作的一款硬件，用于KVM Over IP。Hat关键功能包括HDMI视频捕获、ATX控制、PoE供电、OLED屏幕显示、RTC时钟。
Hat配有金属外壳，用于保护和散热。Hat可以被安装到1U的机架。同时支持blikvm镜像和pikvm镜像。

 ![Image title](assets/images/BLIKVM-HAT/case.png){width="300"}  
## **安装要求**
!!! note "如果你购买的只是一个Hat，你还需要下面设备"
    * 树莓派4B，1GB RAM或者更多
    * MicroSD card (推荐最少16Gb, class 10).
    * HDMI 线缆.
    * 网线 (用于Hat和ATX的连接).
    * 电源适配器和线缆(5.1V 3A USB-C).


## 功能
- **视频捕获** (HDMI,最高支持1080P@50Hz输入)
- **键盘转发**
- **鼠标转发**
- **虚拟U盘(重装系统)**
- **ATX** 使用 ATX 功能控制服务器电源
- **全屏模式**
- 通过 **Web UI** 访问
- 支持 **多语言** 切换
- 支持**PoE**供电
- 支持串口终端
- **OLED** 屏幕
- **实时时钟 (RTC)**  
- PWM风扇


## **基础设置**
**1.** [烧录镜像](./flashing_os.md) 

**2.组装Hat** 参考下面的视频说明或者参考[图文说明](./BLIHAT-Installation.md):

??? info "Hat 视频安装导览: 手把手教你如何组装Hat到树莓派上"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/FaZBQUA7rAM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**3.** 安装**ATX**模块

!!! info "ATX模块配有一个全高或者半高的PCIe挡板，你可以根据需求选择安装"
    ![IMG_8366](assets/images/BLIKVM-HAT/hat-install/IMG_8366.JPG){width="300"}
    ![IMG_8367](assets/images/BLIKVM-HAT/hat-install/IMG_8367.JPG){width="300"}

!!! info "使用杜邦线连接ATX模块和机箱里的主板，ATX模块上都有清晰的引脚定义方便你连接"
    ![IMG_8368](assets/images/BLIKVM-HAT/hat-install/IMG_8368.JPG){width="300"}
    ![IMG_8369](assets/images/BLIKVM-HAT/hat-install/IMG_8369.JPG){width="300"}

!!! info "将ATX模块安装到机箱外壳上"
    ![IMG_8370](assets/images/BLIKVM-HAT/hat-install/IMG_8370.JPG){width="300"}

!!! info "使用RJ45的网线连接ATX和Hat"
    ![004d8da8059a57b87d2d40ce70174e7](assets/images/BLIKVM-HAT/hat-install/004d8da8059a57b87d2d40ce70174e7.png){width="300"}

**4.** 连接HDMI线缆

!!! info "使用HDMI线缆，将被控电脑的HDMI和Hat的HDMI IN端口连接。HDMI模拟器不是必须使用的，当你的电脑不能正确输出画面时，可以尝试使用HDMI模拟器来校正电脑的HDMI输出"
    ![30c484ad28e149b703ccc74c09e52db](assets/images/BLIKVM-HAT/hat-install/30c484ad28e149b703ccc74c09e52db.png){width="300"}
    ![IMG_8373](assets/images/BLIKVM-HAT/hat-install/IMG_8373.JPG){width="300"}

**5.** 安装USB线缆
!!! info "请注意这里使用USB分电板不是必须的，如果你使用PoE供电不需要使用此模块，如果你需要使用USB供电则需要。通过USB-C线连接树莓派4B的TYPE-C口到分电板的RPI4端口"
    ![IMG_8374](assets/images/BLIKVM-HAT/hat-install/IMG_8374.JPG){width="300"}
    ![IMG_8375](assets/images/BLIKVM-HAT/hat-install/IMG_8375.JPG){width="300"}

!!! info "连接分电板上的USB端口到被控电脑"
    ![IMG_8376](assets/images/BLIKVM-HAT/hat-install/IMG_8376.JPG){width="300"}

!!! warning "当使用PoE供电时，请注意不需要在使用USB供电设备。当不使用PoE供电时，推荐使用5V/3A的电源适配器到分电板的PWR端口"

**6.** 测试
!!! info "图中通过PoE供电，Hat通过网线连接到网络中"
    ![IMG_8377](assets/images/BLIKVM-HAT/hat-install/IMG_8377.JPG){width="300"}

!!! info "OLED屏幕将会正常显示设备的工作状态，包括设备的IP地址"
    ![IMG_8379](assets/images/BLIKVM-HAT/hat-install/IMG_8379.JPG){width="300"}

!!! info "打开浏览器，输入设备的IP地址，即可打开控制的WEB界面，现在去使用它吧！"
    ![image-20220621174207504](assets/images/BLIKVM-HAT/hat-install/image-20220621174207504.png){width="300"}

## **性能参数**
![Image title](assets/images/BLIKVM-HAT/specification.png){width="600"}

??? note "**HDMI 输入**"
    使用Toshiba TC358743为HDMI转换的主芯片，同时支持视频和声音的采集，支持视频最高输入为1080P60Hz.解决了HDMI反向供电问题。

??? note "**CN-ATX**"
    CN-ATX接口通过网线连接ATX模块，用来控制被控电脑的开机、关机、和重启操作。

??? note "**显示屏**"
    配有白色的显示屏，分辨率为128x32，使用芯片为SSD1306。显示屏会显示如温度、IP地址等树莓派的信息。

??? note "**PoE**"
    - **标准:** IEEE 802.3af PoE
    - **输入电压:** 37-57 V DC
    - **输出电压:** 5 V DC/2.4 A
    - 使用PoE模块供电，需要将Hat上的PoE的引脚使用跳线帽短接。

??? note "**风扇**"
    风扇默认使用树莓派上的GPIO12控制。

??? note "**RTC时钟**"
    RTC时钟主芯片为PCF8563，通过I2C和树莓派连接。启用RTC时钟工作的纽扣电池安装位置在HDMI-IN模块的下面。

## **配件**

### **ATX模块**

![Image title](assets/images/BLIKVM-HAT/ATX-A-B.png){width="300"}

ATX模块通过杜邦线和电脑的主板连接。ATX模块配有全高和半高的PCIe挡板。

### **USB/PWR 分电板**
![Image title](assets/images/BLIKVM-HAT/usb-spiltter.png){width="300"}

- RPI4端口用于连接到树莓派4B.
- USB端口用于连接到被控电脑.
- 当使用PoE供电时，不需要使用分电板.

### **HDMI模拟器**

![Image title](assets/images/BLIKVM-HAT/edid-emulator.png){width="300"}

如果被控电脑不能正确输出画面，可以尝试使用此模块来解决。将此模块连接到Hat上后，再通过HDMI线缆连接到被控电脑。

### **金属外壳**

![Image title](assets/images/BLIKVM-HAT/metal-case.png){width="300"}  

金属外壳可以保护Hat和用于散热.外壳上每个端口有清晰的丝印来表示此端口用途。此外壳可以方便的安装在1U的机架上。


## **List**

### **Product List**
![Image title](assets/images/BLIKVM-HAT/product-list.png){width="300"}

| BliKVM Hat 模块                   | 1    |
|---------------------------------| ---- |
| ATX 模块                          | 1    |
| USB/PWR 分电板                     | 1    |
| HDMI模拟器                         | 1    |
| 金属外壳                            | 1    |
| 32G TF 卡                        | 1    |
| USB Type-C 转 USB Type-C 线缆 30cm | 1    |
| 杜邦线 8pin 母对母 40cm               | 1    |
| 杜邦线 8pin 母对公 40cm               | 1    |
| 十字螺丝刀                           | 1    |
| 十字扳手套筒                          | 1    |

### **用户需要准备设备的清单**

| 树莓派4B                      | 1    |
|----------------------------| ---- |
| RJ45 网线                    | 2    |
| USB Type-A 转 USB Type-C 线缆 | 2    |
| HDMI 线缆                    | 1    |
| PoE供电设备 or 5V/3A USB 电源适配器 | 1    |
| CR1220纽扣电池                 | 1    |
