# First steps

## First power on

**Power up the device.**

!!! warning "Do not turn off the device until it's fully booted for the first time"
    After turning on the power, BLIKVM OS will perform the necessary operations on the memory card.

## Getting access to BLIKVM

By default, BLIKVM receives a dynamic IP address via DHCP.

??? example "Finding BLIKVM in the network"
    To determine the IP address of your BLIKVM, use one of the following methods:

    * **Common way:** Open the web interface of your router and find the list of issued IP addresses there. It depends on the router model.
    * **Linux-only:** Use command `arp-scan --localnet`.
    * **Linux, MacOS, Windows:** Download and run [Angry IP Scanner](https://angryip.org).
    * **Windows PowerShell:** Use command `arp -a`.
    
    In order to find your RaspberryPi using the arp commands, you need to look for the following MAC Address's: B827EB, DCA632 or E45F01

For future examples, let's assume that your BLIKVM has received the address **192.168.0.100**, which you have successfully detected using the instructions above. Then your device was assigned a hostname: **blikvm**.

??? example "Access to BLIKVM Web Interface"
    In MOST networks you should be able to reach BLIKVM via any browser with the URL `https://192.168.0.100/`. Google Chrome (Chromium), Firefox and Safari work best with 0 extensions enabled, if one works but the others do not, this is a browser/extension issue. Its advised you use Private window or Incog mode. Microsoft Edge and Internet Explorer are not supported.
    **The default user is admin, the password is also admin**. After logging in, you will get access to the menu with the main functions.

??? example "Access to BLIKVM via SSH"
    SSH is the most common remote access method in the Linux world. BLIKVM is accessible via SSH. This method is used to manage the device:

    * **Linux, MacOS:** Open any terminal application and run: `ssh blikvm@192.168.0.100`.
    * **Windows:** Use [PuTTY](https://www.putty.org/) for this.

    **The default `blikvm` password is `blikvm`.**

??? example "OPTIONAL: Update BLIKVM software"
    See [this page](update.md).

## What's next?
* Explore BLIKVM features using the table of contents on the left.
* Join our [Discord](https://discord.com/invite/9Y374gUF6C) to contact the community and developers.
* Check out the [GitHub](https://github.com/ThomasVon2021/blikvm) - BLIKVM is a Open Source project!


-----
## FAQ and Troubleshooting
If you have any questions or run into problems, take a look at the [FAQ](faq.md).
Seriously, it's really useful! We've probably already found a solution for it :)

For any other help and support, you can contact us via the [Discord chat](https://discord.com/invite/9Y374gUF6C).
