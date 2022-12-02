# HDMI-CSI&I2Sブリッジ ガイド
> HDMI信号をCSIとI2Sオーディオに変換します

## **はじめに**
このモジュールは入力されたHDMI信号をCSIとI2Sオーディオに変換します。1080p 60HzのHDMI信号をサポートします。Raspberry Piで動作し、これまで3つのバリエーション(C779, C780, C790)があります。最新版はC790です。C790はHDMIバックパワー問題を解消し、2種のCSIコネクタを持ち4チャンネルに対応します。
![](assets/images/hdmi-csi-i2s/c790.png)

## **機能**
### **C790**
!!! note "ハードウェア仕様"
    * HDMI入力: 最大1080P60Hz(Raspberry Piの場合)
    * HDMI-CSI-2ブリッジチップ:Toshiba TC358743XBG
    * 4 CSI-2 チャンネル
    * CSI-2インターフェイス: 1mm幅15ピンFCPケーブル、C790の表に実装
    * The CSI-2 interface, 0.5mm幅22ピンFPCケーブル、C790の裏に実装
    * 寸法: 30 x 45 mm
    * 設置に使用する部品: 4 x M2.5
    * 入力電圧:3.3V
    * 重量: 10g

!!! note "インターフェイス"
    ![](assets/images/hdmi-csi-i2s/c790-interface.png){width="400"}  
    C790は2つのCSI出力インターフェイスを持ちます。C890の表のCSI-2インターフェイスは1mm幅の15ピンFPCケーブル用です。裏のCSI-2インターフェイスは0.5mm幅の22ピンFPCケーブル用です。
    ![](assets/images/hdmi-csi-i2s/c790-i2s-connect.png){width="400"}  

!!! note "寸法"
    ![](assets/images/hdmi-csi-i2s/c790-size.png){width="400"}  

### **C780**
??? info "C780A ハードウェア仕様"
    * HDMI入力: 1080P50Hz(Raspberry Piの場合、CSI-2のチャンネル数により制限されています)
    * HDMI-CSI-2ブリッジチップ: Toshiba TC358743XBG
    * 2 CSI-2 チャンネル
    * CSI-2 インターフェイス: 1.0mm幅15ピンFPCケーブル
    * 寸法: 30 x 65 mm (切り離し前); 30 x 45 mm (切り離し後)
    * 設置に使用する部品: 6 x M2.5
    * 入力電圧:3.3V
    * 重量: 10g
??? info "C780B ハードウェア仕様"
    * HDMI入力: 1080P60Hz(Raspberry Piの場合)
    * HDMI-CSI-2ブリッジチップ: Toshiba TC358743XBG
    * 4 CSI-2 チャンネル
    * CSI-2 インターフェイス: 0.5mm幅22ピンFPCケーブル
    * 寸法: 30 x 65 mm (切り離し前); 30 x 45 mm (切り離し後)
    * 設置に使用する部品: 6 x M2.5
    * 入力電圧:3.3V
    * 重量: 10g
??? info "インターフェイス"
    ![](assets/images/hdmi-csi-i2s/2-4.png){width="400"}  

    オーディオのピン配列は下記の図を参照ください。

    ![](assets/images/hdmi-csi-i2s/2-8.png){width="400"}

??? info "寸法"
    C780の寸法は数の通りです。2.75mm径の穴が6つあり、M2.5のネジを使用できます。
    ![](assets/images/hdmi-csi-i2s/2-1.png){width="400"}  
    次の図のようにRaspberry Pi Zeroに直接固定できます。そして、基板を切り離すことにより、他のほとんどのRaspberry Piにより設置しやすくなります。
    
    ![](assets/images/hdmi-csi-i2s/2-2.png){width="400"}

