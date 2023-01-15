# HDMI转CSI&I2S模块手册
> 将HDMI信号转换成CSI视频信号和I2S音频信号.
## **简介**
此模块将HDMI信号转换成CSI视频信号和I2S音频信号，最高支持1080P60Hz的视频输入，在树莓派上工作的很好，目前共有3个版本(C779、C780、C790).
C790是目前最新的版本，解决了所有已知的问题，同是有CSI 2通道和4通道接口，I2S音频接口，修复了HDMI反向供电问题。
![](assets/images/hdmi-csi-i2s/c790.png)

## **性能参数**
### **C790**
!!! note "硬件参数"
    * HDMI输入: 在树莓派上此模块最高支持1080P60Hz输入；
    * HDMI转CSI-2桥接芯片:Toshiba TC358743XBG
    * 4路CSI-2通道和时钟
    * CSI-2接口1: 15 pin FPC, 间距1.0 mm, 在C790模块的正面.
    * CSI-2接口2, 22 pin FPC, 间距0.5 mm, 在C790模块的背面.
    * 尺寸: 30 x 45 mm
    * 安装孔位:4 x M2.5
    * 供电电压:3.3V
    * 重量: 10g

!!! warning "树莓派4B只支持1080P50Hz(因为4B只有两个CSI-2通道) ,树莓派CM4只支持1080P60Hz,所以如果你的输入设备一定要是1080P60Hz，请同时使用CM4和C790."

!!! note "接口"
    ![](assets/images/hdmi-csi-i2s/c790-interface.png){width="400"}  
    C790有两个CSI输出接口: 接口1，在C790正面，15 pin FPC, 间距1.0 mm;
    接口1，在C790背面,22 pin FPC, 间距0.5 mm。
    ![](assets/images/hdmi-csi-i2s/c790-i2s-connect.png){width="400"}  

!!! note "尺寸"
    ![](assets/images/hdmi-csi-i2s/c790-size.png){width="400"}  

### **C780**
??? info "C780A硬件参数"
    * HDMI输入: 最高支持080P50Hz在树莓派上；
    * HDMI转CSI-2桥接芯片:Toshiba TC358743XBG；
    * 2路CSI-2通道和时钟；
    * CSI-2接口: 15 pin FPC, 间距 1.0 mm；
    * 尺寸: 30 x 65 mm (折断前); 30 x 45 mm (折断后)
    * 安装孔位:6 x M2.5
    * 供电电压:3.3V
    * 重量: 10g
??? info "C780B硬件参数"
    * HDMI输入: 最高支持080P60Hz在树莓派上；
    * HDMI转CSI-2桥接芯片:Toshiba TC358743XBG；
    * 4路CSI-2通道和时钟；
    * CSI-2接口: 22 pin FPC, 间距 0.5 mm；
    * 尺寸: 30 x 65 mm (折断前); 30 x 45 mm (折断后)
    * 安装孔位:6 x M2.5
    * 供电电压:3.3V
    * 重量: 10g
??? info "接口"
    ![](assets/images/hdmi-csi-i2s/2-4.png){width="400"}  
    音频引脚定义如下图所示:
    ![](assets/images/hdmi-csi-i2s/2-8.png){width="400"}
??? info "尺寸"
    尺寸如下图所示. 有6个直径为2。75mm的孔位用于安装，安装螺钉可以选择M2.5。
    ![](assets/images/hdmi-csi-i2s/2-1.png){width="400"}  
    如下图所示，C780被设计成可折断式的，C780模块在未被折断前可以完美的安装在zero上。
    ![](assets/images/hdmi-csi-i2s/2-2.png){width="400"}

### **C779**
??? info "硬件参数"
    * HDMI输入: 最高支持080P50Hz在树莓派上；
    * HDMI转CSI-2桥接芯片:Toshiba TC358743XBG；
    * 2路CSI-2通道和时钟；
    * CSI-2接口: 15 pin FPC, 间距 1.0 mm；
    * 尺寸: 35 x 50 mm 
    * 安装孔位:4 x M2.5
    * 供电电压:3.3V
    * 重量: 10g

