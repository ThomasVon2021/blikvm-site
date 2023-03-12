# Wifi Configure
!!! warning "Because BLIKVM has many kinds of hardware and supports different OS, such as BLIKVM OS and PiKVM OS, different OS confifure wifi methods may not be the same. Please confirm the hardware and OS usage before using the method in this document."
    1. Please confirm that the hardware you use supports wifi function, for example, the CM400200 version does not have wifi function;
    2. If the SOC of KVM hardware is CM4, please confirm whether wifi antenna is connected;
    3. PiKVM OS is arch linux;
    4. BLIKVM OS raspberry pi series is debian system, and H616 series is armbian system;

## **Use raspi-config for wifi configure on raspberry pi debian system**

1. Log in to ssh, command: ssh blikvm@ip
2. The system is reloaded as writable. Command: rw
3. Start raspi-config, command: sudo raspi-config
4. Select System Options
5. Select Wireless LAN
6. Select the country where wifi is located, and China will select CN. If it has been set before, this step will skip to 7
7. Enter the ssid (name) of Wi-Fi
8. Enter the Wi-Fi password. If there is no password, press Enter directly
9. At this time, you will return to the interface in Step 4, press the tab key to select<Finish>, and press Enter
10. Check whether to connect to wifi. Command: ifconfig wlan0. If you see the ip obtained, you are connected
11. Mount the system as read-only. Command: ro

