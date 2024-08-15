# BLIKVM Overview

BLIKVM is an open-source KVM, it has four versions: v1 CM4, v2 PCIe, v3 HAT and the v4 Allwinner.
This device helps to manage servers or workstations remotely, regardless of the health of the operating system or whether one is installed. You can fix any problem, configure the BIOS, and even reinstall the OS using the virtual CD-ROM or Flash Drive. Unlike software-based remote management, you don't need to install any software on the controlled computer, providing non-intrusive control. Here you will find comprehensive information about all aspects of the operation of BLIKVM.

Join our [BLIKVM Discord Community](https://discord.com/invite/9Y374gUF6C) for Support, FAQ & News!

![Image title](assets/images/version_all.png)

|FEATURE|BliKVM v1 CM4|BliKVM v2 PCIe|BliKVM v3 HAT|BliKVM v4 /H313|
|-|-|-|-|-|
|SOC|Raspberry CM4|Raspberry CM4|Raspberry 4B|Allwinner H616/H313|
|Supported resolutions|1920x1080@60Hz|1920x1080@60Hz|1920x1080@50Hz|3840x2160@30Hz|
|HDMI Capture|TC358743|TC358743|TC358743|MS2131|
|HDMI Loop Through|No|No|No|Yes|
|POE|No|Yes|Yes|Yes|
|DC-IN|No|No|No|Yes|
|USB-C Power|Yes|Yes|Yes|Yes|
|USB Power/Data Splitter|Yes|Yes(external)|Yes|Yes|
|Serial Console|No|Yes|Yes|Yes|
|ATX controls|Yes|Yes|Yes|Yes|
|BIOS controls|Yes|Yes|Yes|Yes|
|Open source system|Yes|Yes|Yes|Yes|
|Reinstall the controlled computer system|Yes|Yes|Yes|Yes|
|FAN|Yes(Not support PWM controls)|Yes|Yes|Optional(default with heat sink)|
|Display Module|OLED 128x64 white|OLED 128x32 white|OLED 128x64 white|LCD 240x240 color|
|Real Time Clock|Yes(DS1307)|Yes(PCF8563)|Yes(PCF8563)|Yes(PCF8563)|
|Case|Metallic Black|No|Metallic Black White Blue Orange(1U rack compatible)|Metallic Black(1U rack compatible)|
|Buzzer|No|No|No|Yes|
|Custom button|No|No|No|Yes|
|Software update|Yes|Yes|Yes|Yes|
|32GB SD Card|Yes (OS included)|Yes (OS included)|Yes (OS included)|Yes (OS included)|
|HDMI backpower mitigation|No|Yes|Yes|Yes|
|Professional technical support|Yes|Yes|Yes|Yes|

## **Features**

* Video capture (1080P 60Hz)
* Keyboard forwarding  
* Mouse forwarding  
* ATX  
* Fan Control  
* Fullscreen mode  
* Paste text from clipboard  
* VPN support  
* Mass Storage Drive (emulate a CD-ROM or Flash Drive)  
* Multiport KVM over IP  
* OLED to display system info, like temp, uptime, IP  
* Password authentication  
* Support multiple languages  
* Wake-on-LAN  

## **Guides**

[1. BLIKVM v1 CM4 version](./BLIKVM-CM4-guide.md)

[2. BLIKVM v2 PCIE version](./BLIKVM-PCIE-guide.md)

[3. BLIKVM v3 HAT version](./BLIKVM-HAT-guide.md)

[4. BliKVM v4 Allwinner version](./BliKVM-v4-guide.md)
