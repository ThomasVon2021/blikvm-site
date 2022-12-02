# ATXA ガイド

## **1. はじめに**
ATXAはコンピュータの電源を管理するためのATXアダプタボードです。
この製品にはAボードとBボードの2つのボードで構成されます。AボードはRaspberry Piへ接続し、Bボードはコンピュータのマザーボードへ接続します。そして、AボードとBボードはネットワークケーブルで接続します。
この製品のニュース、質問やサポートは<a href="https://discord.gg/9Y374gUF6C" target="_blank">Discord コミュニティチャット </a>に参加してください。
 
| ATXA_A                                       | ATXA_B                                       |
|----------------------------------------------|----------------------------------------------|
| ![ATXA_A](assets/images/atx/ATXA_A.png){width="400"} | ![ATXA_B](assets/images/atx/ATXA_B.png){width="250"} |

## **2. Aボード**
AボードはRaspberry Piへ接続します。下記の表はPiKVMアプリケーションでの一般的な接続です。

| A-board | RPI4   |
| ------- | ------ |
| GND     | GND    |
| 3V3     | 3V3    |
| LED PWR | GPIO24 |
| LED HDD | GPIO22 |
| SW PWR  | GPIO23 |
| SW RST  | GPIO27 |

![2](assets/images/atx/status.png){width="400"}

AボードはネットワークケーブルでBボードへ接続されます。下記の表はAボードとBボードのピンの接続および状態対応表です。

|  Aボードのピン  |                          Bボードのピン                           |
|:-----------------:|:------------------------------------------------------------------:|
|  LED PWR - HIGH  |                 LED PWR+ - HIGH,  LED PWR- - LOW                 |
|  LED PWR - LOW   |                 LED PWR+ - LOW,  LED PWR- - LOW                  |
|  LED HDD - HIGH  |                 LED HDD+ - HIGH,  LED HDD- - LOW                 |
|  LED HDD - LOW   |                 LED HDD+ - LOW,  LED HDD- - LOW                  |
|  SW PWR - HIGH   |    BTN PWR+ と BTN PWR- が短絡, 電源ボタンが押された状態              |
|   SW PWR - LOW   | BTN PWR+ と BTN PWR- が切断, 電源ボタンが押されていない状態             |
|  SW RST - HIGH   |    BTN RST+ と BTN RST- が短絡, リセットボタンが押された状態    |
|   SW RST - LOW   | BTN RST+ と BTN RST- が切断, リセットボタンが押されていない状態  |

## **3. Bボード**

Bボードには標準のブラケットとロープロファイルのブラケットが付属します。コンピュータのケースに合わせて設置してください。製品に付属するデュポンケーブルでコンピュータのマザーボードにあるATXコントロールインターフェイスとBボードのピンを接続してください。

![3](assets/images/atx/physical_map.png){width="400"}

## **3.寸法**

![4](assets/images/atx/4.png)

## **4.テストビデオ**
YouTube：<a href="https://www.youtube.com/watch?v=gOFdGrVMBU8" target="_blank">ATX</a>

## **5.リンク**
購入に関して：<a href="https://www.aliexpress.com/item/1005003761450893.html?spm=a2g0o.store_pc_allProduct.8148356.12.4c8f16b4prvvUV" target="_blank">ATX</a>
