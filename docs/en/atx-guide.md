# ATXA guide

## **1. Introduction**

ATXA is an ATX adapter board to manage the power of your computer.

The product includes two modules; A-board and B-board. A-board is connected to the Raspberry Pi, B-board is connected to the computer's motherboard, and A-board is connected to B-board through a network cable.

Join the <a href="https://discord.gg/9Y374gUF6C" target="_blank">Discord Community Chat</a> for news, questions and support!

| ATXA_A                                       | ATXA_B                                       |
|----------------------------------------------|----------------------------------------------|
| ![ATXA_A](assets/images/atx/ATXA_A.png){width="400"} | ![ATXA_B](assets/images/atx/ATXA_B.png){width="250"} |

## **2. A-board**

![2](assets/images/atx/status.png){width="400"}
A-board is connected to the Raspberry Pi.

***

The following table is a typical connection method in PiKVM application.

| A-board | RPI4   |
| ------- | ------ |
| GND     | GND    |
| 3V3     | 3V3    |
| LED PWR | GPIO24 |
| LED HDD | GPIO22 |
| SW PWR  | GPIO23 |
| SW RST  | GPIO27 |
|![raspberry-board](assets/images/atx/raspberry-board.png){width="300"}|![raspberry-gpio](assets/images/atx/raspberry-gpio.png){width="300"}|  

A-board is connected to B-board through a network cable. The following table is the corresponding relationship between the pin status of A-board and B-board.

|  Pins on A-board  |                          Pins on B-board                           |
|:-----------------:|:------------------------------------------------------------------:|
|  LED PWR is HIGH  |                 LED PWR+ is HIGH,  LED PWR- is LOW                 |
|  LED PWR is LOW   |                 LED PWR+ is LOW,  LED PWR- is LOW                  |
|  LED HDD is HIGH  |                 LED HDD+ is HIGH,  LED HDD- is LOW                 |
|  LED HDD is LOW   |                 LED HDD+ is LOW,  LED HDD- is LOW                  |
|  SW PWR is HIGH   |    BTN PWR+ and BTN PWR- connected, the power button is pressed    |
|   SW PWR is LOW   | BTN PWR+ and BTN PWR- disconnected, the power button is unpressed  |
|  SW RST is HIGH   |    BTN RST+ and BTN RST- connected, the reset button is pressed    |
|   SW RST is LOW   | BTN RST+ and BTN RST- disconnected, the reset button is unpressed  |

## **3. B-board**

The b-board has an adapted full-height and half-height metal PCI mounting plate, which can be installed on the computer case. The user connects the pins on the B-board to the ATX control interface on the computer motherboard using the color DuPont cables provided with the product.  
![3](assets/images/atx/physical_map.png){width="400"}

!!! info "ATXA-B Instructions for connecting to the computer motherboard"
    According to the instructions of the computer motherboard, first find the position of the ATX function related pins on the motherboard, and then unplug the ATX ray that has been connected to the motherboard. After unplugging, the power button of the computer will lose its function. There are two rows of 8PIN pins on the ATXA-B motherboard. It is unnecessary to distinguish between the two rows of pins when they are used with the same functions. One row of pins is used for KVM to control ATX-related functions, and the other row of pins is connected to the ATX DuPont head unplugged from the main board to maintain the original chassis power button function. Connect each wire according to the specific pin definitions on the motherboard and ATXA-B. See the following figure for the connection relationship：  
    ![ATXA-B-motherboard](assets/images/atx/ATXA-B-motherboard.png)

## **4.Mechanical Diagram**

![4](assets/images/atx/4.png)

## **5. Test video**

YouTube: <a href="https://www.youtube.com/watch?v=gOFdGrVMBU8" target="_blank">ATX</a>

## **6. Purchase**

Purchase：<a href="https://www.aliexpress.com/item/1005003761450893.html?spm=a2g0o.store_pc_allProduct.8148356.12.4c8f16b4prvvUV" target="_blank">ATX</a>
