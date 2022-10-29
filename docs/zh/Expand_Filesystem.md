# 树莓派扩容
如果你发现树莓派SD卡或者eMMC的可用空间小于实际SD卡或者eMMc的容量，你需要进行以下操作，对树莓派进行扩容。

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