??? info "尺寸"
    尺寸如下图所示. 有4个直径为2。75mm的孔位用于安装，安装螺钉可以选择M2.5。
    ![](assets/images/hdmi-csi-i2s/c779-size.png){width="400"}  

## **软件使用demo**
下文中的软件使用方法跟你使用的树莓派镜像版本有关，可能存在不同。如果你有任何疑问，请加入
[BLIKVM Discord 社区](https://discord.com/invite/9Y374gUF6C)获得支持、解答和新闻。 
以下说明适用于内核为5.4或者更高版本。如果你的树莓派镜像低于此版本，请升级。终端使用使用“uname-a”可以查看你系统的内核版本。
``` 
pi@raspberrypi:~ $ uname -a
Linux raspberrypi 5.10.63-v7l+ #1459 SMP Wed Oct 6 16:41:57 BST 2021 armv7l GNU/Linux
```
!!! note "1. 使用下列命令进行升级 (不是必须的，在某些国家这个花费的时间可能很长)"
    ``` 
    sudo apt-get update
    sudo apt-get upgrade
    ``` 
!!! note "2. 使能相机模块(在树莓派Bullseys OS系统中，相机已默认被使能)"
    ```
    sudo raspi-config
    sudo reboot
    ```
    移动光标到‘Interfacing Options’，然后按Enter键进入。然后选择‘Camera’选项，按Enter键进入后，使能相机。然后选择“Finish”后，
    选择“reboot”。**重启非常终于!!**

!!! note "3. 编辑 /boot/config.txt (需要sudo权限)"
    ```
    sudo nano /boot/config.txt
    ```
    添加下面的内容
    ```
    dtoverlay=tc358743
    ```
    如果你的模块(C780和C790)支持声音，添加下面内容支持声音
    ```
    dtoverlay=tc358743-audio
    ```
    如果你是用树莓派计算模组(CM3、CM4)，可以通过下列配置，使能CSI的4个通道。
    ```
    dtoverlay=tc358743,4lane=1
    ```
!!! note "4. 使用“dmesg | grep cma”检查分配给CMA堆的内存量，终端出现的第一行内容应该如下所示"
    ```
    pi@raspberrypi:~ $ dmesg | grep cma
    [0.000000] cma: Reserved 256 MiB at 0x000000001ec00000
    ```
    如果显示少于96MB，编辑/boot/cmdline.txt，添加下面一行。
    ```
    cma=96M
    ```
!!! note "5. 重启树莓派，如果配置成功，你将会看到/dev/video0设备描述符出现。可以使用“v4l2-ctl –list-devices” 命令列出所有的video描述符。再将树莓派与模块正确连接后，树莓派上电，你可以看到C790模块上有一个绿色灯常亮，然后可以按照下面的命令，检查是否已经正常出现了video0。"
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
!!! note "6. 默认没有加载EDID,如果你有EDID编辑器，你可以自己编辑你所需要的分辨率，或者使用下面提供的EDID分辨率（720p60hz）。"
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
    # 拷贝上门的内容到edid.txt文件中，然后保存退出。使用下列命令设置加载edid，如果正确设置，可以看到如下的输出。
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
!!! note "7. 驱动程序不会自动切换到检测到的分辨率。是用下列命令检查目前HDMI的输入"
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
    你必须使用“v4l2-ctl –set-dv-bt-timings”命令设置驱动程序使用目前的输入分辨率
    ```
    v4l2-ctl --set-dv-bt-timings query
    ```
    to select the currently detected timings.
    ```
    v4l2-ctl -V
    ```
    should now reflect the resolution detected.

!!! note "8. 芯片支持两种格式(BGR3和UYVY)，BGR3像素深度为24bpp，UYVY为YUV4:2:2 16bpp。如果使用CSI 2通道，BGR3格式最大支持1080P30Hz的输入，使用UYVY则最大支持1080P60Hz的输入。使用下面命令设置为UYVY格式。
    ```
    v4l2-ctl -v pixelformat=UYVY
    ```
!!! note "9. 使用下列命令，检查音频硬件和驱动是否正常"
    ```
    pi@raspberrypi:~ $ arecord -l
    **** List of CAPTURE Hardware Devices ****
    card 1: tc358743 [tc358743], device 0: bcm2835-i2s-dir-hifi dir-hifi-0 [bcm2835-i2s-dir-hifi dir-hifi-0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    ```
    Note: card 1: tc358743意味着音频相关硬件已被正确加载，注意这里的1可能不同。

!!! note "10. 安装GStreamer工具."
    ```
    sudo apt install gstreamer1.0-tools
    ```
    检查gstreamer工具版本:
    ```
    pi@raspberrypi:~ $ gst-launch-1.0 --version
    gst-launch-1.0 version 1.18.4
    GStreamer 1.18.4
    http://packages.qa.debian.org/gstreamer1.0
    ```
    Note:不同的版本这里输出可能不同.

!!! note "11. 使用gstreamer去录制视频或者声音"
    ```
    #GStreamer v1.14 command
    gst-launch-1.0 v4l2src io-mode=5 ! video/x-raw, format=UYVY, framerate=25/1 ! v4l2h264enc output-io-mode=4 ! video/x-h264,profile=high ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    ```
    你会得到一个foo.mkv文件.
    如果你的gstreamer是1.8或者更高版本，可以尝试使用下列命令。其中device=hw:1表示的是TC358743声卡。
    ```
    #The command to recode a video with audio. (GStreamer 1.18.4)
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=30/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    #The sample command to recode a video without audio. (C779 doesn't support audio)
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=30/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv
    Press CTRL+C to end recording.
    ```
    PS: 这里我们建议你使用实际的输入帧率去采集HDMI信号。你可以使用 ‘v4l2-ctl –query-dv-timings’去检查实际输入帧率。
    ![Image title](assets/images/hdmi-csi-i2s/v4l2-rate.png){width="400"}  
    
    如上图中的HDMI输入设备，帧率是60Hz，所以我们可以使用下面命令去录制视频：
    ```
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=60/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv
    ```
    录制视频和音频: (如果你的设备支持音频的话)
    ```
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=60/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    ```
    Note: alsasrc device=hw:1 – “1” means the audio card number, You must change to correct audio card number.
    (Query the car number via ‘arecord –l’, refer to step 9)

## **发货清单**
??? info "C790"
    ![](assets/images/hdmi-csi-i2s/c790-packing-list.png){width="400"}

## **测试视频**
C780A 测试:https://www.youtube.com/watch?v=ecqyINoiHNQ

C780B 测试:https://www.youtube.com/watch?v=nc-hwPT2Uak&t=15s

## **采购连接**
中国客户采购链接：<a href="https://www.aliexpress.com/item/1005002861310912.html?pdp_ext_f=%7B%22sku_id%22:%2212000022635165947%22,%22ship_from%22:%22CN%22%7D&gps-id=pcStoreJustForYou&scm=1007.23125.137358.0&scm_id=1007.23125.137358.0&scm-url=1007.23125.137358.0&pvid=8e29d7e9-f257-4f20-a0b2-c2bff6a048d6&spm=a2g0o.store_pc_home.smartJustForYou_6000897758043.1" target="_blank">C790 & C780</a>

其它国家客户采购连接：<a href="https://www.aliexpress.com/item/1005003033156483.html?spm=a2g0o.productlist.0.0.36f93cc2DFaouV&algo_pvid=2bfab2d1-a9c7-4c29-9434-2f451401d0e1&algo_exp_id=2bfab2d1-a9c7-4c29-9434-2f451401d0e1-9&pdp_ext_f=%7B%22sku_id%22%3A%2212000023351081819%22%7D" target="_blank">C779</a>
