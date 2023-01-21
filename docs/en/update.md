# Software update introduction
## **Introduction**

!!! note "The currently available versions of the BLIKVM project are hosted in the release package of the github. The update software function needs to keep the device connected. There are currently two ways to update the software."
    * Method 1: Click the update button through the web interface, and the program will be updated automatically. Restart is required after the update.
    * Method 2: Manually run the script on the KVM terminal to update, and restart after the update.

!!! info "Common causes of upgrade errors"
    * The device is not connected to the network;
    * Network access to github is limited;
    
## **Web UI update**

!!! info "After clicking the More Options button, find the CheckUpdate button and click it. If the available version is found, the pop-up box in the figure below will appear. Click OK to enter the upgrade process. The web interface is temporarily inoperable during the upgrade process. View the current update status by manually refreshing the page. When the message of successful update appears, it means that the update has been successful. Click the restart button, and the new version of software will take effect."
    ![IMG_8366](assets/images/update/update_button.png){width="300"}
    ![IMG_8366](assets/images/update/update_info.png){width="300"}
    ![IMG_8366](assets/images/update/upgrading.png){width="300"}
    ![IMG_8366](assets/images/update/update_reboot.png){width="300"}

## **Manually run the script to update**

!!! info "In the terminal"
    ```
    sudo -i
    python3 /opt/bin/blikvm/script/update.py
    ```
   Observe the output of the terminal. When you see the message of successful upgrade, the terminal enters reboot, and the reboot takes effect.


