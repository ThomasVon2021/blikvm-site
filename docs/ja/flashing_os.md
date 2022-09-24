# OSイメージの書き込み

!!! warning "microSDカード 動作要件"
    * 容量**16 GB** 以上
    * 読み書き速度は **Class 10** を推奨

## イメージのダウンロード

* **[PiKVM image (BLIKVM-CM4)](https://drive.google.com/file/d/1wBeygdHefMrdtQUCm6dKgQg1b8D4yIhk/view?usp=sharing)**
* **[PiKVM image (BLIKVM-PCIe)](https://drive.google.com/file/d/1lsZRhSrK3w_OE7MG1ycY6YeiT3jfJS4A/view?usp=sharing)**
* **[PiKVM image (BLIKVM-HAT)](https://mgk9cjip0o.feishu.cn/file/boxcnYAhGhLxaEVOQdSrNiD1Pbg?from=from_copylink)**

## イメージの書き込み

!!! tip
    このステップではmicroSDカードのフォーマットは必要ありません。 利用環境に合わせた方法を参照してください。
    [How to flash the eMMC on a Raspberry Pi Compute Module 4](https://www.youtube.com/watch?v=jp_mF1RknU4)

### ボードの接続
まずはじめに、Boot Pinのジャンパーをショートしてください。
!!! info "BLIKVM CM4 バージョンの場合"
    USB-OTGコネクタとPCをデータケーブルで接続します。電源をオンにするとACTランプが緑に点灯します。

    ![Image title](assets/images/flash_os/flash_led-300x300.png){width="300"}

!!! info "BLIKVM PCIe バージョンの場合"
    USB-PCコネクタとPCをデータケーブルで接続します。電源をオンにした後はACTおよびPWRランプは点灯しません。
    usbbootまたはpribootでeMMCを初期化すると、ACTおよびPWRランプが点灯します。

    ![Image title](assets/images/flash_os/pcie-flash-boot.jpg){width="300"}
    ![Image title](assets/images/flash_os/pcie_flash_after_rpiboot.jpg){width="300"}

!!! tip "eMMCに関して"
    eMMCを搭載したCM3またはCM4のようなRaspberry Pi Compute Moduleを使用する場合は、usbbootからeMMCを初期化できます。
    eMMCバージョンはmicroSDカードから直接起動できませんのでご注意ください。
    この映像でイメージの書き込み手順を見ることができます。[How to flash the eMMC on a Raspberry Pi Compute Module 4 video](https://www.youtube.com/watch?v=jp_mF1RknU4)

**Ubuntu環境での例です:**
###  Linux usbboot
microSDカードを利用する場合は、この手順は必要ありません。
```
# sudo apt-get install libusb-1.0-0-dev
# git clone --depth=1 https://github.com/raspberrypi/usbboot
# cd usbboot
# make
# sudo ./rpiboot
```
eMMCの初期化に成功すると、下記のように表示されます。

![Image title](assets/images/flash_os/flash_rpiboot.png){width="300"}

### RPi Imagerを利用する (Linux, MacOS and Windows)

1. **最新バージョン** の[RPi Imager](https://github.com/raspberrypi/rpi-imager/releases)をダウンロードしてからインストールしてください

2. RPi Imagerを起動します

![Image title](assets/images/flash_os/flash_rpi.png){width="300"}

3. **CHOOSE OS**をクリックして、リストの最後にある**Use custom**を選択してください

![Image title](assets/images/flash_os/flash_choose_os.png){width="300"}

4. それをクリックして、イメージファイル(`.img.xz`)を選択してください。その後に**CHOOSE STORAGE**をクリックしてください

![Image title](assets/images/flash_os/flash_img.png){width="300"}

5. microSDカードをカードリーダーに挿入して、リストからカードリーダーを選択してください。正しいカードリーダーを選択できているかよく確認してください

![Image title](assets/images/flash_os/flash_storage.png){width="300"}

6. microSDカードの選択が済んだら、**WRITE**ボタンをクリックしてください。操作の確認が表示されるので、宜しければ操作を進めてください。

![Image title](assets/images/flash_os/flash_write.png){width="300"}

7. コーヒーを飲んだり、ストレッチをしながら処理が完了するまで待ちましょう :)

!!! tip
    進行状況99％から長く止まったように見える場合がありますが問題ありません。そのまま処理の完了を待ってください。
    ![Image title](assets/images/flash_os/flash_wait_process.png){width="300"}

8. 完了したらmicroSDカードを抜いてください

![Image title](assets/images/flash_os/flash_write_successful.png){width="300"}

!!! tip
    もし、書き込みやPiKVMの起動に失敗した場合は、このプロセスをもう一度試してみてください。

