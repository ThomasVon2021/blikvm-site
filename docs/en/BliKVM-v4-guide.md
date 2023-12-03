# **BliKVM v4 Allwinner**

![](assets/images/v4/BliKVM-v4-front.png){width="300"}
![](assets/images/v4/BliKVM-v4-back.png){width="300"} 

BliKVM v4 is a production-ready, plug and play KVM-over-IP device that offers professional users a convenient solution **for remote server or workstation management**. It is based on Linux and fully open source. With BliKVM, you can easily **power on/off, restart your computer, configure UEFI/BIOS settings, and perform OS reinstallation using an emulated Mass Storage Device**. BliKVM simulates a keyboard, mouse, and monitor, all accessible through a web browser, ensuring a seamless user experience. **Its hardware-level access guarantees independence from specific remote ports, protocols, or services**, making it a highly flexible and reliable remote management solution for professionals!

* [BliKVM V4 Datasheet](./Datasheet-BliKVM-v4.md)

## Features
- **Video capture** (HDMI, support 4K@30Hz input)
- **Keyboard forwarding**
- **Mouse forwarding**
- **HDMI video loop through**
- **ATX** Control the server power using ATX functions
- **Fullscreen mode**
- Access via **Web UI**
- Support **multi language** switching
- Support **PoE & DC**
- Support **WiFi**
- **Serial** console port
- 1.33 inch **color** display
- **Real Time Clock (RTC)**  

## Installation Requirements
!!! note "In addition to the v4 kit, you will need the following equipment:"
    * Power adapter (5V 3A, USB-C port, or 12V 2A DC port). If you plan to use PoE (Power over Ethernet) or if the USB ports on your controlled computers provide sufficient power, a separate power adapter is not required.
    * HDMI cables (at least one). If you also need to use the HDMI loop-out interface, you will need two cables.
    * Ethernet cable(s) (provide based on your requirements). One cable is required for using the ATX power switch function, and one cable is required for using the Ethernet connection.
    * USB-C to USB-A cable (for mouse and keyboard data transmission).

!!! warning "Terminal Upgrade Notice!"
    Before upgrading, execute the following command, otherwise, after running apt-get update and apt-get upgrade, the image will fail to start.
    ```
    apt-mark hold linux-dtb-edge-sunxi64 linux-image-edge-sunxi64
    ```

 info "Video Guide: Unpacking and connecting case step by step"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/aRVzbb_g-UQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## **Installation Steps**
**1.** Open the v4 kit package and connect the BliKVM to the controlled computer according to the connection diagram shown below:
![](assets/images/v4/v4-Connection-Diagram.png)

**ATX Connection**
Please refer to the [ATX Connection Guide](./atx.md).

**2.** Once all the cables are connected, power on the BliKVM. Wait until the display shows the interface, indicating that the device has started up successfully.

**3.** Read the [**"First Steps"** guide](./first_steps.md) carefully. It provides instructions on how to find the device on the network, how to log in, change passwords, and more. Follow the steps described there and then return to this page.

**4.** **Try managing your computer using the BliKVM web interface.** Make sure you can see the image and that the keyboard and mouse are working properly. If you encounter any issues, check out our [FAQ](./faq.md) (it's very helpful). If you find no solution there, seek support in our [Discord chat room](https://discord.com/invite/9Y374gUF6C).

**5.** You can explore other pages in the wiki to discover more features of BliKVM. Enjoy your experience!

## **Video Mode**
v4 supports a maximum video input of 4K30Hz, and the default transmission resolution is 1920x1080.

## Product List

| BLIKVM v4              | 1    |
| -------------------------------------- | ---- |
| WiFi Antenna                | 1    |
| ATX adapter board                | 1    |
| ATX Dupont Cables 8pin Male to Male 60cm | 1    |
| ATX Dupont Cables 8pin Male to Female 60cm | 1    |
| 1U Rack Mounting Ears               | 2   |
| M2.5x5 Screws               | 8   |
| Silicone Bumper Pellets              | 1   |

## Dev 
If you want to develop or port software on v4 hardware yourself, you can refer to this [hardware resource description](./Dev-BliKVM-v4-Allwinner.md).

## **Buy link**
[v4 buy](https://www.aliexpress.com/item/1005005859415746.html?spm=5261.ProductManageOnline.0.0.346d2ddbm8cDsR)
