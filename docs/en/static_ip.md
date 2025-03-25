# **Set static IP**

To configure a static IP address on a BliKVM image, you can follow these steps:

## v1 v2 v3 versions - Debian

1. SSH into the BliKVM, If it is a read-only system, please use the `rw` command to make the system writable.
2. Edit the network interfaces configuration file using the following command:

   ```bash
   sudo vim /etc/NetworkManager/NetworkManager.conf
   # make sure ifupdown if true
   [main]
   dns=none
   plugins=ifupdown,keyfile

   [ifupdown]
   managed=true

   [device]
   wifi.scan-rand-mac-address=no
   ```

3. example `vim /etc/network/interfaces`.

   ```bash
   source /etc/network/interfaces.d/*
   auto eth0
   iface eth0 inet static
   address 192.168.1.100
   netmask 255.255.255.0
   gateway 192.168.1.1
   ```

   Adjust the values according to your network configuration.

5. Save the changes.
6. Restart the BliKVM for the changes to take effect:

   ```bash
   sudo reboot
   ```

## v4 version - armbian

1. SSH into the BliKVM, If it is a read-only system, please use the `rw` command to make the system writable.
2. Edit the network interfaces configuration file using the following command:

   ```bash
   sudo vim /etc/network/interfaces
   ```

3. Within the file, locate the section that starts with `# Example static IP configuration`.
4. Uncomment the lines below that section and modify them to set your desired static IP address, gateway, DNS servers, and other network settings.

   For example:

   ```bash
   source /etc/network/interfaces.d/*
   auto eth0
   allow-hotplug eth0
   iface eth0 inet static
   address 192.168.0.100
   netmask 255.255.255.0
   gateway 192.168.0.1
   dns-nameservers 192.168.0.1
   ```

   Adjust the values according to your network configuration.

5. Save the changes.
6. Restart the NetworkManager for the changes to take effect:

   ```bash
   sudo systemctl restart NetworkManager
   ```

After the reboot, your BliKVM will use the configured static IP address instead of obtaining one dynamically from a DHCP server. Make sure the static IP address you choose is not already assigned to another device on the network and is within the same subnet.
