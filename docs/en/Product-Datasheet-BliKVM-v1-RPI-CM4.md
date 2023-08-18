# BliKVM v1 (RPI CM4)

![main](assets/images/BLKVM-CM4/main.png){width="300"}

BliKVM is a production-ready, plug and play KVM-over-IP device that offers professional users a convenient solution **for remote server or workstation management**. It is based on Linux and fully open source. With BliKVM, you can easily **power on/off, restart your computer, configure UEFI/BIOS settings, and perform OS reinstallation using an emulated Mass Storage Device**. BliKVM simulates a keyboard, mouse, and monitor, all accessible through a web browser, ensuring a seamless user experience. **Its hardware-level access guarantees independence from specific remote ports, protocols, or services**, making it a highly flexible and reliable remote management solution for professionals!

## Connectivity diagram

![Interface-Layout-Diagram](assets/images/BLKVM-CM4/Interface-Layout-Diagram.png)

| 1 | OTG port           | 7   | Micro SD card slot |
| ----- | ------------------------------- | ---- | ----------------------------- |
| 2     | USB3.0 x2 | 8  | ACT LED (green) |
| 3     | ATX control port           | 9  | Ethernet port |
| 4     | HDMI video input port | 10  | OLED Display |
| 5     | PWR IN port                | 11  | Antenna mounting hole |
| 6     | Power LED (red)       |      |                       |

## Specifications

![Topology-Diagram](assets/images/BLKVM-CM4/Topology-Diagram.png)

| Parameter name              | Characteristics                                              |
| --------------------------- | ------------------------------------------------------------ |
| **Power**                   |                                                              |
| 5V 3A                       | PWR IN port                                                  |
|                             |                                                              |
| **Connectivity/Interfaces** |                                                              |
| HDMI IN                     | HDMI video input port                                        |
| OTG                         | Keyboard, mouse, mass storage, and other external device emulation |
| CN-ATX                      | Turn on/off or restart the controlled computer               |
| Micro SD card slot          | Persistent storage for OS and your data                      |
| PWR IN port                 | 5V 3A power port                                             |
|                             |                                                              |
| **Displays and indicators** |                                                              |
| LED indicators              | Power LED (red), ACT LED (green)                             |
| OLED display                | OLED 128x64 0.96 inch                                        |
|                             |                                                              |
| **Video**                   |                                                              |
| Supported resolutions       | Up to 1920x1200@60Hz                                         |
| Video compression methods   | H.264, MJPEG                                                 |
|                             |                                                              |
| **Core**                    |                                                              |
| Chip                        | Raspberry Pi Compute Module 4                                |
|                             |                                                              |
| **Power consumption**       | Up to 15W                                                    |
|                             |                                                              |
| **Environmental**           |                                                              |
| Operating temperature       | 0°C to 70°C                                                  |
| Storage temperature         | -20°C to 60°C                                                |
|                             |                                                              |
| **Dimensions and weight**   |                                                              |
| Size                        | 120(L) x 70W) x 37(H) mm                                     |
| Weight                      | 0.45 kg                                                      |

## Dimensions Schematic Diagram

![Dimensions](assets/images/BLKVM-CM4/Dimensions.png)