### **C779**
??? info "ハードウェア仕様"
    * HDMI入力: 1080P50Hz(Raspberry Piの場合、CSI-2のチャンネル数により制限されています)
    * HDMI-CSI-2ブリッジチップ: Toshiba TC358743XBG
    * 2 CSI-2 チャンネル
    * CSI-2 インターフェイス: 1.0mm幅15ピンFPCケーブル
    * 寸法: 35 x 50 mm 
    * 設置に使用する部品:4 x M2.5
    * 入力電圧:3.3V
    * 重量: 10g

??? info "寸法"
    C779の寸法は数の通りです。2.75mm径の穴が4つあり、M2.5のネジを使用できます。
    ![](assets/images/hdmi-csi-i2s/c779-size.png){width="400"}  

## **ソフトウェアデモ**
ここで紹介するのは公式のRaspberry Pi OSでのC790/C780/C779の使い方です。バージョンが異なる場合は使用方法が異なる場合があります。もし、質問がある場合は[BLIKVM Discord 
コミュニティ](https://discord.com/invite/9Y374gUF6C)に参加してください。
カーネルドライバを利用するために、Raspberry Pi OSは最新の状態にアップデートしてください。Linuxカーネル V5.4以降に幾つかの変更が行われており、ここで説明する使用方法はそれ以降のバージョンに対応しています。“uname -a”コマンドで確認して5.4以前の状態でしたら、実行する前にアップデートを行なってください。
``` 
pi@raspberrypi:~ $ uname -a
Linux raspberrypi 5.10.63-v7l+ #1459 SMP Wed Oct 6 16:41:57 BST 2021 armv7l GNU/Linux
```

!!! note "1. Raspberry Piシステムのアップデートとアップグレード(国によっては時間がかかる可能性があります)"
    ``` 
    sudo apt-get update
    sudo apt-get upgrade
    ``` 
!!! note "2. カメラモジュールを有効化(Raspberry Pi OS(Bullseye)ではデフォルトで有効化されています)"
    ```
    sudo raspi-config
    sudo reboot
    ```
    ‘Interfacing Options’へ進み、‘Camera’オプションを選択して有効にしください。“Finish”を行なってからRaspberry Piを再起動してください。**忘れずに再起動してください!!**
!!! note "3. /boot/config.txtの編集 (sudoが必要です)
    ```
    sudo nano /boot/config.txt
    ```
    この行を追加:
    ```
    dtoverlay=tc358743
    ```
    C780,C790のようにオーディオをサポートしてる場合はこの行を追加
    ```
    dtoverlay=tc358743-audio
    ```
    C780やC790のように4データレーンに対応した22ピンコネクタを持つデバイスをRaspberry Pi Compute ModuleのCAM1に接続して使用する場合には、この行を追加すると4データレーンを使用できます:
    ```
    dtoverlay=tc358743,4lane=1
    ```
!!! note "4. “dmesg | grep cma”コマンドを実行してCMAヒープに割り当てられたメモリを確認してください。最初の行が下記のようになっているかを確認:"
    ```
    pi@raspberrypi:~ $ dmesg | grep cma
    [0.000000] cma: Reserved 256 MiB at 0x000000001ec00000
    ```
    もし、割り当てられたメモリが96MBよりも少ない場合には、/boot/cmdline.txtへ下記の設定を追加してください。途中で改行を行わないように注意してください。
    ```
    cma=96M
    ```
!!! note "5. 再起動。設定が成功していると、/dev/video0というデバイスファイルが生成されます。そして、“v4l2-ctl –list-devices”コマンドを実行すると、Unicamというデバイスが確認できるはずです。全てのケーブルを接続してから、Raspberry Piの電源をオンにすると、通常であればC790は緑色のLEDが点灯します。そして、Raspberry Piのターミナルからこれらのコマンドを実行できます:"
    ```
    pi@raspberrypi:~ $ ls /dev/video0
    /dev/video0
    pi@raspberrypi:~ $ v4l2-ctl --list-devices
    bcm2835-codec-decode (platform:bcm2835-codec):
        /dev/video10
        /dev/video11
        /dev/video12
        /dev/video18
        /dev/media1
    bcm2835-isp (platform:bcm2835-isp):
        /dev/video13
        /dev/video14
        /dev/video15
        /dev/video16
        /dev/media0
    unicam (platform:fe801000.csi):
        /dev/video0
        /dev/video1
        /dev/media2
    ```
!!! note "6. このドライバはユーザーまたはアプリケーションによりコントロールされています。デフォルトではサポートするHDMI信号を決めるためのEDIDはチップには設定されていませんEDIDエディタなどでEDIDファイル(edid.txt)を作成して、デバイスに設定できます。"
    edid.txtの例:
    ```
    00ffffffffffff005262888800888888
    1c150103800000780aEE91A3544C9926
    0F505400000001010101010101010101
    010101010101011d007251d01e206e28
    5500c48e2100001e8c0ad08a20e02d10
    103e9600138e2100001e000000fc0054
    6f73686962612d4832430a20000000FD
    003b3d0f2e0f1e0a2020202020200100
    020321434e041303021211012021a23c
    3d3e1f2309070766030c00300080E300
    7F8c0ad08a20e02d10103e9600c48e21
    0000188c0ad08a20e02d10103e960013
    8e210000188c0aa01451f01600267c43
    00138e21000098000000000000000000
    00000000000000000000000000000000
    00000000000000000000000000000000
    ```
    ```
    cd ~
    sudo nano edid.txt
    #上記の例をコピーして保存、終了してください
    pi@raspberrypi:~ $ v4l2-ctl --set-edid=file=edid.txt --fix-edid-checksums
    
    CTA-861 Header
      IT Formats Underscanned: yes
      Audio:                   yes
      YCbCr 4:4:4:             no
      YCbCr 4:2:2:             no
    
    HDMI Vendor-Specific Data Block
      Physical Address:        3.0.0.0
      YCbCr 4:4:4 Deep Color:  no
      30-bit:                  no
      36-bit:                  no
      48-bit:                  no
    
    CTA-861 Video Capability Descriptor
      RGB Quantization Range:  yes
      YCC Quantization Range:  no
      PT:                      Supports both over- and underscan
      IT:                      Supports both over- and underscan
      CE:                      Supports both over- and underscan
    ```
!!! note "7. ドライバは自動的に信号検出を行いません。下記のコマンドを実行してください:"
    ```
    pi@raspberrypi:~ $ v4l2-ctl --query-dv-timings
	Active width: 1280
	Active height: 720
	Total width: 1650
	Total height: 750
	Frame format: progressive
	Polarities: -vsync -hsync
	Pixelclock: 74250000 Hz (60.00 frames per second)
	Horizontal frontporch: 0
	Horizontal sync: 370
	Horizontal backporch: 0
	Vertical frontporch: 0
	Vertical sync: 30
	Vertical backporch: 0
	Standards: 
	Flags: 
    ```
    “v4l2-ctl –set-dv-bt-timings”コマンドを実行してタイミングを設定する必要があります。You MUST set the timings via “v4l2-ctl –set-dv-bt-timings”. 検出されたモードのインデックスを指定するか、下記のコマンドを実行します:
    ```
    v4l2-ctl --set-dv-bt-timings query
    ```
    検出されたタイミングが選択されます
    ```
    v4l2-ctl -V
    ```
    検出された解像度が反映されているはずです。

!!! note "8. このチップは2つのフォーマットをサポートしています。BGR3(デフォルト)とUYVY. BGR3は24bppで、UYVYはYUV4:2:2 16bppです"
    CSI-2 2データレーンで使用する場合には、BGR3は最大 1080p30Hz、UYVYは1080p50Hzを使用できます。下記のコマンドでUYVYを選択できます。しかしながら、この設定はアプリケーションが上書きする場合があります。
    ```
    v4l2-ctl -v pixelformat=UYVY
    ```
!!! note "9. オーディオドライバの確認 / ALSAで利用できます"
    ```
    pi@raspberrypi:~ $ arecord -l
    **** List of CAPTURE Hardware Devices ****
    card 1: tc358743 [tc358743], device 0: bcm2835-i2s-dir-hifi dir-hifi-0 [bcm2835-i2s-dir-hifi dir-hifi-0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    ```
    Note: card 1はTC358743XBGのカード番号が"1"であるという意味です。ただじ、状況によって番号が変わる場合があります。

!!! note "10. GStreamerのインストール"
    ```
    sudo apt install gstreamer1.0-tools
    ```
    gstreamer toolのバージョンを確認:
    ```
    pi@raspberrypi:~ $ gst-launch-1.0 --version
    gst-launch-1.0 version 1.18.4
    GStreamer 1.18.4
    http://packages.qa.debian.org/gstreamer1.0
    ```
    Note:
    バージョンが異なるとコマンドラインの引数が変わる場合があります。ご注意ください。

!!! note "11. gstreamerを使いビデオとオーディオ合わせてを録画する"
    ```
    #GStreamer v1.14 command
    gst-launch-1.0 v4l2src io-mode=5 ! video/x-raw, format=UYVY, framerate=25/1 ! v4l2h264enc output-io-mode=4 ! video/x-h264,profile=high ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    ```
    出力されるファイルはfoo.mkvです。もし、gstreamerのバージョンが1.8以降なら次のコマンドを試してみてください。そして、’alsasrc 
    device=hw:1’はTC358743のカード番号を示しています。“arecord -l”コマンドで確認してください。
    ```
    #The command to recode a video with audio. (GStreamer 1.18.4)
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=30/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    #The sample command to recode a video without audio. (C779 doesn't support audio)
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=30/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv
    Press CTRL+C to end recording.
    ```
    PS: 実際のHDMI入力信号に合わせて、上記コマンド例のパラメータを変更することを推奨します。フレームレートは‘v4l2-ctl –query-dv-timings’コマンドの結果から取得できます。

    ![Image title](assets/images/hdmi-csi-i2s/v4l2-rate.png){width="400"}

    上記のHDMIデバイスの例ではフレームレートは60fpsなので、次のコマンドのようにパラメータを変更します。コマンドはビデオのみ録画します:
    ```
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=60/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv
    ```
    オーディオと共にビデオを録画します: (ボードがオーディオをサポートしている場合)
    ```
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=60/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    ```
    Note: alsasrc device=hw:1 – “1”はカード番号を示しています。正しいカード番号を設定してください。
    (‘arecord –l’で確認できます。ステップ9を参照してください)

## **パックリスト**
??? info "C790"
    ![](assets/images/hdmi-csi-i2s/c790-packing-list.png){width="400"}

## **テストビデオ**
C780A テスト : https://www.youtube.com/watch?v=ecqyINoiHNQ

C780B テスト : https://www.youtube.com/watch?v=nc-hwPT2Uak&t=15s

## **リンク**
購入：<a href="https://www.aliexpress.com/item/1005002861310912.html?pdp_ext_f=%7B%22sku_id%22:%2212000022635165947%22,%22ship_from%22:%22CN%22%7D&gps-id=pcStoreJustForYou&scm=1007.23125.137358.0&scm_id=1007.23125.137358.0&scm-url=1007.23125.137358.0&pvid=8e29d7e9-f257-4f20-a0b2-c2bff6a048d6&spm=a2g0o.store_pc_home.smartJustForYou_6000897758043.1" target="_blank">C790 & C780</a>

購入：<a href="https://www.aliexpress.com/item/1005003033156483.html?spm=a2g0o.productlist.0.0.36f93cc2DFaouV&algo_pvid=2bfab2d1-a9c7-4c29-9434-2f451401d0e1&algo_exp_id=2bfab2d1-a9c7-4c29-9434-2f451401d0e1-9&pdp_ext_f=%7B%22sku_id%22%3A%2212000023351081819%22%7D" target="_blank">C779</a>
