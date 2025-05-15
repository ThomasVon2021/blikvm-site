# EDID

The EDID file in BliKVM serves the purpose of informing the controlled computer about the expected HDMI output resolution. For example, if the EDID is set to 1080P60Hz, and the controlled computer supports this resolution, it will output at 1080P60Hz. Additionally, EDID can be used to disable audio, modify the display model, name, manufacturer, and other information. In most cases, you don't need to change it, but sometimes, especially with strange UEFI/BIOS behavior, it may be necessary.

!!! note
    - BliKVM v1, v2, and v3 use the CSI video capture scheme, which supports EDID settings. However, BliKVM v4 uses the USB video capture scheme, which does not support EDID settings.
    - For v3 HAT, there is a limitation of two CSI channels on the Raspberry Pi 4B, which means it can only capture video input with a maximum resolution of 1080P50Hz. Therefore, if you set 1080P60Hz EDID for v3, it will not be able to capture the image.
    - If you are using PiKVM OS, you can refer to [this link](https://docs.pikvm.org/edid/) for modification instructions.
    - If you are using BliKVM OS, the EDID file is located at `/mnt/exec/release/lib/edid.txt`. Open this file, and replace the EDID contents with the desired resolution's EDID.

## EDID Examples for 1080P60Hz

The following EDID is suitable for v1 and v2 hardware.

??? example "1920x1080 60Hz, with audio"
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

## EDID Examples for 1080P50Hz

The following EDID is suitable for v1, v2, and v3 hardware, especially when you want v3 HAT to capture 1080P resolution.

??? example "1920x1080 50Hz, with audio"
    ```
    00ffffffffffff005262888800888888
    1c150103800000780aEE91A3544C9926
    0F505400000001010101010101010101
    010101010101011d007251d01e206e28
    5500c48e2100001e8c0ad08a20e02d10
    103e9600138e2100001e000000fc0054
    6f73686962612d4832430a20000000FD
    003b3d0f2e0f1e0a202020202020014f
    020321434e041303021211012021a23c
    3d3e1f2309070766030c00300080E300
    7F8c0ad08a20e02d10103e9600c48e21
    0000188c0ad08a20e02d10103e960013
    8e210000188c0aa01451f01600267c43
    00138e21000098000000000000000000
    00000000000000000000000000000000
    00000000000000000000000000000028
    ```

## EDID Examples for 720P60Hz

The following EDID is suitable for v1, v2, and v3 hardware.

??? example "1280x720 60Hz, with audio"
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

## Custom EDID

To customize the EDID, it is best to use third-party utilities, such as the recommended advanced [AW EDID Editor](https://www.analogway.com/emea/products/software-tools/aw-edid-editor) (works well in Windows and can be used in wine) or [wxEDID](https://sourceforge.net/projects/wxedid). Both editors work with the binary EDID format.
Using these tools, you can modify the EDID information like editing a file, similar to changing the information on an identity card. By editing the EDID, you can adjust the parameters and characteristics of the display to suit different usage requirements, and thus achieve better display performance.
