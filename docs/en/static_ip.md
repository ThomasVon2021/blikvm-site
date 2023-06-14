# **Set static IP**
To configure a static IP address on a BliKVM image, you can follow these steps:

1.  SSH into the BliKVM, If it is a read-only system, please use the `rw` command to make the system writable.
2. Edit the network interfaces configuration file using the following command:
   ```
   sudo vim /etc/dhcpcd.conf
   ```
3. Within the file, locate the section that starts with "# Example static IP configuration".
4. Uncomment the lines below that section and modify them to set your desired static IP address, gateway, DNS servers, and other network settings. For example:
   ```
   interface eth0
   static ip_address=192.168.1.100/24
   static routers=192.168.1.1
   static domain_name_servers=192.168.1.1
   ```
   Adjust the values according to your network configuration.
5. Save the changes.
6. Restart the BliKVM for the changes to take effect:
   ```
   sudo reboot
   ```

After the reboot, your BliKVM will use the configured static IP address instead of obtaining one dynamically from a DHCP server. Make sure the static IP address you choose is not already assigned to another device on the network and is within the same subnet.