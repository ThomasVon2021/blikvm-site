# BLIKVMの概要
BLIKVMは3つのバリエーション(CM4ボード、Raspberry Pi HAT、PCIeボード)を持つオープンソースのKVMです。このデバイスはサーバーやワークステーションにインストールされているオペレーティングシステムに依存しないリモート管理環境を提供します。さまざま問題解決、BIOSの設定、さらにCD-ROMやフラッシュドライブのエミュレーションによりオペレーティングシステムのインストールも可能です。このサイトにはBLIKVMを使用するために必要な情報が記載されています。サポートやFAQ、最新情報などは[BLIKVM Discord コミュニティ](https://discord.com/invite/9Y374gUF6C)に参加してください。
![Image title](assets/images/version_all.png)

|FEATURE NAME|BliKVM CM4|BliKVM Pi4 HAT|BliKVM PCIe|BliKVM PCIe(PA)|PiKVM V3 HAT|PiKVM V3 HAT (PA)|TinyPilot Voyager 2|
 |-|-|-|-|-|-|-|-|
 |Cost (without tax + shipping)|99$|99$|111$|206$|160$|250$|400$|
 |Serial Console|No|Yes|Yes|Yes|Yes|Yes|No|
 |ATX controls|Yes|Yes|Yes|Yes|Yes|Yes|No|
 |FAN PWM controls|No|Yes|Yes|Yes|Yes|Yes|No|
 |OLED|128x64|128x32|128x64|128x64|128x32|128x32|No|
 |POE|No|Yes|Yes|Yes|No, but you can use poe splitter|No, but you can use poe splitter|No (optional $59)|
 |Real Time Clock (pcf8563)|ds1307|Yes|Yes|Yes|Yes|Yes|No|
 |USB Power/Data Splitter|Yes(built-in)|Yes (external)|Yes(built-in)|Yes(built-in)|Yes(built-in)|Yes(built-in)|Yes(built-in)|
 |TC358743 CSI Video capture|Yes|Yes|Yes|Yes|Yes|Yes| Yes|
 |Case|Yes (steel - black)|Yes (steel - blue and black)|No|No|No|Yes (steel - black)|Yes (3d print black)|
 |Dedicated software devs|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
 |Dedicated support|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
 |Pi4 or CM4 2GB Included|No|No|No|Yes|No|Yes|Yes|
 |32GB SD Card|No|Yes (OS included)|Yes (OS included)|Yes (OS included)|No|Yes (OS included)|Yes (OS included)|
 |HDMI backpower mitigation|No|Yes|Yes|Yes|Yes|Yes|No|
 |HDMI Passthru EDID dongle|No|Yes|Yes|Yes|No|No|No|
 
## **機能**
* ビデオキャプチャ (1080P 60Hz)  
* キーボード操作  
* マウス操作  
* ATX コントロール
* ファンコントロール  
* フルスクリーンモード  
* クリップボードからテキストの貼り付け  
* VPNサポート  
* マスストレージデバイス (CD-ROM/フラッシュドライブのエミュレーション)  
* マルチポート KVM over IP  
* OLED ディスプレイ (システム情報の表示 - 温度、起動時間、IPアドレス)
* パスワード認証  
* 多言語サポート  
* Wake-on-LAN  

## **ガイド**
[1.BLIKVM CM4 バージョン](./BLIKVM-CM4-guide.md)  
[2.BLIKVM HAT バージョン](./BLIKVM-HAT-guide.md)   
[3.BLIKVM PCIE バージョン](./BLIKVM-PCIE-guide.md)   

