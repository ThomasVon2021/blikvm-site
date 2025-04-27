# Modifying PiKVM image to work with BliKVM hardware

!!! warning "Because the blikvm hardware implementation scheme and PiKVM hardware implementation scheme are not exactly the same, you need to modify some errors through the following configuration for the official image of PiKVM. Of course, you can use the [configured image](./flashing_os.md)."

## **Fan config**

!!! info "Since BliKVM's fan hardware is different to PiKVM's, you need to replace the control fan script first. The following default starting fan temperature is 40 degrees Celsius"
    ```
    su -
    rw
    git clone https://github.com/blikvm/blikvm.git
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

## **OLED**

!!! abstract "Follow the method below to enable OLED."
    If you use PiKVM official image, log in to PiKVM and run these commands:
    ```
    # rw
    # systemctl enable --now kvmd-oled //Enable OLED
    # ro
    ```
    If the oled still can't work, you need to check whether there has "dtparam=i2c_arm=on" in "/boot/config.txt" file, and whether there has "i2c-dev" in "/etc/modules-load.d/i2c.conf" file. If not, please create and add them.
    If it still does not work after the above configuration, please burn [the image](./flashing_os.md) provided by blikvm for testing to check whether the OLED hardware is damaged.  

## **Config about v4mini image**
If you want to PiKVM v4mini image for blikvm v1 and v2, because  v4mini image uses different gpio pins for ATX controls, so you will need the following override if you want to run v4mini image on your blikvm v1 or v2 version and be able to use ATX controls; if you don't make this change, ATX controls won't work properly (the led pins are different);
Edit the /etc/kvmd/override.yaml file and add the following:
```
kvmd:
    ### disable fan socket check ###
    info:
        fan:
            unix: ''
    atx:
        hdd_led_pin: 22
        power_led_pin: 24
        power_switch_pin: 23
        reset_switch_pin: 27
        type: gpio
    gpio:
        scheme:
            __v3_usb_breaker__:
                pin: 5
                mode: output
                initial: false
                pulse:
                    delay: 0
```
