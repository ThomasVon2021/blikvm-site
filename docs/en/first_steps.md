# First steps

## First power on

**Power up the device.**

!!! warning "Do not turn off the device until it's fully booted for the first time"
    After turning on the power, BLIKVM OS will perform the necessary operations on the memory card.

## Getting access to BLIKVM

By default, BliKVM receives a dynamic IP address via DHCP. The IP address will be displayed on the BliKVM monitor. If you are using DIY hardware without a monitor, use the following tips:

??? example "Finding BliKVM in the network"
    You can determine the IP address of BliKVM using the following methods:

    * **Common Method:** Access the web interface of your router and look for the allocated IP address list. The specific method depends on the router model.
    * **Linux Only:** Use the command `arp-scan --localnet`.
    * **Linux, macOS, Windows:** Download and run [Angry IP Scanner](https://angryip.org).
    * **Windows PowerShell:** Use the command `arp -a`.

In the example below, let's assume your BliKVM has obtained the address **192.168.0.100**, and you have successfully found that address using the instructions above.

??? example "Accessing BliKVM Web Interface"
    In *most* networks, you can access BliKVM in any browser using the following URL: `http://192.168.0.100/`. Google Chrome (Chromium), Firefox, and Safari work best with no extensions enabled. If one works and the other does not, it may be an issue with the browser or extensions. It is recommended to use a private browsing window or incognito mode. Internet Explorer and early versions of Microsoft Edge (non-Chromium version) are not supported.

    **The default username is `admin`, and the password is also `admin`.** Once logged in, you will have access to the main menu with essential functions. You can change system settings and passwords using the web interface's account management feature.

!!! warning "Note about accessing BliKVM web via http, not https"

??? example "Accessing BliKVM via SSH"
    SSH is the most common method for remote access in the Linux world. You can access BliKVM via SSH. This method is used for managing the device:

    * **Linux, macOS:** Open any terminal application and run: `ssh blikvm@192.168.0.100`.
    * **Windows:** Use [PuTTY](https://www.putty.org/) for the operation.

    **The default `blikvm` user password is `blikvm`.**
    You can use `sudo -i` to obtain root privileges.

??? example "Optional: Updating BliKVM Software"
    This section is not mandatory and should only be performed if you are next to the BliKVM for recovery purposes. Refer to the [Software Update Guide](./update.md) for instructions.

## Note on BliKVM OS Terminal Usage

Some configuration changes must be made under the `root` user (i.e., administrator).

!!! tip "Obtaining Root Privileges"
    * If you are logged in via SSH, use `sudo -i` to obtain root privileges.

BliKVM storage cards in versions v1, v2, and v3 are mounted in read-only mode. This protects the file system from being corrupted in the event of a sudden power outage. To edit any files and make changes, you need to remount the file system in read-write mode. You can determine the current mode by checking if `ro` or `rw` is displayed in the terminal.

!!! tip "Enabling Write Mode"
    * To enable write mode, run the command `rw`.
    * To disable write mode, run the command `ro`.
    * If you receive a "Device is busy" message, execute the `reboot` command.


## What's next?
* Set up internet access using [Port Forwarding](./port_forwarding.md) or [Tailscale VPN](./tailscale.md).
* Explore BLIKVM features using the table of contents on the left.
* Join our [Discord](https://discord.com/invite/9Y374gUF6C) to contact the community and developers.
* Check out the [GitHub](https://github.com/ThomasVon2021/blikvm) - BLIKVM is a Open Source project!


-----
## FAQ and Troubleshooting
If you have any questions or run into problems, take a look at the [FAQ](faq.md).
Seriously, it's really useful! We've probably already found a solution for it :)

For any other help and support, you can contact us via the [Discord chat](https://discord.com/invite/9Y374gUF6C).
