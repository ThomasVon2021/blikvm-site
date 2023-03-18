# Serial-over-USB connection

The BliKVM device can be accessed through the serial port terminal.

!!! info "1.For hardware connection, you should use the USB to ttl module to connect the USB of the computer to the uart of BliKVM. If you are using the Hat version, please connect the serial ports GPIO14 and GPIO15. If you are using the PCIe version, connect the **GTR** pin marked by the PCB"
    ![](assets/images/serial/rasp4b.png){width="300"}

!!! info "2.Install terminal login tools on the computer. For example, you can install putty tools on Windows"
    ![](assets/images/serial/putty.png){width="100"}

!!! info "3. Use the putty instruction. Enter the correct COM port. The default baud rate is 115200. Select serial as the connection method, and then click Open（Use PiKVM firmware as an example）"
    ![](assets/images/serial/putty_conf.png){width="300"}
    ![](assets/images/serial/putty_ter01.png){width="300"}
    ![](assets/images/serial/putty_ter02.png){width="300"}

!!! warning "If your computer cannot correctly recognize the USB to TTL module, please follow the steps below to install the driver for your computer"
    1. Connect the usb-a connector to your admin host (in this example, it's on a windows host). As a result, device manager will show a new USB Serial device in Other devices.   
    ![](assets/images/serial/drive-usb-serial.png){width="300"}
    2. Download and extract/run drivers. In this example, I downloaded and extracted the ZIP file.   
    https://learn.sparkfun.com/tutorials/how-to-install-ch340-drivers/all
    3. Update driver for the new USB Serial device, point it to where you extracted the files, and click Next then Close.  
    ![](assets/images/serial/update-ch430-01.png){width="300"}
    ![](assets/images/serial/update-ch430-02.png){width="300"}
    4. If done right, the new USB serial device should now show up under Ports as USB-SERIAL CH340 (COMX).    
    ![](assets/images/serial/drive-ch430.png){width="300"}