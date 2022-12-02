# OLEDディスプレイ
!!! abstract "OLEDディスプレイを使用するには、下記の操作を行ってください"
    PiKVMのイメージを使用している場合には、PiKVMにログインしてから下記のコマンドを実行してください。
    ```
    # rw
    # systemctl enable --now kvmd-oled //Enable OLED
    # ro
    ```
!!! info "BLIKVM CM4バージョンのOLEDディスプレイ"
    製品には128x64の解像度を持つモノクロOLEDディスプレイが組み込まれています。これはSSD1360と言うチップを使用しています。
    ディスプレイはケーブルを使用して接続されています。

    ![Image title](assets/images/oled/BLIKVM-CM4-oled.png){width="300"}

    このモジュールはI2Cインターフェイスを介してCM4に接続されています。ケーブルは下記の表のように接続されています。
    このモノクロOLEDディスプレイのためのライブラリを使用しています。[SSD1306 drivers.](https://github.com/adafruit/Adafruit_SSD1306)

    | ディスプレイ(SSD1306) | CM4               |
    | ---------------- | ----------------- |
    | GND              | GND               |
    | VCC              | 3.3V              |
    | SCL              | GPIO3(SCL1,I2C) |
    | SDA              | GPIO2(SDA1,I2C) |

