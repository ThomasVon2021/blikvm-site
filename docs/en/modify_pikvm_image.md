# PiKVM image Modify for blikvm 

## **fan config**
!!! info "Because BLIKVM fan hardware different with PiKVM, you need to replace the control fan script first. The following default starting fan temperature is 40 degrees Celsius"
    ```
    su -
    rw
    git clone https://github.com/ThomasVon2021/blikvm.git
    cd blikvm/package/kvmd-fan
    bash install-kvmd-fan.sh
    ro
    ```
!!! note "Edit the /etc/kvmd/override.yaml file and add the following content to remove the web UI error warning about fans."
    ```
    kvmd:
        info:
            fan:
                unix: ''
    ```
!!! note "make sure /boot/config.txt has the 4lane=1 entry in it for 1080p60hz support"
    ```
    # Video and audio
    dtoverlay=tc358743,4lane=1
    dtoverlay=tc358743-audio
    ```
!!! note "If you use webrtc can't get audio, try to edit /etc/kvmd/janus/janus.plugin.ustreamer.jcfg to add audio support."
    ```
    audio: {
        device = "hw:0,0"
        tc358743 = "/dev/kvmd-video"
    }
    ```



## **Check EDID file for 1080P60Hz input**
!!! note "The function of the EDID file is to set the controlled computer to input according to the expected resolution. Since the image EDID file of PiKVM in different periods does not necessarily meet 1080P60Hz, when you use the CM4 version of hardware, it is found that the default output of the controlled computer is not 1080P60Hz, you can modify /etc/kvmd/tc358743-edid.hex to the following contents"
    ```
    00FFFFFFFFFFFF005262888800888888
    1C150103800000780AEE91A3544C9926
    0F505400000001010101010101010101
    010101010101011D007251D01E206E28
    5500C48E2100001E8C0AD08A20E02D10
    103E9600138E2100001E000000FC0054
    6F73686962612D4832430A20000000FD
    003B3D0F2E0F1E0A202020202020014F
    020323454F041303021211012021A23C
    3D3E1F102309070766030C00300080E3
    007F8C8C0AD08A20E02D10103E9600C4
    8E210000188C0AD08A20E02D10103E96
    00138E210000188C0AA01451F0160026
    7C4300138E2100009800000000000000
    00000000000000000000000000000000
    00000000000000000000000000000087
    ```

