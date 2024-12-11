# **8口KVM+ATX切换器 BliSwitch v2**


![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/front.png)
![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/back.png)
BliSwitch v2是一款8通道KVM+ATX切换器，使8台主机共享一套键盘、鼠标和HDMI屏幕，且实现对8台主机的开关机控制。
![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/main.png)

## **端口定义**

![Interface](assets/images/Product-Datasheet-BliSwitch-v2.assets/Interface.png)

## **产品参数**

| 品牌     | BLI                                             |
| -------- | ----------------------------------------------- |
| 品名     | 8口KVM+ATX切换器                                |
| 型号     | BliSwitch v2                                    |
| 功能     | 八台主机共享一套键鼠和显示器，8台主机开关机控制 |
| 材质     | 全金属                                          |
| 分辨率   | 1080P60Hz                                       |
| 切换方式 | 按键切换 或 USB控制模块切换                     |
| 供电     | 5V1A                                            |

## **控制协议**
!!! info "若您希望将blicube的switch用在其它平台上，请参考下面的协议"
    * 通信波特率为19200
    * 切换到1通道发送给switch的消息为SW1\r\nG01gA
    * 切换到2通道发送给switch的消息为SW2\r\nG02gA
    * 切换到3通道发送给switch的消息为SW3\r\nG03gA
    * 切换到4通道发送给switch的消息为SW4\r\nG04gA
    * 切换到1通道发送给switch的消息为SW5\r\nG05gA
    * 切换到2通道发送给switch的消息为SW6\r\nG06gA
    * 切换到3通道发送给switch的消息为SW7\r\nG07gA
    * 切换到4通道发送给switch的消息为SW8\r\nG08gA
    * switch返回当前所在通道消息为:G01gA,G02gA,G03gA,G04gA,G05gA,G06gA,G07gA,G08gA


## **软件配置**

!!! info "如果你使用的是BliKVM软件，在1.5.3版本后,在BliKVM启动前先把switch通电并接好线，然后通过web界面进行使能和配置即可。"
    - 如果插入了多个USB设备，需要用命令`ls /dev/ttyUSB*`判断出switch的设备名称, 然后在web界面进行配置。

!!! info "若您使用的PiKVM软件，参考switch v1中的配置，类型配置仍为:`type: xh_hk4401`"
    - 目前xh_hk4401类型PiKVM软件做了限制，无法扩展到8通道，正在适配中;
    - 可以先在web使能4通道后，在命令行使用如`echo -ne "SW8\r\nG08gA" > /dev/ttyUSB0`,切换到其它通道;

## **连接参考**
![connect](assets/images/Product-Datasheet-BliSwitch-v2.assets/connect.png)

## **尺寸**

![Dimensions](assets/images/Product-Datasheet-BliSwitch-v2.assets/Dimensions.png)


## **发货清单**

| 产品                     | 数量 |备注｜
|-------------------------| ---- |---|
| BliSwitch v4切换器 | 1    ||
| 挂耳                | 2    ||
| ATX线 公头         | 8   | |
| ATX线 母头         | 8    | |
| 全高PCIe挡板        | 8    | |
| 半高PCIe挡板        | 8    | |
| ATX板              | 8    | |
| 控制线              | 1    | |
| USB线         | 1    | |
| 胶垫         | 4    | |
| M2.5x5 沉头螺钉 | 10    | |

![Dimensions](assets/images/Product-Datasheet-BliSwitch-v2.assets/packlist-removebg-preview.png)


