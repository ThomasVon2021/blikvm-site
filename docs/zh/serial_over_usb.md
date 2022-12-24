# 串口终端连接

可以通过串口终端对BliKVM设备进行访问。

!!! info "1.硬件连接，您应该使用USB转ttl模块将计算机的USB连接到BliKVM的uart。其中如果你使用的是Hat版本，请注意连接GPIO14和GPIO15这个串口，若是PCIe版本，连接丝印标注的Uart引脚即可"
    ![](assets/images/serial/rasp4b.png){width="300"}

!!! info "2.电脑上安装可终端登陆的工具，如在windows上可以安装putty工具"
    ![](assets/images/serial/putty.png){width="100"}

!!! info "3. putty使用说明,输入正确的COM口，默认波特率115200，选择连接方式为serial,然后点击open即可（以使用PiKVM固件为例）"
    ![](assets/images/serial/putty_conf.png){width="300"}
    ![](assets/images/serial/putty_ter01.png){width="300"}
    ![](assets/images/serial/putty_ter02.png){width="300"}