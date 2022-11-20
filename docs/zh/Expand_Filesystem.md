# 树莓派扩容
## 简介
由于在制作镜像过程中，对镜像进行了压缩，如果你发现树莓派SD卡或者eMMC的可用空间小于实际SD卡或者eMMc的容量，你可能需要进行以下操作，对树莓派进行扩容。
如果你发现系统并无raspi-config工具，则可使用方法二（使用GParted分区工具）。

## 方法一 使用raspi-config工具
**1.** 打开raspi-config系统配置工具
```
sudo raspi-config
```
**2.** 选择Advancd Options：  
![IMG_8366](assets/images/expand_filesystem/advance_option.png){width="300"}

**3.** 选择Expand Filesystem：  
![IMG_8366](assets/images/expand_filesystem/expand.png){width="300"}

**4.** Ok:  
![IMG_8366](assets/images/expand_filesystem/expand_ok.png){width="300"}

**5.** 重启树莓派后，即可。

## 方法二 使用GParted分区工具
**1.** 将烧录好镜像的SD卡或者EMMc通过usb接到电脑上，以linux下GParted分区工具为例，其它平台也有类似的分区工具。打开GParted软件，选择SD卡：  
![](assets/images/expand_filesystem/gparted01.png){width="300"}

**2.** 观察上图SD卡的分区情况，可以发现在sdb3分区的前后各有2.01GB和21.87GB的空间未使用，这部分空间就是我们要扩容的空间。选中sdb3分区，点击调整大小。  
![](assets/images/expand_filesystem/gparted02.png){width="300"}
![](assets/images/expand_filesystem/gparted03.png){width="300"}

**3.** 可以拖动sdb3的白色分区扩大到最左和最右，或者填写“之前的可用空间”为“0”，“新大小”为“最大大小”的25958，然后点击右下角的调整大小，然后弹出来的提醒点击确认，即可看到sd的所有未使用空间全部用上了。  
![](assets/images/expand_filesystem/gparted04.png){width="300"}
![](assets/images/expand_filesystem/gparted05.png){width="300"}

**4.** 将SD卡插入设备，启动即可。

