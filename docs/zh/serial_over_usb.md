# 串口终端连接

可以通过串口终端对BliKVM设备进行访问。

!!! info "1.硬件连接，您应该使用USB转ttl模块将计算机的USB连接到BliKVM的uart。其中如果你使用的是Hat版本，请注意连接GPIO14和GPIO15这个串口，若是PCIe版本，连接丝印标注的**GRT**引脚即可"
    ![](assets/images/serial/rasp4b.png){width="300"}

!!! info "2.电脑上安装可终端登陆的工具，如在windows上可以安装putty工具"
    ![](assets/images/serial/putty.png){width="100"}

!!! info "3. putty使用说明,输入正确的COM口，默认波特率115200，选择连接方式为serial,然后点击open即可（以使用PiKVM固件为例）"
    ![](assets/images/serial/putty_conf.png){width="300"}
    ![](assets/images/serial/putty_ter01.png){width="300"}
    ![](assets/images/serial/putty_ter02.png){width="300"}

!!! warning "如果你的电脑不能正确识别usb转ttl模块，请按照下列步骤对电脑安装驱动"
    1. 将usb-a头连接到您的主机（在本例中，它位于windows主机上）。因此，设备管理器将在其他设备中显示一个新的USB串行设备。  
    ![](assets/images/serial/drive-usb-serial.png){width="300"}
    2. 下载并提取/运行驱动程序。在这个例子中，我下载并提取了ZIP文件。  
    https://learn.sparkfun.com/tutorials/how-to-install-ch340-drivers/all
    3. 更新新USB串行设备的驱动程序，将其指向提取文件的位置，然后单击下一步，然后单击关闭。  
    ![](assets/images/serial/update-ch430-01.png){width="300"}
    ![](assets/images/serial/update-ch430-02.png){width="300"}
    4. 如果一切正确，新的USB串行设备现在应该显示在端口下的USB-serial CH340（COMX）。  
    ![](assets/images/serial/drive-ch430.png){width="300"}