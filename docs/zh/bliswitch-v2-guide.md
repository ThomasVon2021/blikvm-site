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

??? info "若您使用的PiKVM软件，基于树莓派譬如(v1 v2 v3)版本，和v4基于Allwinner版本配置不太一致，v4多了ATX的配置。"
    v4使用效果展示
    ![Interface](assets/images/Product-Datasheet-BliSwitch-v2.assets/pikvm-ui-bliswitch-v2.png)
    1. 修改xh_hk4401.py从而可以支持8通道
    ```
    修改你本地的 /usr/lib/python3/dist-packages/kvmd/plugins/ugpio/xh_hk4401.py
    https://github.com/pikvm/kvmd/blob/master/kvmd/plugins/ugpio/xh_hk4401.py#L90 将3改成7
    https://github.com/pikvm/kvmd/blob/master/kvmd/plugins/ugpio/xh_hk4401.py#L175 将 [1-4] 改成 [1-8]
    https://github.com/pikvm/kvmd/blob/master/kvmd/plugins/ugpio/xh_hk4401.py#L185 将 <= 3 改成 <= 7 
    ```
    你可以直接下载替换[xh_hk4401.py](https://zcwrego195.feishu.cn/file/TomlbzbE9oxHTNxVVRJcL5Z5nId?from=from_copylink)
    2. 树莓派譬如(如BliKVM v1 v2 v3)版本, /etc/kvmd/override.yaml配置
    ```
    kvmd:
    gpio:
        drivers:
            hk:
                type: xh_hk4401
                protocol: 1
                device: /dev/ttyUSB0
        scheme:
            ch0_led:
                driver: hk
                pin: 0
                mode: input
            ch1_led:
                driver: hk
                pin: 1
                mode: input
            ch2_led:
                driver: hk
                pin: 2
                mode: input
            ch3_led:
                driver: hk
                pin: 3
                mode: input
            ch4_led:
                driver: hk
                pin: 4
                mode: input
            ch5_led:
                driver: hk
                pin: 5
                mode: input
            ch6_led:
                driver: hk
                pin: 6
                mode: input
            ch7_led:
                driver: hk
                pin: 7
                mode: input
            ch0_button:
                driver: hk
                pin: 0
                mode: output
                switch: false
            ch1_button:
                driver: hk
                pin: 1
                mode: output
                switch: false
            ch2_button:
                driver: hk
                pin: 2
                mode: output
                switch: false
            ch3_button:
                driver: hk
                pin: 3
                mode: output
                switch: false
            ch4_button:
                driver: hk
                pin: 4
                mode: output
                switch: false
            ch5_button:
                driver: hk
                pin: 5
                mode: output
                switch: false
            ch6_button:
                driver: hk
                pin: 6
                mode: output
                switch: false
            ch7_button:
                driver: hk
                pin: 7
                mode: output
                switch: false
        view:
            table:
                - ["#Input 1", ch0_led, ch0_button]
                - ["#Input 2", ch1_led, ch1_button]
                - ["#Input 3", ch2_led, ch2_button]
                - ["#Input 4", ch3_led, ch3_button]
                - ["#INPUT 5", ch4_led, ch4_button]
                - ["#INPUT 6", ch5_led, ch5_button]
                - ["#INPUT 7", ch6_led, ch6_button]
                - ["#INPUT 8", ch7_led, ch7_button]
    ```
    3. BliKVM v4版本, /etc/kvmd/override.yaml配置
    ```
    kvmd:
    gpio:
        drivers:
            ### requires compiled atx binary per https://github.com/RainCat1998/Bli-PiKVM#configure-atx-controller
            power_short:
                type: cmd
                cmd: [/usr/bin/sudo, /usr/bin/atx, --v, v4, --c, power_on]
            power_long:
                type: cmd
                cmd: [/usr/bin/sudo, /usr/bin/atx, --v, v4, --c, power_off]
            reset_sw:
                type: cmd
                cmd: [/usr/bin/sudo, /usr/bin/atx, --v, v4, --c, power_reset]

            ### BliKVM v2 Switch ###
            hk:
                type: xh_hk4401
                protocol: 1
                device: /dev/ttyUSB0

        scheme:
            on-off-button:
                driver: power_short
                pin: 0
                mode: output
                switch: false
            force-off-button:
                driver: power_long
                pin: 0
                mode: output
                switch: false
            reset-button:
                driver: reset_sw
                pin: 0
                mode: output
                switch: false

            ch0_led:
                driver: hk
                pin: 0
                mode: input
            ch1_led:
                driver: hk
                pin: 1
                mode: input
            ch2_led:
                driver: hk
                pin: 2
                mode: input
            ch3_led:
                driver: hk
                pin: 3
                mode: input
            ch4_led:
                driver: hk
                pin: 4
                mode: input
            ch5_led:
                driver: hk
                pin: 5
                mode: input
            ch6_led:
                driver: hk
                pin: 6
                mode: input
            ch7_led:
                driver: hk
                pin: 7
                mode: input

            ch0_button:
                driver: hk
                pin: 0
                mode: output
                switch: false
            ch1_button:
                driver: hk
                pin: 1
                mode: output
                switch: false
            ch2_button:
                driver: hk
                pin: 2
                mode: output
                switch: false
            ch3_button:
                driver: hk
                pin: 3
                mode: output
                switch: false
            ch4_button:
                driver: hk
                pin: 4
                mode: output
                switch: false
            ch5_button:
                driver: hk
                pin: 5
                mode: output
                switch: false
            ch6_button:
                driver: hk
                pin: 6
                mode: output
                switch: false
            ch7_button:
                driver: hk
                pin: 7
                mode: output
                switch: false

        view:
            table:
                - []
                - ["#BliKVM v2 Switch"]
                - []
                - ["#INPUT 1", ch0_led, ch0_button]
                - ["#INPUT 2", ch1_led, ch1_button]
                - ["#INPUT 3", ch2_led, ch2_button]
                - ["#INPUT 4", ch3_led, ch3_button]
                - ["#INPUT 5", ch4_led, ch4_button]
                - ["#INPUT 6", ch5_led, ch5_button]
                - ["#INPUT 7", ch6_led, ch6_button]
                - ["#INPUT 8", ch7_led, ch7_button]
                - []
                - ["#ATX on BliKVM hardware - selected INPUT ONLY"]
                - []
                - ["on-off-button|confirm|On/Off", "force-off-button|confirm|Force Off", "reset-button|confirm|Reset"]
    ```


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


