# BLIKVM HAT バージョンガイド
## **はじめに**

!!! info "BLIKVM HAT ビデオ"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/SdpmMojDbGA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Raspberry Pi IPKVM HATはKVM over IPに特化したRaspberry Pi 4専用アドオンボードです。
BLIKVM-RPI4はRaspberry Pi 4のPoEに対応したKVM HATです。この製品の主な機能は、ビデオキャプチャ、ATXアダプタ、PoE、OLED、そしてRTCです。HATを熱から守るための専用金属ケースが付属します。そのケースは1Uのラックに設置できます。そして、blikvmおよびpikvmのソフトウェアイメージを利用できます。

 ![Image title](assets/images/BLIKVM-HAT/case.png){width="300"}  
## **インストール要件**
!!! note "組み立てキットの場合には下記のものが必要となります"
    * Raspberry Pi 4B (1GB 以上のRAM)
    * HDMIケーブル
    * ストレートイーサネットケーブル(ATXアダプタボードへの接続に利用)
    * 電源およびケーブル(5.1V 3A USB-C, Raspberry Pi専用を推奨).

## **基本設定**
**1.** [microSDカードまたはeMMCにOSイメージを書き込む](./flashing_os.md) 

**2.BLIKVMを組み立てる** ビデオまたは[組み立て手順](./BLIHAT-Installation.md)を参考に進めてください

??? info "ビデオガイド: 金属ケース組み立て"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/FaZBQUA7rAM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**3.** ATXアダプタボードのインストール

!!! info "ボードには標準のPCIe I/Oブラケットとロープロファイルのブラケットが付属します。必要な方を使用してください"
    ![IMG_8366](assets/images/BLIKVM-HAT/hat-install/IMG_8366.JPG){width="300"}
    ![IMG_8367](assets/images/BLIKVM-HAT/hat-install/IMG_8367.JPG){width="300"}

!!! info "ATXアダプタボードからマザーボードとケースパネルへの接続にデュポンケーブルを使用してください。ピンの接続先はボードに記載されています"
    ![IMG_8368](assets/images/BLIKVM-HAT/hat-install/IMG_8368.JPG){width="300"}
    ![IMG_8369](assets/images/BLIKVM-HAT/hat-install/IMG_8369.JPG){width="300"}

!!! info "ATXアダプタボードをケースに取り付けてください"
    ![IMG_8370](assets/images/BLIKVM-HAT/hat-install/IMG_8370.JPG){width="300"}

!!! info "RJ45のネットワークケーブルでATXアダプタボードとHATのCN-ATXインターフェイスを繋いでください"
    ![004d8da8059a57b87d2d40ce70174e7](assets/images/BLIKVM-HAT/hat-install/004d8da8059a57b87d2d40ce70174e7.png){width="300"}

**4.** HDMIケーブルの接続

!!! info "HATのHDMI INポートとコンピュータのHDMI出力ポートをHDMIケーブルで直接接続してください。HDMIパススルーEDIDエミュレータは必要ありません。もし、コンピュータが正しいHDMI出力を行わない場合は、HDMIパススルーEDIDエミュレータをコンピュータのHDMI出力ポートに挿してください。これはコンピュータのHDMI出力フォーマットを修正します。"
    ![30c484ad28e149b703ccc74c09e52db](assets/images/BLIKVM-HAT/hat-install/30c484ad28e149b703ccc74c09e52db.png){width="300"}
    ![IMG_8373](assets/images/BLIKVM-HAT/hat-install/IMG_8373.JPG){width="300"}

**5.** USBケーブルの接続
!!! info "RPI4ポートをRaspberry Pi 4へ接続してください"
    ![IMG_8374](assets/images/BLIKVM-HAT/hat-install/IMG_8374.JPG){width="300"}
    ![IMG_8375](assets/images/BLIKVM-HAT/hat-install/IMG_8375.JPG){width="300"}

!!! info "USBポートを操作されるコンピュータへ接続してください"
    ![IMG_8376](assets/images/BLIKVM-HAT/hat-install/IMG_8376.JPG){width="300"}

!!! warning "PoEを使用して給電している場合は、PWRポートを接続する必要はありません。PoEを使用しない場合は、標準の5V/3AのUSB電源をPWRポートへ接続してください。"

**6.** テスト
!!! info "PoEで給電している場合は、HATはネットワークケーブル経由でルーターへ接続されます"
    ![IMG_8377](assets/images/BLIKVM-HAT/hat-install/IMG_8377.JPG){width="300"}

