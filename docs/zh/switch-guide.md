# **HDMI切换器手册**
!!! tip " switch实际使用和测试视频，支持BliKVM和PiKVM"
    <iframe width="560" height="315" src="//player.bilibili.com/player.html?aid=349888644&bvid=BV16R4y1m7Pt&cid=955481186&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
## **简介**
此switch为四通道HDMI+USB切换器，支持机器按键切换，桌面控制器切换，kvm远程切换，3种切换模式。切换器本身最高支持4K@60HZ的输入，即插即用，免驱动。
目前此型号在PiKVM和BliKVM上均完成了适配工作。
!!! note "注意事项"
    * switch可以直接从输入电脑的USB取电，即一般不需要给switch供电，即可正常工作；
    * 若被控电脑的USB供电无法使switch工作，可以对switch进行单独供电使用；
    * switch套装只提供了USB电源线，并没有提供电源适配器，需要客户自行配置电源适配器（5V）；
    * **桌面控制器**可以通过USB电缆控制切换，对于不使用KVM的客户，当您在设备旁边时，这是除使用switch设备上按钮切换之外的另一种切换方式；
    * HDMI输入最高支持**4096x2160/60Hz**；

## **接口示意图**
!!! info "正面和反面接口示意图，右侧图中的control接口即为远程控制接口"
    ![](assets/images/switch/interface-zh1.png){width="600"}
!!! info "侧面接口示意图"
    ![](assets/images/switch/interface-zh2.png){width="600"}
!!! info "设备连接示意图"
    ![](assets/images/switch/interface-zh3.png){width="600"}

## **软件配置**
!!! info "如果你使用的是BliKVM软件，则不需要做任何配置，点击左下角的MORE，找到BliKVM switch这一栏，进行切换选择即可。注意对应通道蓝色小点闪动表示识别到了switch插入，并且正处于当前通道，若无蓝色小点则表示未识别到switch插入。"
    ![](assets/images/switch/blikvm-soft-switch.png){width="600"}


!!! info "若您使用的PiKVM软件，请按照下面的说明进行配置"
    1. 通过SSH登陆PiKVM，用户名和密码均为root;
    2. 终端使用`rw`命令将系统改为可读写系统;
    3. 编辑`/etc/kvmd/override.yaml`此文件，使改文件包含下面的内容.
        ```
        kvmd:
            gpio:
                drivers:
                    hk:
                        type: xh_hk4401
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
                view:
                    table:
                        - ["#Input 1", ch0_led, ch0_button]
                        - ["#Input 2", ch1_led, ch1_button]
                        - ["#Input 3", ch2_led, ch2_button]
                        - ["#Input 4", ch3_led, ch3_button]
        ```
    4. 终端使用`ro`命令将系统重新设置为只读系统；
    5. 终端使用`systemctl restart kvmd`重启服务。
    6. 进入PiKVM web界面，并单击“GPIO”菜单。您应该看到4个输入，其中一个输入有一个绿色圆圈，表示当前已选中。单击其他输入以更改选定的主机。
    ![](assets/images/switch/pikvm-soft-switch.png){width="600"}

## **控制协议**
!!! info "若您希望将blicube的switch用在其它平台上，请参考下面的协议"
    * 通信波特率为19200
    * 切换到1通道发送给switch的消息为**SW1\r\nG01gA**
    * 切换到2通道发送给switch的消息为**SW2\r\nG02gA**
    * 切换到3通道发送给switch的消息为**SW3\r\nG03gA**
    * 切换到4通道发送给switch的消息为**SW4\r\nG04gA**
    * switch返回当前所在通道消息为:**G01gA**,**G02gA**,**G03gA**,**G04gA**



## **发货清单**

| 产品                     | 数量 |备注｜
|-------------------------| ---- |---|
| KVM Switch切换器（4通道)  | 1    |110mm * 60mm * 33mm|
| USB桌面控制器             | 1    ||
| USB数据线                | 4    |长度: 1.2m|
| HDMI（标准接头）线         | 4   |长度: 1.5m|
| USB电源线                 | 1    |长度: 0.8m|
| KVM USB线                 | 1    |长度: 1.5m|
| USB桌面控制线              | 1    |长度: 1m|

