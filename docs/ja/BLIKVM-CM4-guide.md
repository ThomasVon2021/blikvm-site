# BLIKVM CM4 バージョンガイド

!!! info "BLIKVM CM4 ビデオ"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/2av-JFFkF6I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## **インストール要件**
!!! note "組み立てキットの場合は、下記の部品が必要です"
    * Raspberry CM4 (1GB以上のRAM)
    * microSDカード (容量16GB以上、読み書き速度 class 10を推奨)
    * USB-C - USB-A ケーブル
    * HDMI ケーブル
    * RJ45 イーサネットケーブル (ATXアダプタボードとの接続に利用)
    * 電源 (5.1V 3A USB-C, Raspberry Pi対応電源を推奨).

!!! warning "電源供給に関して"
    必ずUSB-C - USB-Aケーブルを使ってください。USB-C - USB-Cケーブルでは動作しません。ハードウェアが対応していないためです。将来的に改善されるでしょう。

## **基本的なセットアップ**
**1.** [OSイメージの書き込み](./flashing_os.md) 

**2.BLIKVMの組み立て** ビデオの指示を確認してから指示通りに進めてください:

??? info "ビデオガイド: メタルケースの組み立て"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/aehOawHklGE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
??? info "Geerling: Engineering Test video"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/3OPd7svT3bE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  
??? info "Ortimo: BLIKVM with Raspberry PI CM4 16GB eMMC setup"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/xypeC7Fne6Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**3.** 下記の指示に従ってBLIKVMとコンピュータを接続してください:

![Image title](assets/images/blikcm-cm4-interface.png){width="400"}

* HDMI INとOTGポートをコンピュータに接続してください。CN-ATXは必須ではありません。利用する場合は後の指示に従って接続してください。起動時のUEFIやBIOSでUSBデバイスとして認識されない場合がありますので、BLIKVMのOTGポートとコンピュータの間にはUSBハブを介さないように接続することを推奨します。
BLIKVM は1080p60Hzまたはそれ以下のHDMI信号をサポートします。
* ETHERNETポートをネットワークに接続して、PWRポートに電源を接続してください。

## **ATX接続**
![Image title](assets/images/BLKVM-CM4/ATX-interface.png){width="400"}

コンピュータの電源を操作するには、CN-ATXポートとコンピュータを接続してください。コントロールされるコンピュータのマザーボード上のATXスイッチと付属のケーブルを繋いでください。
ATXケーブルの長さは60cmです。またはメスーメスのデュポンケーブルを使用できます。

![Image title](assets/images/BLKVM-CM4/atx-cable-computer.png){width="400"}

## **ハードウェア機能**
![Image title](assets/images/BLKVM-CM4/blikvm-cm4-hardware-features.png)

* 1、HDMI IN ポート(I2S対応)
* 2、ATX コントローラインターフェイス (電源ON/OFF、再起動、PWRおよびHDD ACTランプ)
* 3、USB3.0 x 2
* 4、USB-C OTG
* 5、リアルタイムクロック (RTC)
* 6、ギガビットイーサネット
* 7、アクティビティLED
* 8、microSDカードスロット
* 9、パワーLED
* 10、I2C ディスプレイコネクタ
* 11、nRPI_BOOT ジャンパー
* 12、USB-C 電源入力
* 13、ファンコネクタ 5V
* 14、CSI-2 データレーンスイッチ
* 15、CM4 モジュールコネクタ

## ** 1080p60Hz HDMI入力サポート **
V2.2ではCSIチャネルスイッチがあります。このスイッチはCSIのデータレーンサイズを2レーンまたは4レーンを切り替えます。
他のバージョンではスイッチは廃止されています。新しいものはものは製造時の設定を保持していますので、このスイッチは無視してください。もし、スイッチを操作する場合は、必ず電源を切った状態で操作してください。故障の原因となります。4つのスイッチのUp/Downはまとめて操作するようにしてください。

![Image title](assets/images/BLKVM-CM4/kvm-cm4-switch.png){width="400"}
Raspberry Piのビデオエンコード機能は、東芝のHDMI-CSIブリッジチップTC358743のCSI-2の4データレーンに対応しています。
Raspberry Pi 4BのカメラインターフェイスはCSI-2 2データレーンだけをサポートしています(最大 1080p 50Hz)。Raspberry Pi CM4では4データレーンをサポートしています(最大 1080p 60Hz)。現時点では、PiKVMは2データレーンだけ使っています。

1、 EDIDファイルの置き換え:
```
rw
vim /etc/kvmd/tc358743-edid.hex
```
下記の1080p 60Hzに対応したEDIDをtc358743-edid.hexへ書き込んでください。
```
00FFFFFFFFFFFF0031D8888800888888
1C150103800000780AEE91A3544C9926
0F50543FCD0001000101010101010101
010101010101011D007251D01E206E28
5500C48E2100001E8C0AD08A20E02D10
103E9600138E2100001E000000FC0050
694B564D0A20202020202020000000FD
003B3D0F2E0F1E0A202020202020013C
02031E434F041303021211012021A23C
3D3E1F1066030C00300080E2007F8C0A
D08A20E02D10103E9600C48E21000018
8C0AD08A20E02D10103E9600138E2100
00189729A0D051842230509816009A01
11000018000000000000000000000000
00000000000000000000000000000000
0000000000000000000000000000001C
```
2、4レーンの設定を追加してください
/boot/config.txtの"dtoverlay=tc358743"を"dtoverlay=tc358743,4lane=1"に書き換えてください。
```
vim /boot/config.txt
ro
```
そして、BLIKVMを再起動してから、1080p 60Hzの信号をお試しください。

![](https://github.com/blikvm/pikvm-CM4-Board/blob/main/images/wiki/60hz.jpg)  
