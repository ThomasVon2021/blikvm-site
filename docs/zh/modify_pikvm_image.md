# 如果你使用的是PiKVM官方镜像，需要做以下修改来适配BLIKVM硬件
!!! warning "因为blikvm硬件实现方案和PiKVM硬件实现方案并不完全相同，因此针对PiKVM官方镜像，您需要通过下列配置修改一些错误。当然您可以使用我们已经做好配置的[镜像](./flashing_os.md)"

## **风扇**
!!! info "因BLIKVM硬件与PiKVM使用风扇不同，首先需替换控制风扇脚本，下列默认开始风扇温度为40摄氏度"
    ```
    su -
    rw
    git clone https://github.com/ThomasVon2021/blikvm.git
    cd blikvm/package/kvmd-fan
    bash install-kvmd-fan.sh
    ro
    ```
!!! note "编辑/etc/kvmd/override.yaml文件，添加下列内容已去除Web UI关于风扇的错误警告。"
    ```
    kvmd:
        info:
            fan:
                unix: ''
    ```

## 2. **EDID文件更换**
EDID文件作用为，设置被控计算机按照期望的分辨率进行输入，由于PiKVM不同时期的镜像EDID文件不一定是满足1080P60Hz, 当你使用的硬件为CM4版本，发现被控电脑默认输出不是1080P60Hz，可以通过修改/etc/kvmd/tc358743-edid.hex为下列内容：
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

!!! note "确认 /boot/config.txt 添加了下列配置，从而支持1080p60hz视频输入和声音输入，相关配置参考如下："
    ```
    # Video and audio
    dtoverlay=tc358743,4lane=1
    dtoverlay=tc358743-audio
    ```

!!! note "如果你使用webrtc没有声音，尝试在/etc/kvmd/janus/janus.plugin.ustreamer.jcfg此文件中添加下列内容"
    ```
    audio: {
        device = "hw:0,0"
        tc358743 = "/dev/kvmd-video"
    }
    ```