!!! info "OLEDディスプレイにIPアドレスなどのデバイスの状態を表示します"
    ![IMG_8379](assets/images/BLIKVM-HAT/hat-install/IMG_8379.JPG){width="300"}

!!! info "表示されたIPアドレスへWebブラウザからアクセスしてください"
    ![image-20220621174207504](assets/images/BLIKVM-HAT/hat-install/image-20220621174207504.png){width="300"}

## **仕様**
![Image title](assets/images/BLIKVM-HAT/specification.png){width="600"}

??? note "**HDMI IN**"
    ビデオとオーディオ(I2S)のキャプチャをサポートする東芝のTC358743と言うチップを使用しています。そして、ビデオキャプチャの最大解像度は1080P 50fpsです。HDMIバックパワーによる問題は修正されています。

??? note "**CN-ATX**"
    CN-ATXインターフェイスはネットワークケーブルでATXアダプタボード(HATに付属するアクセサリ)と接続します。これによりコンピュータの電源スイッチ、リセットボタンなどを操作できます。

??? note "**Display**"
    SSD1306を搭載した解像度128x32の白色OLEDディスプレイです。このディスプレイにはRaspberry Piの温度やIPアドレスなどの情報が表示されます。

??? note "**PoE**"
    - **規格:** IEEE 802.3af PoE
    - **入力電圧:** 37-57 V DC
    - **出力:** 5 V DC/2.4 A
    - PoE給電を使用するには、PoEジャンパーを短絡してください

??? note "**ファン**"
    GPIO12に接続され、Raspberry Piによりコントロールされる小さいファンが搭載されています

??? note "**リアルタイムクロック (RTC)**"
    I2Cに接続されRaspberry PiによりコントロールされるPCF8563チップです。ボタン電池の設置場所はHDMI INモジュールの下にあります。

## **アクセサリ**

### **ATXアダプタボード**

![Image title](assets/images/BLIKVM-HAT/ATX-A-B.png){width="300"}

このボードはコントロールされるコンピュータのマザーボード上のピンにデュポンケーブルで接続されます。このボードには標準のPCIe I/Oブラケットとロープロファイルのブラケットが付属しています。

### **USB/PWRスプリッタ**
![Image title](assets/images/BLIKVM-HAT/usb-spiltter.png){width="300"}

- RPI4ポートはRaspberry Pi 4へ接続します
- USBポートはコントロールされるコンピュータへ接続します
- PoE給電を利用する場合は、PWRポートは使用しません。PoE給電を利用しない場合は、PWRポートへRaspberry Pi標準の5V/3AのUSB電源を接続します

### **HDMIパススルーEDIDエミュレータ**

![Image title](assets/images/BLIKVM-HAT/edid-emulator.png){width="300"}

コントロールされるコンピュータが正常なHDMI信号を出力しないときにこのアクセサリを使ってください。Sourceポートをコントロールされるコンピュータへ、SinkポートをHATへ接続してください。コントロールされるコンピュータから正常なHDMI信号が出力されます。

### **金属ケース**

![Image title](assets/images/BLIKVM-HAT/metal-case.png){width="300"}  
この金属ケースはHATを保護して、熱耐性を向上させます。ケースには各ポートの名称が印字されています。
このケースは標準的な1Uラックにインストールできます。

## **部品一覧**

### **製品に付属する部品**
![Image title](assets/images/BLIKVM-HAT/product-list.png){width="300"}

| Raspberry Pi IPKVM HAT                 | 1    |
| -------------------------------------- | ---- |
| ATXアダプタボード                        | 1    |
| USB/PWRスプリッタ                        | 1    |
| HDMIパススルーEDIDエミュレータ             | 1    |
| 金属ケース                               | 1    |
| 32GB microSDカード                      | 1    |
| USB Type-C to USB Type-C ケーブル 30cm  | 1    |
| デュポンケーブル 8ピン メス-メス 40cm      | 1    |
| デュポンケーブル 8ピン メス-オス 40cm      | 1    |
| +ドライバー                             | 1    |
| 十字レンチ                             | 1    |

### **用意していただく部品**

| Raspberry Pi 4                              | 1    |
| ------------------------------------------- | ---- |
| RJ45 ネットワークケーブル                      | 2    |
| USB Type-A to USB Type-C ケーブル            | 2    |
| HDMI ケーブル                                | 1    |
| PoE対応電源装置または5V/3A USBアダプタ          | 1    |
| CR1220 ボタン電池                            | 1    |
