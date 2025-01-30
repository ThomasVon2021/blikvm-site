# Wifi Configure

!!! warning "Because BLIKVM has many kinds of hardware and supports different OS, such as BLIKVM OS and PiKVM OS, different OS confifure wifi methods may not be the same. Please confirm the hardware and OS usage before using the method in this document."
    1. Please confirm that the hardware you use supports wifi function, for example, the CM400200 version does not have wifi function;
    2. If the SOC of KVM hardware is CM4, please confirm whether wifi antenna is connected;
    3. PiKVM OS is arch linux;
    4. BLIKVM OS raspberry pi series is debian system, and v4 series is armbian system;

## **v1 v2 v3 Use raspi-config for Wi-Fi config on Raspberry Pi Debian systems**

1. Log in to SSH. Command: `ssh blikvm@ip`
2. Mount the system as writable. Command: `rw`
3. Start raspi-config. Command: `sudo raspi-config`
4. Select System Options
5. Select Wireless LAN
6. Select the country where Wi-Fi is located, and China will select CN. If it has been set before, this step will skip to 7
7. Enter the Wi-Fi SSID (name)
8. Enter the Wi-Fi password. If there is no password, press **Enter** directly
9. At this time, you will return to the interface in Step 4, press the **tab** key to select **Finish**, then press **Enter**
10. Check whether to connect to wifi. Command: ifconfig wlan0. If you see the ip obtained, you are connected
11. Mount the system as read-only. Command: `ro`

## **v4 Hardware using Armbian System with armbian-config**
1. Log in via SSH using the command: `ssh blikvm@ip` to access the Armbian system. If it is a read-only system, you need to first use the command `rw` to make it read-write, and use the command `sudo chmod 777 -R /etc/NetworkManager/system-connections` to give the corresponding folder permissions. After modifying the permissions, you need to restart the NetworkManager service for the changes to take effect using the command `systemctl restart NetworkManager`.
2. Enter the following command to launch the `armbian-config` tool:

```bash
sudo armbian-config
```

3. In the `armbian-config` menu, navigate and select options using the arrow keys and press **Enter**.
4. Scroll down to the "Network" option using the arrow keys and press **Enter** to enter the submenu.
5. In the "Network" submenu, select the "Wireless" option and press **Enter** to enter the Wi-Fi configuration menu.
6. In the Wi-Fi configuration menu, select the "Connect to Wi-Fi" option and press **Enter** to enter the Wi-Fi connection setup.
7. `armbian-config` will list the available wireless interfaces and already configured networks. Select the wireless interface you want to connect to and press **Enter**.
8. `armbian-config` will display the list of available Wi-Fi networks. Use the arrow keys to select the Wi-Fi network you want to connect to and press **Enter**.
9. If the Wi-Fi network is password-protected, `armbian-config` will prompt you to enter the Wi-Fi password. Enter the password and press **Enter**.
10. Wait for a moment while the Armbian system attempts to connect to the specified Wi-Fi network. If the connection is successful, you will see a corresponding message on the screen.
11. Exit the `armbian-config` tool.

Please note that the menu options and configurations mentioned above may vary slightly depending on the specific version of the Armbian system. Make sure to follow the appropriate steps based on your system version and configuration.
