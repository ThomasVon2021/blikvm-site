# **BliSwitch v2 8-port KVM+ATX switch**
![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/front.png)
![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/back.png)
The BliSwitch v2 is an 8-channel KVM+ATX switch for 8 hosts to share input and power.
Function: 8 hosts share a keyboard, mouse, and display, with power control for all.
Switch Method: Button or USB control.
![main](assets/images/Product-Datasheet-BliSwitch-v2.assets/main.png)

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

!!! info "If you are using PiKVM software, refer to the configuration in switch v1, expanding from 4 channels to 8 channels. The type configuration remains: `type: xh_hk4401`"
    - Currently, the PiKVM software with type `xh_hk4401` has limitations and cannot be expanded to 8 channels. Adaptation is in progress.

- After initializing `/dev/ttyUSB0`, use the command `echo -ne "SW8\r\nG08gA" > /dev/ttyUSB0` to switch to other channels.
- After initializing `/dev/ttyUSB0`, use the command `cat /dev/ttyUSB0` to check the current channel.

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
