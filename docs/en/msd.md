# **Mass Storage Drive**

BliKVM's USB device simulation feature allows you to remotely mount images on the virtual machine's mass storage drive, making it easy to install or reinstall operating systems and other software. This can be a useful feature for system administrators who need to manage multiple virtual machines remotely. By mounting an image on the mass storage drive, you can quickly and easily set up or configure a new virtual machine without having to physically connect a USB drive or other external storage device.

Note: the size of the MSD is limited by the size of your sd card or eMMC module.

## Upload images manually (without Web UI)

!!! info "1) The following four paths should exist for using the Mass Storage Drive feature in BliKVM."
    ```
    /usr/bin/blikvm/ventoy-1.0.88
    /usr/bin/blikvm/kvmd-msd.sh
    /opt/bin/msd/user    
    /opt/bin/msd/ventoy
    ```

    The `/opt/bin/msd/user` path is particularly important as it is used to store the images that will be mounted on the virtual machine's mass storage drive. If you are using the latest official image of BliKVM and it is fully configured, these paths should already exist and you won't need to check. However, if you have installed BliKVM manually or modified the configuration, it's a good idea to confirm that these paths exist before proceeding.

!!! info "2) When you log in to BliKVM using SSH, you may find that some system directories and files are read-only, which can prevent you from making changes to the system. By executing the `sudo rw` command, you can temporarily switch the system permission to writable, allowing you to make changes to the system files."

!!! info "3) The `scp` command is used to securely copy files between remote and local hosts. In this case, we are using `scp` to copy an ISO file from our local PC to the BliKVM device so that we can mount it on the virtual machine's mass storage drive."

    Here's an example command:

    ```
    scp /path/to/local/iso blikvm@xxx.xxx.xxx.xxx:/opt/bin/msd/user/
    ```

    Replace /path/to/local/iso with the path to your ISO file on your local PC and xxx.xxx.xxx.xxx with the IP address of your BliKVM device. You will also need to enter the password for the BliKVM user when prompted.

!!! warning "Please note that this is just one way to upload the ISO file to the specified path."

!!! info "4) After you have copied the ISO file to the /opt/bin/msd/user/ directory on the BliKVM device, you need to execute the make command to create the virtual USB mass storage drive with the ISO file."

    Here's how you can do it:

    If the /opt/bin/msd/user directory contains only one ISO file, run the following command:

    ```
    sudo bash /usr/bin/blikvm/kvmd-msd.sh make
    ```

    If the /opt/bin/msd/user directory contains multiple ISO files, run the following command, replacing xxx.iso with the name of the ISO file you want to use:

    ```
    sudo bash /usr/bin/blikvm/kvmd-msd.sh make xxx.iso
    ```

!!! warning "Note"
    - The default size of the virtual USB mass storage drive is 5GB. If your ISO file is larger than 5GB, you may need to modify the `kvmd-msd.sh` script to increase the size of the virtual drive.
    - The copy process can take some time, especially if the ISO file is large or if you have a slow network connection. Please be patient and wait for the process to complete

!!! info "5) Follow this step to expand the size of the USB flash drive. Here's the original instruction with minor edits for clarity"

    If you want to expand the size of the USB flash drive, find the following line in the kvmd-msd.sh script:

    ```
    sudo dd if=/dev/zero of=ventoy.img bs=1M count=5120 status=progress;
    ```

    To change the size, modify the count value, which is currently set to 5120. For example, if you want to increase the size to 10GB, change it to count=10240. Save the file after making changes."

!!! info "6) Use the following command to connect the BliKVM device to the MSD"

    ```
    sudo bash  /usr/bin/blikvm/kvmd-msd.sh conn
    ```

!!! info "7) Use the following command to disconnect the BliKVM device to the MSD"

    ```
    sudo bash  /usr/bin/blikvm/kvmd-msd.sh disconn
    ```

!!! info "8) Use the following command to disconnect the BliKVM device to remove the MSD"

    ```
    sudo bash  /usr/bin/blikvm/kvmd-msd.sh clean
    ```

!!! info "9) Now you need to put the system back into read-only mode by executing the `sudo ro` command."

!!! info "10) This step involves restarting the PC through the web interface, entering the BIOS settings, and modifying the boot priority to set the BliKVM USB as the first boot option."

!!! info "11) After completing the previous steps, you can now select the desired operating system and proceed with the installation process. Here are the general steps you can follow"

    ```
    a) Power on the BliKVM device.
    b) Enter the BIOS by pressing the corresponding key during startup (usually F2 or Del).
    c) Set the BliKVM USB as the first boot option.
    d) Save and exit the BIOS.
    e) Wait for the BliKVM device to boot from the BliKVM USB.
    f) Follow the on-screen instructions to select the desired operating system and configure the installation options.
    g) When prompted, select the partition where you want to install the operating system.
    h) Format the partition if necessary.
    i) Proceed with the installation process and wait for it to complete.
    j) Once the installation is finished, you can disconnect the blikvm USB and boot from the newly installed operating system.
    ```

!!! warning "Note that the specific steps may vary depending on the operating system you are installing and the installation process itself. It's always a good idea to refer to the installation documentation or seek assistance if you encounter any issues."

## Upload images through Web UI
Under development
