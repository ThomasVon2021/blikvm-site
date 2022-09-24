# BLIKVM PCIeガイド

## **はじめに**

![main1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_main1.png){width="500"}

BLIKVM PCIeはRaspberry Pi CM4を使ったKVM Over IPのためのPCIeカードです。この製品の主な機能は、ビデオキャプチャ、ATXコントローラ、PoE給電、OLEDディスプレイ、UARTそしてリアルタイムクロック(RTC)です。このカードにはPCIe標準のブラケットとロープロファイルのブラケットが付属します。現時点ではblikvmとpikvmの両方に互換性があります。

## **インストール要件**
!!! note "次のものを用意してください"
    * Raspberry Pi CM4(PCIeカードのみを購入した場合).
    * PoE給電装置または5V/3A USBアダプタ
    * CR1220 ボタン電池

## **基本設定**
**1.** 組み立てキットを購入した場合は、[microSDカードまたはeMMCにOSイメージを書き込んでください](./flashing_os.md)   
**2.BLIKVMの組み立て** [組み立てガイド]に従ってください(./BLIKVM-PCIe-installation.md):

??? info "Geerling: Engineering Test video"
<iframe width="560" height="315" src="https://www.youtube.com/embed/cVWF3u-y-Zg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## **仕様**
!!! note "ハードウェアの外観"
    ![BLIKVM_PCIe_main-define](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_main-define.png){width="300"}
    ![BLIKVM_PCIe_main-back](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_main-back.png){width="300"}

!!! note "**HDMI IN**"
    ビデオとオーディオ(I2S)のキャプチャをサポートする東芝のTC358743と言うチップを使用しています。そして、ビデオキャプチャの最大解像度は1080P 60fpsです。HDMIバックパワーによる問題は修正されています。

!!! note "**USB-PC**"
    製品には2つのUSB-PCポートがあります。USB-PCポートのどちらも利用できます。

!!! note "**POWER-IN**"
    PoE給電を利用する場合は、PWR-INポートは接続する必要はありません。PoE給電を利用しない場合は、PWR-INポートに標準の5V/3AのUSB電源を接続してください。

!!! note "**ETHERNET-PoE**"
    - ギガビットイーサネットポート
    - **規格:** IEEE 802.3af PoE
    - **入力電圧:** 37-57 V DC
    - **出力:** 5 V DC/2.4 A

!!! note "**ATX-Connecter**"
    コントロールされるコンピュータのマザーボード上の電源コントロールにデュポンケーブで接続します。コンピュータの電源ON/OFFやリセットの操作を行えます。

!!! note "**OLED Display**"
    SSD1306チップを載せた解像度128x64の白色OLEDディスプレイです。Raspberry Piの温度、IPアドレスなどの情報が表示されます。

!!! note "**FAN**"
    Raspberry Pi CM4のGPIO12に接続されコントロールされているファンを接続できます。

!!! note "**BOOT**"
    eMMCブートを無効にするためのジャンパーです。

!!! note "**Real Time Clock (RTC)**"
    クロックチップはRaspberry Pi CM4のI2Cに接続されたPCF8563です。HDMI INモジュール下にCR1220ボタン電池をセットします。

!!! note "**UART**"
    Raspberry Pi CM4をデバッグするために利用します。

## **アクセサリ**

![BLIKVM_PCIe_main-back](assets/images/BLIKVM-PCIe/accessories.png){width="400"}
!!! note "**HDMIパススルーEDIDエミュレータ**"
    コントロールされるコンピュータが正常なHDMI信号を出力しないときにこのアクセサリを使ってください。Sourceポートをコントロールされるコンピュータへ、SinkポートをHATへ接続してください。コントロールされるコンピュータから正常なHDMI信号が出力されます。

!!! note "**VGA-HDMIモジュール**"
    コンピュータにHDMIポートがない場合に、VGA-HDMI変換モジュールを使用してください。

!!! note "**USB to TTL モジュール**"
    Raspberry Pi CM4をデバッグするために、PCのUSBとBLIKVMのUARTを接続してください。

!!! note "**ファン**"
    Raspberry Pi CM4を冷やすための冷却ファンです。ただし、組み込むファンは標準PCIeカードの厚さを超えないものを使用してください。

## **寸法**

![dimension1](assets/images/BLIKVM-PCIe/dimension.png){width="400"}

## **テストビデオ**
??? info "BLIKVM PCIeバージョンは、pikvmでテストされています"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/0SEGeLFV-Wk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## **部品一覧**

### 製品に含まれる部品

| BLIKVM PCIe カードバージョン              | 1    |
| -------------------------------------- | ---- |
| BLIKVM PCIe カード                      | 1    |
| 冷却ファン                               | 1    |
| OLED ディスプレイ                        | 1    |
| USB - TTLモジュール                      | 1    |
| HDMIパススルーEDIDエミュレータ             | 1    |
| VGA-HDMIモジュール                       | 1    |
| 32GB microSDカード                      | 1    |
| HDMI ケーブル 0.5m                      | 1    |
| HDMI カプラ                             | 1    |
| ネットワークケーブル 1m                   | 1    |
| USB-A - USB-C ケーブル 1m               | 2    |
| デュポンUSBケーブル 0.4m                 | 1    |
| WiFi アンテナ                           | 1    |
| デュポンケーブル 8ピン メス-メス 40cm      | 1    |
| デュポンケーブル 8ピン メス-オス 40cm      | 1    |
| ヒートシンク                            | 1    |
| +ドライバー                             | 1    |
| 十字レンチ                              | 1    |

| BLIKVM PCIe プラグアンドプレイバージョン　  | 1    |
| -------------------------------------- | ---- |
| BLIKVM PCIe カード                      | 1    |
| Raspberry Pi CM4 102000                | 1    |
| 冷却ファン                               | 1    |
| OLED ディスプレイ                        | 1    |
| USB - TTL モジュール                     | 1    |
| HDMIパススルーEDIDエミュレ ータ            | 1    |
| VGA-HDMI モジュール                      | 1    |
| 32GB microSDカード                      | 1    |
| HDMI ケーブル 0.5m                      | 1    |
| HDMI カプラ                             | 1    |
| ネットワークケーブル 1m                   | 1    |
| USB-A - USB-C ケーブル 1m                | 2    |
| デュポン USBケーブル 0.4m                 | 1    |
| WiFi アンテナ                           | 1    |
| デュポンケーブル 8ピン メス-メス 40cm      | 1    |
| デュポンケーブル 8ピン メス-オス 40cm      | 1    |
| ヒートシンク                            | 1    |
| +ドライバー                             | 1    |
| 十字レンチ                              | 1    |

### 用意していただく部品

| Raspberry Pi CM4(PCIeカードのみを購入した場合)| 1    |
| -------------------------------------------- | ---- |
| PoE対応電源装置または5V/3A USBアダプタ          | 1    |
| CR1220 ボタン電池                            | 1    |
