# Serial-over-USB connection

The BliKVM device can be accessed through the serial port terminal.

!!! info "1.For hardware connection, you should use the USB to ttl module to connect the USB of the computer to the uart of BliKVM. If you are using the Hat version, please connect the serial ports GPIO14 and GPIO15. If you are using the PCIe version, connect the Uart pin marked by the PCB"
    ![](assets/images/serial/rasp4b.png){width="300"}

!!! info "2.Install terminal login tools on the computer. For example, you can install putty tools on Windows"
    ![](assets/images/serial/putty.png){width="100"}

!!! info "3. Use the putty instruction. Enter the correct COM port. The default baud rate is 115200. Select serial as the connection method, and then click Open（Use PiKVM firmware as an example）"
    ![](assets/images/serial/putty_conf.png){width="300"}
    ![](assets/images/serial/putty_ter01.png){width="300"}
    ![](assets/images/serial/putty_ter02.png){width="300"}