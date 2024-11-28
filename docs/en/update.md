# Software update introduction

!!! info "If you are running an older version then we recommend first reflashing and subsequently running the update process, while you are next to your BliKVM device. "

## **Introduction**

!!! note "The currently available versions of the BLIKVM project are hosted in the release package of the GitHub. The update software function needs to keep the device connected. There are currently two ways to update the software."
    - Method 1: Click the update button through the web interface, and the program will be updated automatically. A restart is required after the update.
    - Method 2: Manually run the script on the KVM terminal to update, and restart after the update.

!!! info "Common causes of upgrade errors"
    - The device is not connected to the network;
    - Network access to GitHub is limited;

!!! warning "We strongly recommend performing the update while you are in close proximity to the BliKVM hardware you are upgrading. This way if anything goes wrong you can intervene."
    - If you are familiar with command-line operations, we recommend manually updating so that you can monitor the command-line status in real time.
    - If the update is abnormal and the web interface cannot exit the update status, use ssh to get you a terminal and reboot to recover.

## **Manually run the script to update**

!!! info "In the terminal，if the system terminal shows the `ro` keyword that means your system is currently in read-only, it is necessary to use the `rw` command to make the system writable."
    ```
    sudo -i
    curl -L https://raw.githubusercontent.com/ThomasVon2021/blikvm/master/script/update.py -o /tmp/update.py && python3 /tmp/update.py
    ```
   Observe the output of the terminal. When you see the message of a successful upgrade, enter in the terminal the: `reboot` command and the reboot should take effect.

!!! warning "If you are unable to update successfully due to network issues, you can download the latest release.tar.gz package on another PC with a stable network connection and follow the instructions below for installation."
    - Download Address: https://github.com/ThomasVon2021/blikvm/releases
    - v1 v2 v3 hardware use release.tar.gz
    - v4 hardware use release-h616-v4.tar.gz
    SSH into the device terminal and use `tar -zxvf release.tar.gz` to extract the release.tar.gz file.
    ```
    sudo -i
    cd /your release path/
    python3 install_release.py --releasepath=./
    ```
    You can compare the versions before and after in `/usr/bin/blikvm/package.json`. If you have upgraded to the specified version, the installation is successful, and you can reboot for the changes to take effect.
