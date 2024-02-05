# 在jstson nano上使用C790
C779 C780 C790全部适用此文档，本文测试底板为jetson nano b01，若你其它底板有一些设计到跟板子型号相关的步骤，需要对应改变，请注意。

现在内核源码
```
wget  https://developer.nvidia.com/embedded/l4t/r32_release_v7.2/sources/t210/public_sources.tbz2
tar -xf public_sources.tbz2  Linux_for_Tegra/source/public/kernel_src.tbz2 --strip-components=3
tar xf kernel_src.tbz2
```
根据仓库里的目录结构进行文件替换，要全部替换
```
git clone https://github.com/ThomasVon2021/jetson_tc358743
cp ~/jetson_tc358743/* ./ -r
.
└── jetson_tc358743-main
    ├── hardware
    │   └── nvidia
    │       └── platform
    │           └── t210
    │               ├── batuu
    │               │   └── kernel-dts
    │               │       └── tegra210-p3448-0003-p3542-0000.dts
    │               └── porg
    │                   └── kernel-dts
    │                       ├── Makefile
    │                       ├── porg-platforms
    │                       │   ├── tegra210-dual-tc358743.dtsi
    │                       │   ├── tegra210-porg-dual-tc358743.dtsi
    │                       │   ├── tegra210-porg-tc358743.dtsi
    │                       │   └── tegra210-tc358743.dtsi
    │                       ├── tegra210-p3448-0000-p3449-0000-b00.dts
    │                       ├── tegra210-p3448-all-p3449-0000-camera-tc358743-dual.dts
    │                       └── tegra210-p3448-common-tc358743.dts
    ├── kernel
    │   └── kernel-4.9
    │       ├── drivers
    │       │   └── media
    │       │       └── i2c
    │       │           ├── tc358743.c
    │       │           └── tc358743_regs.h
    │       └── include
    │           └── media
    │               └── i2c
    │                   └── tc358743.h
    └── README.md
```

交叉编译链下载,后面make时，你需要指定编译链
```
wget http://releases.linaro.org/components/toolchain/binaries/7.3-2018.05/aarch64-linux-gnu/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz
tar xf gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz
```

进入到kernel/kernel-4.9/，先配置再编译，
```
make ARCH=arm64 tegra_defconfig menuconfig

Device Drivers > Multimedia Support > I2C Encoders, decoders, sensors and other helper chips
Toshiba TC358743 decoder should be * (press y or space on the option)

grep -i tc358743 .config #checking if its really enabled  

make ARCH=arm64 CROSS_COMPILE=/root/work/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu- -j4
```






将编译出来的Image和dtb文件分别拷贝到nano的系统的下面路径下,若你的载板不是B01，需要更换对应的dtb文件，dtb文件与你的板子型号对应关系，可以查找 [wiki](https://wiki.veye.cc/index.php/VEYE_CS_Camera_for_Jetson_TX2#DTB_file_corresponds_to_Jetson_boards) 
 
```
kernel/kernel-4.9/arch/arm64/boot/Image ==> /boot/Image
kernel/kernel-4.9/arch/arm64/boot/dts/tegra210-p3448-0000-p3449-0000-b00.dtb ==>  /boot/veyecam/
#其中你的nano路径如果不存在veyecam文件夹，先创建
sudo mkdir /boot/veyecam/
sudo cp <path to your dtb dir>/<DTB file name> /boot/veyecam/ -f
```

先备份 extlinux.conf 文件，然后编辑/boot/extlinux/extlinux.conf文件，在该文件下增加：
FDT /boot/veyecam/<DTB file name>
注意<DTB file name>为你版本编译出来的dtb实际文件名，
重启后生效
