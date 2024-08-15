# HDMI to CSI&I2S bridge guide

> Convert HDMI signal acquisition into CSI signal and I2S audio signal. Currently, all platforms are supported (Zero, Pi3B, Pi4B, CM4, Pi5B), and the maximum capture resolution not only depends on the HDMI to CSI converter board you are using but also on the Raspberry Pi hardware version you have. Raspberry Pi hardware versions are primarily divided into two series, one supporting a maximum of 1080P60Hz and the other supporting a maximum of 1080P50Hz.

- The Raspberry Pi versions that support a maximum of 1080P60Hz are CM3, CM4, and Pi5B.

- The Raspberry Pi versions that support a maximum of 1080P50Hz are Zero, Zero 2, Pi3B, Pi4B, and so on.

## **Introduction**

This module takes the incoming HDMI signal and converts it into a separate CSI signal and I2S audio signal. HDMI input supports up to 1080P60Hz. It works well on Raspberry Pi, there are three versions of this module in history (C779, C780, C790). C790 is the latest version. C790 has mitigated HDMI backpowering, and also has two csi channels and four csi channels at the same time.
![hdmi-csi-i2s](assets/images/hdmi-csi-i2s/c790.png)

## **Features**

### **C790**

!!! note "Hardware Parameters"
    - HDMI input: supports up to 1080P60Hz on Raspberry Pi
    - HDMI to CSI-2 bridge chip: Toshiba TC358743XBG
    - 4 CSI-2 channels & clock
    - The CSI-2 interface, with 15 pin FPC seat, spacing 1.0 mm, is located on the front of the C790 module.
    - The CSI-2 interface, with 22 pin FPC seat, spacing 0.5 mm, is located on the back of the C790 module.
    - Size: 30 x 45 mm
    - Install: 4 x M2.5
    - Power supply: 3.3V
    - Weight: 10g

!!! warning "Pi 4B only support 1080P50Hz, limited by the number of CSI-2 channels. CM4 support 1080P60HZ, So if you must use 1080P60Hz input, please use CM4 and C790 together."

!!! note "Interface"
    ![c790-interface](assets/images/hdmi-csi-i2s/c790-interface.png){width="400"}
    C790 has two CSI output interfaces. In front of C790, the CSI-2 interface is 15 pin FPC seat, spacing 1.0 mm. In back of C790, the CSI-2 interface is 22 pin FPC seat, spacing 0.5 mm.
    ![c790-i2s-connect](assets/images/hdmi-csi-i2s/c790-i2s-connect.png){width="400"}

!!! note "Size"
    ![c790-size](assets/images/hdmi-csi-i2s/c790-size.png){width="400"}

!!! note "Install C790 on Raspberry Pi for reference"
    ![install-c790-pi4b](assets/images/hdmi-csi-i2s/install_c790_pi4b.png){width="400"}

### **C780**

??? info "C780A Hardware Parameters"
    - HDMI input: supports up to 1080P50Hz on Raspberry Pi(Limited by the number of CSI-2 channels)
    - HDMI to CSI-2 bridge chip: Toshiba TC358743XBG
    - 2 CSI-2 channels & clock
    - CSI-2 interface: 15 pin FPC seat, spacing 1.0 mm
    - Size: 30 x 65 mm (unbroken PCB size); 30 x 45 mm (PCB size after breaking)
    - Install: 6 x M2.5
    - Power supply: 3.3V
    - Weight: 10g
??? info "C780B Hardware Parameters"
    - HDMI input: supports up to 1080P60Hz on Raspberry Pi
    - HDMI to CSI-2 bridge chip: Toshiba TC358743XBG
    - 4 CSI-2 channels & clock
    - CSI-2 interface: 22 pin FPC seat, spacing 0.5 mm
    - Size: 30 x 65 mm (unbroken PCB size); 30 x 45 mm (PCB size after breaking)
    - Install: 6 x M2.5
    - Power supply: 3.3V
    - Weight: 10g
??? info "Interface"
    ![2-4](assets/images/hdmi-csi-i2s/2-4.png){width="400"}
    The wiring of audio part is shown in Figure.  
    ![2-8](assets/images/hdmi-csi-i2s/2-8.png){width="400"}
??? info "Size"
    The size of C780 is shown in the image below. There are 6 mounting holes with a diameter of 2.75mm, which are suitable for M2.5 screws.  
    ![2-1](assets/images/hdmi-csi-i2s/2-1.png){width="400"}
    As shown in the image below, the user can directly fix the module on the Raspberry Pi Zero. C780 is designed to be broken, and the hole spacing before breaking can be perfectly installed with most series of Raspberry Pi.
    ![2-2](assets/images/hdmi-csi-i2s/2-2.png){width="400"}

