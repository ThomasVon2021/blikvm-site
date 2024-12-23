# **BliSwitch v2 8-port KVM+ATX switch**
![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/front.png)
![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/back.png)
The BliSwitch v2 is an 8-channel KVM+ATX switch for 8 hosts to share input and power.
Function: 8 hosts share a keyboard, mouse, and display, with power control for all.
Switch Method: Button or USB control.
![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/main.png)

!!! info "BliSwitchv2 Introduction"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/BipzzTIIIQg?si=8Ygw3gYhE-Sgm6mF" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## **Features**
* **ATX on each port(support button and remote control)**
* **Full control via web ui**
* **Compatible with BLIKVM V1, V2, V3 V4 and PikVM hardware.**


## **Port Definition**

![Interface](assets/images/Product-Datasheet-BliSwitch-v2.assets/interface-en.png)

## **Product Parameters**

| Brand    | BLI                                             |
| -------- | ----------------------------------------------- |
| Name     | 8-port KVM+ATX switcher                         |
| Model    | BliSwitch v2                                    |
| Function | Eight hosts share a set of keyboard, mouse, and display, power control of 8 hosts |
| Material | All metal                                       |
| Resolution | 1080P60Hz                                     |
| Switching Method | Button switching or USB control module switching |
| Power Supply | 5V1A                                        |

## **Control Protocol**
!!! info "If you want to use Blicube's switch on other platforms, please refer to the following protocol"
    * Communication baud rate is 19200
    * The message to switch to channel 1 is SW1\r\nG01gA
    * The message to switch to channel 2 is SW2\r\nG02gA
    * The message to switch to channel 3 is SW3\r\nG03gA
    * The message to switch to channel 4 is SW4\r\nG04gA
    * The message to switch to channel 5 is SW5\r\nG05gA
    * The message to switch to channel 6 is SW6\r\nG06gA
    * The message to switch to channel 7 is SW7\r\nG07gA
    * The message to switch to channel 8 is SW8\r\nG08gA
    * The message returned by the switch for the current channel is: G01gA, G02gA, G03gA, G04gA, G05gA, G06gA, G07gA, G08gA

## **Software Configuration**
!!! info "If you are using BliKVM software, from version 1.5.3 onwards, power on the switch and connect the cables before starting BliKVM, then enable and configure it through the web interface."
    - If multiple USB devices are connected, use the command `ls /dev/ttyUSB*` to identify the switch's device name, then configure it through the web interface.

??? info "If you are using PiKVM software, the configuration for Raspberry Pi versions (v1, v2, v3) and the Allwinner-based v4 version is slightly different, with v4 having additional ATX configuration."
    v4 usage demonstration
    ![Interface](assets/images/Product-Datasheet-BliSwitch-v2.assets/pikvm-ui-bliswitch-v2.png)
    1. Modify xh_hk4401.py to support 8 channels
    ```
    Modify /usr/lib/python3/dist-packages/kvmd/plugins/ugpio/xh_hk4401.py
    https://github.com/pikvm/kvmd/blob/master/kvmd/plugins/ugpio/xh_hk4401.py#L90 need to be changed from 3 to 7 also
    https://github.com/pikvm/kvmd/blob/master/kvmd/plugins/ugpio/xh_hk4401.py#L175 change [1-4] to [1-8]   (used to get which input switch is on) 
    https://github.com/pikvm/kvmd/blob/master/kvmd/plugins/ugpio/xh_hk4401.py#L185 change channel <= 3 to <= 7  (used to change inputs)
    ```
    You can directly download and replace [xh_hk4401.py](https://zcwrego195.feishu.cn/file/TomlbzbE9oxHTNxVVRJcL5Z5nId?from=from_copylink)
    2. For Raspberry Pi versions (e.g., BliKVM v1, v2, v3), /etc/kvmd/override.yaml configuration
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
    3. For BliKVM v4 version, /etc/kvmd/override.yaml configuration
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
    


## **Connection Reference**
![connect](assets/images/Product-Datasheet-BliSwitch-v2.assets/connect.png)

## **Dimensions**

![Dimensions](assets/images/Product-Datasheet-BliSwitch-v2.assets/Dimensions.png)


## **Shipping List**

| Product                  | Quantity | Remarks |
|-------------------------| -------- | ------- |
| BliSwitch v4 switcher   | 1        |         |
| Mounting ears           | 2        |         |
| ATX cable male end      | 8        |         |
| ATX cable female end    | 8        |         |
| Full-height PCIe bracket| 8        |         |
| Half-height PCIe bracket| 8        |         |
| ATX board               | 8        |         |
| Control cable           | 1        |         |
| USB cable               | 1        |         |
| Rubber pads             | 4        |         |
| M2.5x5 countersunk screws | 10     |         |

![Dimensions](assets/images/Product-Datasheet-BliSwitch-v2.assets/packlist-removebg-preview.png)

## **Buy link**

[Buy Bliswitch v2](https://www.aliexpress.com/item/1005008024603865.html)
