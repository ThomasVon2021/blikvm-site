# Software update introduction

!!! info "If you are running an older version then we recommend first reflashing and subsequently running the update process, while you are next to your BliKVM device. "

## **Introduction**

!!! note "The currently available versions of the BLIKVM project are hosted in the release package of the GitHub. The update software function needs to keep the device connected. There are currently two ways to update the software."
    - Method 1: Manually run the script on the KVM terminal to update.
    - Method 2: Manually download the release package, then run the installation update on the KVM terminal.

!!! info "Common causes of upgrade errors"
    - The device is not connected to the network;
    - Network access to GitHub is restricted;
    - Your local version may be incompatible with the latest version. If the update is successful but behaves abnormally, you need to reflash the latest system to recover;
    - You cannot use the web SSH terminal for the update because the web program will terminate during the update process, which will cause the installation to never complete.

!!! warning "We strongly recommend performing the update while you are in close proximity to the BliKVM hardware you are upgrading. This way if anything goes wrong you can intervene."
    - If you are familiar with command-line operations, we recommend manually updating so that you can monitor the command-line status in real time.
    - If the update is abnormal and the web interface cannot exit the update status, use ssh to get you a terminal and reboot to recover.

## **Manually run the script to update**

!!! info "In the terminal，if the system terminal shows the `ro` keyword that means your system is currently in read-only, it is necessary to use the `rw` command to make the system writable."
    ```
    sudo -i
    curl -L https://raw.githubusercontent.com/blikvm/blikvm/master/script/update.py -o /tmp/update.py && python3 /tmp/update.py
    ```
   Observe the output of the terminal. 

!!! warning "If you are unable to update successfully due to network issues, you can download the latest release package on a PC with a stable network and then install it using the following commands."
    - Download link: https://github.com/blikvm/blikvm/releases
    - For v1, v2, and v3 hardware, use blikvm-v1-v2-v3.deb
    - For v4 hardware, use blikvm-v4.deb
    ssh into the device terminal and use `dpkg -i xxx.deb`

You can compare the version in /usr/bin/blikvm/package.json before and after the update. If it has been upgraded to the specified version, the update is successful.
