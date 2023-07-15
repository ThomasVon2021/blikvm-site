

# BliKVM v4 Datasheet

 ![Main](assets/images/v4/Datasheet-BliKVM-v4.assets/Main.png){width="400"}


## Connectivity diagram

![Interface-Layout-Diagram](assets/images/v4/Datasheet-BliKVM-v4.assets/Interface-Layout-Diagram.png)

| 1 | USB 2.0 port 1              | 10   | Antenna interface             |
| ----- | ------------------------------- | ---- | ----------------------------- |
| 1 | USB 2.0 port 1              | 10   | Antenna interface             |
| 2     | Power Input 5V 3A & UART        | 11   | RJ45 100M Ethernet port & PoE |
| 3     | RJ45 ATX control port           | 12   | Display 1.33 inch TFT         |
| 4     | HDMI video Loop through port | 13   | Power LED (red)             |
| 5     | USB-PC port                     | 14   | User defined button SW1       |
| 6     | Power Input 12V 2A              | 15   | ACT LED (green) |
| 7     | HDMI video input port           | 16 | Display ON/OFF button         |
| 8     | HDMI input status LED (green)  | 17   | Micro SD card slot            |
| 9     | HDMI output status LED (yellow) |      |                               |

## Specifications

![Topology-Diagram](assets/images/v4/Datasheet-BliKVM-v4.assets/Topology-Diagram.png)

| Parameter name              | Characteristics                                              |
| --------------------------- | ------------------------------------------------------------ |
| **Power**                   |                                                              |
| 5V 3A                       | 5V port, USB-PC port                                         |
| 12V 2A                      | 12V port                                                     |
| PoE                         | Power over Ethernet (IEEE802.3af compliant)  48Vdc           |
|                             |                                                              |
| **Connectivity/Interfaces** |                                                              |
| HDMI-IN                     | HDMI video input port                                        |
| HDMI-OUT                    | HDMI video Loop through port                                 |
| USB-PC                      | Keyboard, mouse, mass storage, and other external device emulation) |
| ATX                         | Turn on/off or restart the controlled computer               |
| WiFi&BT                     | IEEE802.11 b/g/n + BLE4.2                                    |
| Micro SD card slot          | Persistent storage for OS and your data                      |
| 5V port                     | 5V 3A power or serial console management port                |
|                             |                                                              |
| **Displays and indicators** |                                                              |
| LED indicators              | Power LED, ACT LED， HDMI input status LED (green)， HDMI output status LED (yellow) |
| TFT display                 | TFT 240x240 1.33 inch                                        |
| User defined button         | SW1                                                          |
| Buzzer                      | Find me                                                      |
|                             |                                                              |
| **Video**                   |                                                              |
| Supported resolutions       | Up to 4k@30Hz                                                |
| Video compression methods   | MJPEG                                                        |
|                             |                                                              |
| **Core**                    |                                                              |
| Chip                        | ALLWINNER H616                                               |
| RAM                         | 1GB                                                          |
|                             |                                                              |
| **Power consumption**       | Up to 15W                                                    |
|                             |                                                              |
| **Environmental**           |                                                              |
| Operating temperature       | 0°C to 70°C                                                  |
| Storage temperature         | -20°C to 60°C                                                |
|                             |                                                              |
| **Dimensions and weight**   |                                                              |
| Size                        | 100 (L) x 134 (W) x 44.4 (H) mm                              |
| Weight                      | 0.45 kg                                                      |

## Dimensions Schematic Diagram

![Dimensions](assets/images/v4/Datasheet-BliKVM-v4.assets/Dimensions.png){width="400"}
