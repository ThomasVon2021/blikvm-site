# **BliKVM v4**

![](assets/images/v4/BliKVM-v4-front.png){width="300"}
![](assets/images/v4/BliKVM-v4-back.png){width="300"} 

BliKVM v4 is a production-ready, plug and play KVM-over-IP device that offers professional users a convenient solution **for remote server or workstation management**. It is based on Linux and fully open source. With BliKVM, you can easily **power on/off, restart your computer, configure UEFI/BIOS settings, and perform OS reinstallation using an emulated Mass Storage Device**. BliKVM simulates a keyboard, mouse, and monitor, all accessible through a web browser, ensuring a seamless user experience. **Its hardware-level access guarantees independence from specific remote ports, protocols, or services**, making it a highly flexible and reliable remote management solution for professionals!

* [BliKVM V4 Datasheet](./Datasheet-BliKVM-v4.md)

## Installation Requirements
!!! note "In addition to the v4 kit, you will need the following equipment:"
    * Power adapter (5V 3A, USB-A port, or 12V 2A DC port). If you plan to use PoE (Power over Ethernet) or if the USB ports on your controlled computers provide sufficient power, a separate power adapter is not required.
    * HDMI cables (at least one). If you also need to use the HDMI loop-out interface, you will need two cables.
    * Ethernet cable(s) (provide based on your requirements). One cable is required for using the ATX power switch function, and one cable is required for using the Ethernet connection.
    * USB-C to USB-A cable (for mouse and keyboard data transmission).

## **Installation Steps**
**1.** Open the v4 kit package and connect the BliKVM to the controlled computer according to the connection diagram shown below:
![](assets/images/v4/v4-Connection-Diagram.png)

**ATX Connection**
Please refer to the [ATX Connection Guide](./atx.md).

**2.** Once all the cables are connected, power on the BliKVM. Wait until the display shows the interface, indicating that the device has started up successfully.

**3.** Read the **"First Steps"** guide ([link](./first_steps.md)) carefully. It provides instructions on how to find the device on the network, how to log in, change passwords, and more. Follow the steps described there and then return to this page.

**4.** **Try managing your computer using the BliKVM web interface.** Make sure you can see the image and that the keyboard and mouse are working properly. If you encounter any issues, check out our [FAQ](./faq.md) (it's very helpful). If you find no solution there, seek support in our [Discord chat room](https://discord.com/invite/9Y374gUF6C).

**5.** You can explore other pages in the wiki to discover more features of BliKVM. Enjoy your experience!

## **Video Mode**
v4 supports a maximum video input of 4K30Hz, and the default transmission resolution is 1920x1080.
