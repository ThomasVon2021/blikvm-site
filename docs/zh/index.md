# BLIKVM Overview
BLIKVM是一款开源软件的KVM专业设备，目前有3个版本，CM4 Board, Raspberry HAT, PCIe Board。该设备在于帮助用户通过得到控制设备的HDMI
画面和鼠标键盘，去远程管理服务器、工作站或个人PC等。 无论目标设备的操作系统是否能正常运行，你可以通过BLIKVM解决目标设备的一切问题，
如：配置BIOS系统，通过使用远程CD-ROM或者闪存驱动器给目标设备重新安装操作系统。在这里你可以找到关于BLIKVM所有的使用文档。欢迎加入BLIKVM的
[Discord](https://discord.com/invite/9Y374gUF6C) 群组和来自全世界的爱好者和用户进行交流，获得技术支持，常见问题解答和新闻等。
![Image title](assets/images/version_all.png)

|FEATURE NAME|BliKVM CM4|BliKVM Pi4 HAT|BliKVM PCIe|BliKVM PCIe(PA)|PiKVM V3 HAT|PiKVM V3 HAT (PA)|TinyPilot Voyager 2|
|-|-|-|-|-|-|-|-|
|Cost (without tax + shipping)|67$|95$|111$|206$|160$|250$|400$|
|Serial Console|No|Yes|Yes|Yes|Yes|Yes|No|
|ATX controls|Yes|Yes|Yes|Yes|Yes|Yes|No|
|FAN PWM controls|No|Yes|Yes|Yes|Yes|Yes|No|
|OLED|128x64|128x32|128x64|128x64|128x32|128x32|No|
|POE|No|Yes|Yes|Yes|No, but you can use poe splitter|No, but you can use poe splitter|No (optional $59)|
|Real Time Clock (pcf8563)|ds1307|Yes|Yes|Yes|Yes|Yes|No|
|USB Power/Data Splitter|Yes(built-in)|Yes (external)|Yes(built-in)|Yes(built-in)|Yes(built-in)|Yes(built-in)|Yes(built-in)|
|TC358743 CSI Video capture|Yes|Yes|Yes|Yes|Yes|Yes| Yes|
|Case|Yes (steel - black)|Yes (steel - blue and black)|No|No|No|Yes (steel - black)|Yes (3d print black)|
|Dedicated software devs|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
|Dedicated support|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
|Pi4 or CM4 2GB Included|No|No|No|Yes|No|Yes|Yes|
|32GB SD Card|No|Yes (OS included)|Yes (OS included)|Yes (OS included)|No|Yes (OS included)|Yes (OS included)|
|HDMI backpower mitigation|No|Yes|Yes|Yes|Yes|Yes|No|
|HDMI Passthru EDID dongle|No|Yes|Yes|Yes|No|No|No|

## **功能**
* HDMI视频采集 (最高支持1080P 60Hz)  
* 键盘转发  
* 鼠标转发
* ATX开关机  
* PWM风扇控制 
* 全屏模式  
* 从剪贴板粘贴文本 
* VPN组网支持 
* 大容量存储驱动器 (模拟CD-ROM或闪存驱动器)  
* 远程控制多台主机（通过搭配KVM切换器）
* OLED屏幕显示系统信息（温度、IP地址，运行时间等）
* 账号密码认证

## **Guide**
[1.BliKVM v1 CM4 版本 ](./BLIKVM-CM4-guide.md) 
[2.BliKVM v2 PCIe 版本 ](./BLIKVM-PCIE-guide-zh.md)  
[3.BliKVM v3 HAT 版本 ](./BLIKVM-HAT-guide.md)  
[4.BliKVM v4 版本 ](./BliKVM-v4-guide.md)   
  

