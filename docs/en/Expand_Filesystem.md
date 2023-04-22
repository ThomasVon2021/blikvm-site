# Expand Filesystem

If you find that the free space of the raspberry pi SD card or eMMC is smaller than the capacity of the actual SD card or eMMC, you need to do the following to expand the raspberry pi. If you find that the system does not have the raspi config tool, you can use Method 2 (use the GParted partition tool).  

## Method 1: Use raspi-config tool
**1.** open raspi-config.
```
sudo raspi-config
```
**2.** choose Advancd Options：  
![IMG_8366](assets/images/expand_filesystem/advance_option.png){width="300"}

**3.** choose Expand Filesystem：  
![IMG_8366](assets/images/expand_filesystem/expand.png){width="300"}

**4.** Ok:  
![IMG_8366](assets/images/expand_filesystem/expand_ok.png){width="300"}

**5.** reboot raspberry.

## Method 2: Use GParted tool
**1.** Connect the SD card or EMMc that has burned the image to the computer through USB. Take the GParted partition tool under Linux as an example. Other platforms also have similar partition tools. Open GParted software and select SD card:    
![](assets/images/expand_filesystem/gparted01.png){width="300"}

**2.** By observing the partition of the SD card in the above figure, we can find that 2.01GB and 21.87GB of space are unused before and after the sdb3 partition, which is the space we want to expand. Select the sdb3 partition and click Resize.  
![](assets/images/expand_filesystem/gparted02.png){width="300"}
![](assets/images/expand_filesystem/gparted03.png){width="300"}

**3.** You can drag the white partition of sdb3 to the leftmost and rightmost, or fill in 25958 with "Previous Free Space" as "0" and "New Size" as "Maximum Size", and then click Resize in the lower right corner. Then click OK to see that all unused space of sd has been used.  
![](assets/images/expand_filesystem/gparted04.png){width="300"}
![](assets/images/expand_filesystem/gparted05.png){width="300"}

**4.** Insert the SD card into the device and start it.  

## Method 3: Use script
If you are using a PiKVM image, you can run the following script on KVM to automatically expand the space.
**1.** Log in to the KVM terminal, confirm that the system has read and write permissions, run `vim expand. sh` on any path, and write the following content to expand.sh
```
#!/bin/bash
set -x
        if grep -q 'X-kvmd\.otgmsd' /etc/fstab; then
                part=$(grep 'X-kvmd\.otgmsd' /etc/fstab | awk '{print $1}')
                # shellcheck disable=SC2206
                splitted=(${part//=/ })
                if [ "${splitted[0]}" == LABEL ]; then
                        label=${splitted[1]}
                        part=$(blkid -c /dev/null -L "$label")
                else
                        label=PIMSD
                fi
                unset splitted
                disk=/dev/$(lsblk -no pkname "$part")
                npart=$(cat "/sys/class/block/${part//\/dev\//}/partition")
                umount "$part"
                parted "$disk" -a optimal -s resizepart "$npart" 100%
                yes | mkfs.ext4 -L "$label" -F -m 0 "$part"
                mount "$part"
                unset disk part npart label
        fi
```

**2.** Execute 'bash expand. sh' on the terminal and wait for the execution to complete.