### **C779**

??? info "Hardware Parameters"
    - HDMI input: supports up to 1080P50Hz on Raspberry Pi(Limited by the number of CSI-2 channels)
    - HDMI to CSI-2 bridge chip: Toshiba TC358743XBG
    - 2 CSI-2 channels & clock
    - CSI-2 interface: 15 pin FPC seat, spacing 1.0 mm
    - Size: 35 x 50 mm
    - Install: 4 x M2.5
    - Power supply: 3.3V
    - Weight: 10g

??? info "Size"
    The size of C779 is shown in Figure. There are 4 mounting holes with a diameter of 2.75mm, which are suitable for M2.5 screws.  
    ![C779-size](assets/images/hdmi-csi-i2s/c779-size.png){width="400"}

## **CSI Interface Definitions**

The CSI (Camera Serial Interface) interfaces C779 and C780A have 15 pins each, while the C780B interface has 22 pins. The C790 interface is unique as it supports both 15 and 22 PIN configurations.

![Interface](assets/images/hdmi-csi-i2s/interface.png){width="400"}

## **Software Demo**

The use guide of C790/C780/C779 depends on the official Raspberry Pi OS version you are using.
Different versions have different usage methods. If you have some questions, Join our [BLIKVM Discord Community](https://discord.com/invite/9Y374gUF6C) for Support, FAQ & News!
To use the kernel drivers, please update your system. There are a few things that have changed with the 5.4 kernel, so these instructions are for 5.4 or later. If `uname -a` reports anything less, then fix this before proceeding.

```bash
pi@raspberrypi:~ $ uname -a
Linux raspberrypi 5.10.63-v7l+ #1459 SMP Wed Oct 6 16:41:57 BST 2021 armv7l GNU/Linux
```

!!! note "1. Update & upgrade the Raspberry Pi system (It will take a long time depend on the different country)"
    ```
    sudo apt-get update
    sudo apt-get upgrade
    ```
!!! note "2. Enable camera module (the camera is enabled by default in Raspberry pi Bullseys OS)"
    ```
    sudo raspi-config
    sudo reboot
    ```
    Navigate to ‘Interfacing Options’ and hit Enter. Now select the ‘Camera’ option, and hit the Enter key to enable it. Select “Finish” and select to reboot your Raspberry Pi. **reboot is important!!**

??? warning "Due to the absence of hardware encoding on the Pi5B, the software usage instructions for Pi platforms are currently divided into two sections: Pi5B configuration and configuration for other Pi platforms."

??? note "In platforms such as Zero, Zero 2, Pi3B, Pi4B, etc., there is a reference for testing HDMI to CSI module demo."
    Edit /boot/config.txt (that will need sudo)
    ```
    sudo nano /boot/config.txt
    ```
    Add the line:
    ```
    dtoverlay=tc358743
    ```
    Add the line if your shield support audio like C780 or C790.
    ```
    dtoverlay=tc358743-audio
    ```
    If (and only if) you have a device such as the C780 or C790 that supports the 22pin connector with all 4 lanes wired out, and are using a Compute Module with the CAM1 connector that also has all 4 lanes wired up, you can use:
    ```
    dtoverlay=tc358743,4lane=1
    ```
    Check the amount of memory assigned to the CMA heap with “dmesg | grep cma”. The first line should be along the lines of:
    ```
    pi@raspberrypi:~ $ dmesg | grep cma
    [0.000000] cma: Reserved 256 MiB at 0x000000001ec00000
    ```
    If it reports less than 96MB assigned to CMA, then edit /boot/cmdline.txt and add to the start of the line.
    Do NOT add any carriage returns.
    ```
    cma=96M
    ```
    Reboot. If all is well you should get a /dev/video0 device, and “v4l2-ctl –list-devices” will tell you that it is provided by Unicam. After connecting all the cables, power on the Raspberry Pi, the C790 indicator light is normally green, and after opening the Raspberry Pi terminal, enter the following command:
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
    This driver puts all the control in the hands of the user, or the user’s application. By default there is no EDID loaded into the chip to allow it to tell the HDMI source what resolutions are supported. There are EDID editors around. If you create a file edid.txt, then you can push this to the device using the comment of edid.txt file:
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
    #copy the above commend in edid.txt, save&exit;
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
    The driver does NOT automatically switch to the resolution detected. Use the command:
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
    You MUST set the timings via “v4l2-ctl –set-dv-bt-timings”. You can pass in an index to the detected mode, or use:
    ```
    v4l2-ctl --set-dv-bt-timings query
    ```
    to select the currently detected timings.
    ```
    v4l2-ctl -V
    ```
    should now reflect the resolution detected.
    The chip supports two formats – BGR3 (the default) and UYVY. BGR3 is 24bpp, and UYVY is YUV4:2:2 16bpp.
    Over the normal 2 CSI-2 lanes the data rate is such that BGR3 can run at a maximum of 1080p30, whilst UYVY will 
    go up to 1080p50. Use the following command to select UYVY, however your application may override that.
    ```
    v4l2-ctl -v pixelformat=UYVY
    ```
    Check that the audio drivers / card is available to ALSA.
    ```
    pi@raspberrypi:~ $ arecord -l
    **** List of CAPTURE Hardware Devices ****
    card 1: tc358743 [tc358743], device 0: bcm2835-i2s-dir-hifi dir-hifi-0 [bcm2835-i2s-dir-hifi dir-hifi-0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    ```
    Note: card 1 means that the card number for the TC358743XBG is “1” and it might be different.

    Install GStreamer tool.
    ```
    sudo apt install gstreamer1.0-tools
    ```
    Check gstreamer tool version:
    ```
    pi@raspberrypi:~ $ gst-launch-1.0 --version
    gst-launch-1.0 version 1.18.4
    GStreamer 1.18.4
    http://packages.qa.debian.org/gstreamer1.0
    ```
    Note:
    Different versions have different command line parameters, which is very annoying.

    Use gstreamer to record video and audio
    ```
    #GStreamer v1.14 command
    gst-launch-1.0 v4l2src io-mode=5 ! video/x-raw, format=UYVY, framerate=25/1 ! v4l2h264enc output-io-mode=4 ! video/x-h264,profile=high ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    ```
    foo.mkv is the output file.
    If your gstreamer is version 1.8 or above, you can try the following test command. In addition, alsasrc 
    device=hw:1 represents the sound card of TC358743, you can use “arecord -l” to query.
    ```
    #The command to recode a video with audio. (GStreamer 1.18.4)
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=30/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    #The sample command to recode a video without audio. (C779 doesn't support audio)
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=30/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv
    Press CTRL+C to end recording.
    ```
    PS: We recommend that you modify the above framerate parameter to the actual frame rate of your HDMI signal, 
    the actual frame rate value is from the result of ‘v4l2-ctl –query-dv-timings’ command.
    ![Image title](assets/images/hdmi-csi-i2s/v4l2-rate.png){width="400"}
    For the above HDMI device, because the frame rate is 60, so we modify the framerate parameter to 60 like the followint command.
    Record the video only:
    ```
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=60/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv
    ```
    Record the video and audio: (if your shield supports audio also)
    ```
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=60/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    ```
    Note: alsasrc device=hw:1 – “1” means the audio card number, You must change to correct audio card number.
    (Query the car number via ‘arecord –l’, refer to step 9)

??? note "Pi5B platforms HDMI to CSI module test demo reference."
    Edit /boot/config.txt (sudo permission required).
    ```
    sudo nano /boot/config.txt
    ```
    Add the following content:
    ```
    dtoverlay=tc358743
    ```
    If your modules (C780 and C790) support audio, add the following content to enable audio support.
    ```
    dtoverlay=tc358743-audio
    ```
    Reboot the Raspberry Pi and execute the following command to find the media node corresponding to the CSI as media0, under the rp1-cfe (platform: 1f00128000.csi) field:
    ```
    blikvm@blikvm:~ $ v4l2-ctl --list-devices
    pispbe (platform:1000880000.pisp_be):
            /dev/video20
            /dev/video21
            /dev/video22
            /dev/video23
            /dev/video24
            /dev/video25
            /dev/video26
            /dev/video27
            /dev/video28
            /dev/video29
            /dev/video30
            /dev/video31
            /dev/video32
            /dev/video33
            /dev/video34
            /dev/video35
            /dev/video36
            /dev/video37
            /dev/media1
            /dev/media2

    rp1-cfe (platform:1f00128000.csi):
            /dev/video0
            /dev/video1
            /dev/video2
            /dev/video3
            /dev/video4
            /dev/video5
            /dev/video6
            /dev/video7
            /dev/media0

    rpivid (platform:rpivid):
            /dev/video19
            /dev/media3
    ```

    Locate the node corresponding to tc358743 as v4l-subdev2, and the pad0 of rp1-cfe-csi2_ch0 as video0:
    ```
    blikvm@blikvm:~ $ media-ctl -d /dev/media0 -p
    Media controller API version 6.1.63

    Media device information
    ------------------------
    driver          rp1-cfe
    model           rp1-cfe
    serial
    bus info        platform:1f00128000.csi
    hw revision     0x114666
    driver version  6.1.63

    Device topology
    - entity 1: csi2 (8 pads, 8 links)
                type V4L2 subdev subtype Unknown flags 0
                device node name /dev/v4l-subdev0
            pad0: Sink
                    [fmt:SRGGB10_1X10/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
                    <- "tc358743 4-000f":0 [ENABLED,IMMUTABLE]
            pad1: Sink
                    [fmt:unknown/8192x1 field:none]
            pad2: Sink
                    [fmt:SRGGB10_1X10/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
            pad3: Sink
                    [fmt:SRGGB10_1X10/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
            pad4: Source
                    [fmt:SRGGB10_1X10/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
                    -> "rp1-cfe-csi2_ch0":0 []
                    -> "pisp-fe":0 []
            pad5: Source
                    [fmt:unknown/8192x1 field:none]
                    -> "rp1-cfe-embedded":0 []
            pad6: Source
                    [fmt:SRGGB10_1X10/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
                    -> "rp1-cfe-csi2_ch2":0 []
                    -> "pisp-fe":0 []
            pad7: Source
                    [fmt:SRGGB10_1X10/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
                    -> "rp1-cfe-csi2_ch3":0 []
                    -> "pisp-fe":0 []

    - entity 10: pisp-fe (5 pads, 7 links)
                type V4L2 subdev subtype Unknown flags 0
                device node name /dev/v4l-subdev1
            pad0: Sink
                    [fmt:SRGGB16_1X16/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
                    <- "csi2":4 []
                    <- "csi2":6 []
                    <- "csi2":7 []
            pad1: Sink
                    [fmt:FIXED/8192x1 field:none]
                    <- "rp1-cfe-fe_config":0 []
            pad2: Source
                    [fmt:SRGGB16_1X16/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
                    -> "rp1-cfe-fe_image0":0 []
            pad3: Source
                    [fmt:SRGGB16_1X16/640x480 field:none colorspace:raw xfer:none ycbcr:601 quantization:full-range]
                    -> "rp1-cfe-fe_image1":0 []
            pad4: Source
                    [fmt:FIXED/8192x1 field:none]
                    -> "rp1-cfe-fe_stats":0 []

    - entity 16: tc358743 4-000f (1 pad, 1 link)
                type V4L2 subdev subtype Unknown flags 0
                device node name /dev/v4l-subdev2
            pad0: Source
                    [fmt:RGB888_1X24/640x480 field:none colorspace:srgb]
                    [dv.caps:BT.656/1120 min:640x350@13000000 max:1920x1200@165000000 stds:CEA-861,DMT,CVT,GTF caps:progressive,reduced-blanking,custom]
                    [dv.detect:BT.656/1120 1920x1080p24 (2750x1125) stds: flags:]
                    [dv.current:BT.656/1120 640x480p59 (800x525) stds:CEA-861,DMT flags:has-cea861-vic]
                    -> "csi2":0 [ENABLED,IMMUTABLE]

    - entity 18: rp1-cfe-csi2_ch0 (1 pad, 1 link)
                type Node subtype V4L flags 0
                device node name /dev/video0
            pad0: Sink
                    <- "csi2":4 []

    - entity 22: rp1-cfe-embedded (1 pad, 1 link)
                type Node subtype V4L flags 0
                device node name /dev/video1
            pad0: Sink
                    <- "csi2":5 []

    - entity 26: rp1-cfe-csi2_ch2 (1 pad, 1 link)
                type Node subtype V4L flags 0
                device node name /dev/video2
            pad0: Sink
                    <- "csi2":6 []

    - entity 30: rp1-cfe-csi2_ch3 (1 pad, 1 link)
                type Node subtype V4L flags 0
                device node name /dev/video3
            pad0: Sink
                    <- "csi2":7 []

    - entity 34: rp1-cfe-fe_image0 (1 pad, 1 link)
                type Node subtype V4L flags 1
                device node name /dev/video4
            pad0: Sink
                    <- "pisp-fe":2 []

    - entity 38: rp1-cfe-fe_image1 (1 pad, 1 link)
                type Node subtype V4L flags 0
                device node name /dev/video5
            pad0: Sink
                    <- "pisp-fe":3 []

    - entity 42: rp1-cfe-fe_stats (1 pad, 1 link)
                type Node subtype V4L flags 0
                device node name /dev/video6
            pad0: Sink
                    <- "pisp-fe":4 []

    - entity 46: rp1-cfe-fe_config (1 pad, 1 link)
                type Node subtype V4L flags 0
                device node name /dev/video7
            pad0: Source
                    -> "pisp-fe":1 []
    ```
    To query the current input source information, if the resolution displays as 0, it indicates that no input source signal has been detected. In this case, you should check the hardware connections and follow the steps mentioned above to troubleshoot.
    ```
    blikvm@blikvm:~ $ v4l2-ctl -d /dev/v4l-subdev2 --query-dv-timings
        Active width: 1920
        Active height: 1080
        Total width: 2750
        Total height: 1125
        Frame format: progressive
        Polarities: -vsync -hsync
        Pixelclock: 74250000 Hz (24.00 frames per second)
        Horizontal frontporch: 0
        Horizontal sync: 830
        Horizontal backporch: 0
        Vertical frontporch: 0
        Vertical sync: 45
        Vertical backporch: 0
        Standards:
        Flags:
    ```
    Confirm the current input source information.
    ```
    blikvm@blikvm:~ $ v4l2-ctl -d /dev/v4l-subdev2 --set-dv-bt-timings query
    BT timings set
    ```
    Initialize media0.
    ```
    blikvm@blikvm:~ $ media-ctl -d /dev/media0 -r
    ```
    Connect CSI2's pad4 to rp1-cfe-csi2_ch0's pad0.
    ```
    blikvm@blikvm:~ $ media-ctl -d /dev/media0 -l ''\''csi2'\'':4 -> '\''rp1-cfe-csi2_ch0'\'':0 [1]'
    ```
    Configure the media node.
    ```
    blikvm@blikvm:~ $ media-ctl -d /dev/media0 -V ''\''csi2'\'':0 [fmt:RGB888_1X24/1920x1080 field:none colorspace:srgb]'
    blikvm@blikvm:~ $ media-ctl -d /dev/media0 -V ''\''csi2'\'':4 [fmt:RGB888_1X24/1920x1080 field:none colorspace:srgb]'
    ```
    Set the output format.
    ```
    v4l2-ctl -v width=1920,height=1080,pixelformat=RGB3
    ```
    Capture two frames for testing to verify if tc358743 is functioning properly. Other methods, such as using GStreamer, are not currently available.
    ```
    v4l2-ctl --verbose -d /dev/video0 --set-fmt-video=width=1920,height=1080,pixelformat='RGB3' --stream-mmap=4 --stream-skip=3 --stream-count=2 --stream-to=hdmiin.yuv --stream-poll
    ```
    If you have installed a desktop version of Raspberry Pi, you can use ffplay to directly play YUV files.
    ```
    ffplay -f rawvideo -video_size 1920x1080 -pixel_format bgr24 hdmiin.yuv 
    ```
    On a Windows computer, you can use software like 7yuv to view .yuv files. For the tutorial with an input format of 1920*1080, you should select BGR888 in the top right corner of 7yuv and set the resolution to 1920*1080 to view the two frames you just captured.

## **Chip Docs**

[TC358743 Documentation](https://zcwrego195.feishu.cn/drive/folder/V3dXfMA5UlBNmXdX2hycYZuLnxc?from=from_copylink)

## **Packing List**

??? info "C790"
    ![packing-list](assets/images/hdmi-csi-i2s/c790-packing-list.png){width="400"}

## **Test Video**

[C780A Test](https://www.youtube.com/watch?v=ecqyINoiHNQ)

[C780B Test](https://www.youtube.com/watch?v=nc-hwPT2Uak)

## **Purchase Link**

[Purchase C780 & C790](https://www.aliexpress.com/item/1005002861310912.html?pdp_ext_f=%7B%22sku_id%22:%2212000022635165947%22,%22ship_from%22:%22CN%22%7D)

[Purchase C779](https://www.aliexpress.com/item/1005003033156483.html?algo_exp_id=2bfab2d1-a9c7-4c29-9434-2f451401d0e1-9&pdp_ext_f=%7B%22sku_id%22%3A%2212000023351081819%22%7D)
