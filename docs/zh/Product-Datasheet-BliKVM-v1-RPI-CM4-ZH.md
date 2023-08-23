# BliKVM v1 (RPI CM4)

![main](assets/images/BLKVM-CM4/main.png){width="300"}


BliKVM v1是一款基于树莓派CM4的 KVM-over-IP 设备，为专业用户提供了**远程服务器或工作站管理**的便捷解决方案。 它基于Linux并且完全开源。 借助 BliKVM，您可以轻松**打开/关闭电源、重新启动计算机、配置 UEFI/BIOS 设置以及使用模拟大容量存储设备执行操作系统重新安装**。 BliKVM 模拟键盘、鼠标和显示器，所有这些都可以通过 Web 浏览器访问，确保无缝的用户体验。 **其硬件级访问保证独立于特定的远程端口、协议或服务**，使其成为专业人士高度灵活且可靠的远程管理解决方案！

## 接口定义

![Interface-Layout-Diagram](assets/images/BLKVM-CM4/Interface-Layout-Diagram.png)

| 1 | OTG 端口    | 7   | Micro SD 卡槽 |
| ----- | ------------------------------- | ---- | ----------------------------- |
| 2     | USB3.0 x2 | 8  | 状态指示灯 (绿色) |
| 3     | ATX 控制端口       | 9  | 网口 1000M |
| 4     | HDMI 视频输入端口 | 10  | OLED 显示屏 128x64 |
| 5     | Type-C供电端口 5V3A | 11  | 天线安装孔 |
| 6     | 电源指示灯 (红色) |      |                       |

## 参数

![Topology-Diagram](assets/images/BLKVM-CM4/Topology-Diagram.png)

| 参数名称         | 描述                                      |
| ---------------- | ----------------------------------------- |
| **供电**         |                                           |
| 5V 3A            | PWR IN 端口                               |
|                  |                                           |
| **端口**         |                                           |
| HDMI IN          | HDMI 视频输入端口                         |
| OTG              | 模拟键盘，鼠标，大容量存储器或其他USB设备 |
| CN-ATX           | 开关机被控电脑，读取被控电脑状态指示灯    |
| Micro SD 卡槽    | 安装镜像内存卡                            |
| PWR IN 端口      | 5V3A 电源                                 |
|                  |                                           |
| **显示和指示灯** |                                           |
| LED 指示灯       | 电源指示灯（红色），状态指示灯（绿色）    |
| OLED 显示屏      | OLED 128x64 0.96寸                        |
|                  |                                           |
| **视频**         |                                           |
| 分辨率           | 最高支持 1920x1200@60Hz                   |
| 编码格式         | H.264, MJPEG                              |
|                  |                                           |
| **核心**         |                                           |
| 模块             | 树莓派CM4（自备）                         |
|                  |                                           |
| **功耗**         | Up to 15W                                 |
|                  |                                           |
| **环境参数**     |                                           |
| 工作温度         | 0°C to 70°C                               |
| 存储温度         | -20°C to 60°C                             |
|                  |                                           |
| **尺寸和重量**   |                                           |
| 尺寸             | 120(L) x 70W) x 37(H) mm                  |
| 重量             | 0.45 kg                                   |

## 外形尺寸

![Dimensions](assets/images/BLKVM-CM4/Dimensions.png)
