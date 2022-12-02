# USB/PWR スプリッタガイド

## **1. はじめに**

![image-20220107110102815](assets/images/usb-splitter/usb-splitter.png)

このアダプタを使うことにより、Raspberry Pi 4のUSB-CポートでUSB-OTGのデータ通信を使いながらUSB-C電源による給電を行えます。

USB-C (RPI4) <> USB-C (USB) と USB-C (PWR)

|   USB-C(RPI4)   |  USB Type-C(USB)  |  USB Type-C(PWR)  |
|:---------------:|:-----------------:|:-----------------:|
|       5V        |                   |        5V         |
|       D-        |        D-         |                   |
|       D+        |        D+         |                   |
|  CC1 10k to 5V  |  CC1 5.1k to GND  |  CC1 5.1k to GND  |
|  CC2 10k to 5V  |  CC2 5.1k to GND  |  CC2 5.1k to GND  |
|       GND       |        GND        |        GND        |

Raspberry Pi 4でこのアダプタを使用するには下記の部品を用意してください。

- USB-C - USB-C ケーブル[1] Raspberry Pi 4とアダプタとの接続
- USB-C - USB-C/USB Type-A ケーブル アダプタとPCとの接続
- USB-C電源[2] Raspberry Pi 純正USB Type-C 電源

[1] USB-Cケーブルは一般的に電源供給を想定して設計されていますが、できるだけ電圧降下を防ぐために短いケーブルでRaspberry Pi 4と接速してください。

[2] **注意** このボードはデバイスへ5Vの電源から5Vの電圧を供給するようにデザインされています。

このような電源アダプタはUSBの規格に沿っていません。Raspberry Piと純正のUSB-C電源アダプタは専用の設計となっており、他の電源アダプタや充電器を使用した場合には故障の原因となります。

## **2.寸法**

![image-20220107154909710](assets/images/usb-splitter/usb-splitter-size.png)

## **3.テストビデオ**

[USB splitter](https://www.youtube.com/watch?v=4Od5MjBHbhY)
