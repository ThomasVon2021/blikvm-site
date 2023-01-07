# **HDMI Switch Mannul**
!!! tip "Switch uses and tests video, supporting BliKVM and PiKVM"
    <iframe width="560" height="315" src="//player.bilibili.com/player.html?aid=349888644&bvid=BV16R4y1m7Pt&cid=955481186&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
## **Introduction**
This switch is a four channel HDMI+USB switch, which supports machine key switching, desktop controller switching, kvm remote switching. Maximum support of the switch itself 4K@60HZ Plug and play, drive free.
At present, this model has been adapted to PiKVM and BliKVM.
!!! note "points for attention"
    * The switch can be powered directly from the USB input to the computer, that is, the switch can work normally without power supply.
    * If the USB power supply of the controlled computer cannot make the switch work, the switch can be powered independently.
    * The switch package only provides a USB power cable, but does not provide a power adapter. The customer needs to configure a power adapter (5V).

## **接口示意图**
!!! info "Front and back interface diagram, the control interface in the right figure is the remote control interface."
    ![](assets/images/switch/interface-en1.png){width="600"}
!!! info "Schematic Diagram of Side Interface."
    ![](assets/images/switch/interface-en2.png){width="600"}
!!! info "Equipment connection diagram."
    ![](assets/images/switch/interface-en3.png){width="600"}

## **软件配置**
!!! info "If you use the BliKVM software, you do not need to do any configuration. Click **MORE** in the lower left corner, find the BliKVM switch column, and then switch. Note that the flashing blue dot of the corresponding channel indicates that the switch insertion is recognized and is in the current channel. If there is no blue dot, the switch insertion is not recognized。"
    ![](assets/images/switch/blikvm-soft-switch.png){width="600"}


!!! info "If you use PiKVM software, please configure it according to the following instructions."
    1. Log in to PiKVM through SSH. The user name and password are root;
    2. Uses the `rw` command on the terminal to change the system to a read-write system;
    3. Edit `/etc/kvmd/override. yaml` this file to make it contain the following contents.
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
    4. Use the `ro` command on the terminal to reset the system to a read-only system;
    5. Use 'systemctl restart kvmd' on the terminal to restart the service;
    6. Enter the PiKVM web interface and click the GPIO menu. You should see 4 inputs, one of which has a green circle to indicate that it is currently selected. Click Other Inputs to change the selected host.
    ![](assets/images/switch/pikvm-soft-switch.png){width="600"}

## **控制协议**
!!! info "If you want to use the blicube switch on other platforms, please refer to the following protocol"
    * The communication baud rate is 19200
    * The message sent to switch by switching to channel 1 is**SW1\r\nG01gA**
    * The message sent to switch by switching to channel 2 is**SW2\r\nG02gA**
    * The message sent to switch by switching to channel 3 is**SW3\r\nG03gA**
    * The message sent to switch by switching to channel 4 is**SW4\r\nG04gA**
    * The message returned by the switch for the current channel is:**G01gA**,**G02gA**,**G03gA**,**G04gA**



## **发货清单**

| product            |    quantity |
|----------------------------| ---- |
| KVM Switch(4-channel)     | 1    |
| USB cable | 4  |
| HDMI(Standard) cable| 4 |
| USB power cable | 1    |
| KVM USB cable| 1    |
| USB desktop control cable| 1    |

