# FAQ & Troubleshooting

As a first step, we recommend carefully reading our documentation. Most steps to successfully set up your BLIKVM are already described there. If you run into any issues you can check this page which will list common errors. If that still doesn't help you you're welcome to raise an [issue ticket](https://github.com/ThomasVon2021/blikvm/issues) or [join our Discord](https://discord.gg/9Y374gUF6C) for further help.

## Common questions

??? question "Can I connect multiple servers to a single BLIKVM?"
    Yes, but it requires additional work to set up. See [this page](switch-guide.md).


??? question "How can I get the access to PiKVM in my local network over Internet?"
    You can use port forwarding for port 443 on your router if it has an external IP address. In all other cases, you can use the excellent free VPN service Tailscale.


??? question "Can I use BLIKVM for gaming?"
    No, because:

    * For HDMI-CSI bridge, bus bandwidth is not enough to transmit more than 1080p60.
    * For HDMI-USB dongle, high latency and low video quality.
    * General hardware video capture differs from software streaming and introduces additional latency.
    


??? question "Can BLIKVM do 4K video?"
    * For HDMI-CSI bridge, no. There is not enough bandwidth in the CSI bus for that much data. 1080p60 will max out the bandwidth.
    * For the USB capture devices: technically yes, they will downsample to something smaller to meet the USB 2.0 bandwidth limitations, so the source may be 4k, but the stream will not.
    * The 4K real-time video will not fit through the network anyway.


??? question "Where does the cursor/video latency come from?"
    Here is the chain of transferring an image to your browser or VNC client.

    `Capture device -> Compression -> Network -> Decompression -> Rendering`

    100-200ms is very, very fast for this. But we are working to speed things up even more.


??? question "Does BLIKVM support sound?"
    Yes, all version supported.


??? question "Can I power the Pi via PoE?"
    Yes! Hat and PCIe version supported.


## First steps


??? question "What is the default password? How do I change it?"
    If you use PiKVM, there are two types of accounts: OS and PiKVM (web interface) accounts. The system account `root` can be used for SSH/UART access and has the password `root`. The web interface account is called `admin` and has the password `admin`. The PiKVM account cannot be used for SSH access and vice versa.

    To change passwords, use the following commands (under root):

    ```bash
    su -  # If you're in the webterm
    rw  # Switch filesystem to read-write mode
    passwd root  # Change OS root password
    kvmd-htpasswd set admin  # Change web ui admin password
    ro  # Back to read-only
    ```

??? question "How do I add another user?"
    If you use PiKVM software, as stated above you need to make 2 accounts, 1 for the shell, the other for the PiKVM Web UI.
    
    ```
    If you require additional users for PiKVM UI, you can use the following:
    # rw
    # su -
    # kvmd-htpasswd set <user> # Adds a new user
    # kvmd-htpasswd set <user> # Sets the password as long as the user exists
    # kvmd-htpasswd del <user> # Removes/deletes a user
    
    To add a shell/terminal account:
    # rw
    # su -
    # adduser <user>
    # passwd <user>
    ```
    Keep in mind that the more users that are added, the stream if accessed, fps will drop.

   
## Video problems

??? question "BLIKVM does not show the video from the computer at all"
    * Double-check that the video capture device is connected correctly. For the CSI bridge, this should be exactly the camera port.
    * Some laptops do not output any signal until you switch the output (usually via the FN + and an F5 key on the keyboard).
    * Your computer may have turned on sleep mode for the monitor. Move the mouse to turn it off.
    * For windows you might need to check for the active signal resolution. To change the active signal resolution you have to go to Settings>System>Display>Advanced display settings>Display adapter properties then, click "List All Models" and choose the one you want. Keep trying different Hz settings.


??? question "The video works in the booted OS, but not in the BIOS/UEFI"
    This problem appears on Intel NUC, GA-H77-DS3H, and some other devices when using a CSI bridge. All you need to do is change the EDID data. This is the information about supported resolutions that the CSI bridge reports to your computer.


??? question "Glitchy or wrong BIOS/UEFI resolution"
    On some motherboards, the BIOS may be displayed at a lower resolution, or with some rendering issues/glitches, specially on newer ASUS ones. Like this:  
    ![Image title](assets/images/faq/bios_glitch.png){width="400"}    

    This can be solved by enabling the **Compatibility Support Module (CSM)** in your BIOS, usually under the **Boot** options.

    If you can't or don't want to enable the CSM, you can try connecting a DisplayPort (DP) monitor, or a [dummy plug](http://amazon.com/s?k=displayport+dummy+plug). If you remove the DP cable/adapter the bug will reappear.

    If none of this works, try connecting the DP cable first, boot into the BIOS, disable the CSM and shutdown (do not restart) your PC. Then, boot into the BIOS and enable the CSM before shutting down your PC. Then connect the HDMI and turn your PC on again.


??? question "There is no video in GRUB2, but there is before and after"
    Sometimes this can be caused by the specifics of the BIOS/UEFI and how GRUB2 works with video.

    This can be solved by enabling the **Compatibility Support Module (CSM)** in your BIOS, usually under the **Boot** options. The video mode will be located in the same section. Switch the **Video** mode from **UEFI** to **Legacy**.


??? question "No image from computer with Linux + Awesome WM"
    Sometimes Awesome WM on Linux can't recognize a video output change on a cable. That is, if the cable was first inserted into the monitor, and then you reconnected it to BLIKVM - it may happen that you will not see the image. It seems that the problem is Awesome WM, since for example with KDE, it is not reproducable. If you turn on your workstation with BLIKVM already connected, everything will work fine.

    

## USB problems (keyboard, mouse, mass storage, etc)

??? question "What speed is the USB OTG port?"
    Per the official RPI documentation, this is a limitation of the SoC.  The OTG port is only USB2.0, so is limited to 455 Mbit/s.


## Hardware problems (Wi-Fi, ATX, etc)

??? question "If you use PiKVM software, the web UI show **FAN** error!"
    * Because the fan model used by BLIKVM hardware is different from that of PIKVM hardware, viewing the fan status through the web interface may fail in the latest system of pikvm. However, this will not affect the normal operation of BLIKVM fan. Therefore, when using the PIKVM image, as long as you ensure that the [install script](https://github.com/ThomasVon2021/blikvm/tree/master/package/kvmd-fan) displays OK, it means that the update of the kvmd fan program is successful. The threshold temperature set by the default program is 60 degrees Celsius. When the CPU temperature is detected to exceed 60 degrees Celsius, the fan will start rotating at 85% speed. If you want to modify the threshold temperature and speed, you can modify the kvmd-fan.py script, and then re-execute install.sh.

??? question "I can't connect to Wi-Fi at all!"
    * If your device is unable to connect to the Wi-Fi network that you have set up, check the 2.4 GHz Wi-Fi channel used by your Wi-Fi access point. 
      If channels 12 to 14 are used (some countries have banned these channels) try to use a channel between 1 and 11.

??? question "BLIKVM complains about low power warnings"
    * Are you using a "proper" power supply? Not one you hacked together?
    * Some USB power bricks advertise 5V 2.1A or higher, but can't deliver consistent 5V.  Best to use Raspberry Pi Foundation recommended power supplies. It should be 5.1v and 3A DC output.

??? question "When I use the PoE, do I still need to use the power OTG splitter to prevent back power on the machine usb? "
    * Only HAT version you need to use power OTG splitter to prevent back power. Generally, most hosts computer are protected back power, you do not need to usr power OTG splitter in this case.
    * BLIKVM-CM4-V2.2 and BLIKVM-PCIe version don't need.

??? question "In some board like BLIKVM-PCIe or BLIKVM-CM4-V2.2 has boot pin, how do I connect?"
    If you short them, CM4 will not start normally, but will enter the burning image mode. If your hardware version of boot has only two pins, use the jumper cap to connect the two pins as a short circuit. If you do not use the jumper cap or plug it into one pin, CM4 will start normally. If you use three boot pins of the hardware version, use the jumper cap to connect GND and another non-GND pin to indicate short circuit, and plug the jumper cap on the two GND pins or do not use it, CM4 will start normally.
    

