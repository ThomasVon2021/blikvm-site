# **Mass Storage Drive**

!!! info "Reinstall the system Video"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/MDuS3bHsVmc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

BliKVM supports USB drive emulation, allowing remote mounting of images for system reinstallation. Additionally, if you need to copy files from the controlled device, BliKVM also provides a command-line method.

## Web UI
The entry point for the MSD virtual USB drive is:
![](assets/images/msd/web-ui.png)

## Manual (without using Web UI)

!!! info "1. Ensure the following four paths exist. If you are using the latest BliKVM image, no check is needed. The /opt/bin/msd/user path is used to store system images."
  ```
  /mnt/exec/release/lib/ventoy-1.0.99
  /mnt/exec/release/lib/kvmd-msd.sh
  /mnt/msd/user    
  /mnt/msd/ventoy
  ```

!!! info "2. Log in to the BliKVM terminal via SSH, with both the username and password as blikvm. Use the rw command to make the read-only system writable."
  ```
    sudo rw
  ```

!!! info "3. On your control computer, use the following command in the terminal to copy the ISO image file to the specified path in the BliKVM image."
  ```
    scp ***.iso blikvm@xxx.xxx.xxx.xxx:/mnt/msd/user/
  ```	
!!! warning "Of course, you can also use any other method you are familiar with to copy the ISO image file to the specified path."
  
!!! info "4. Use one of the following commands to copy the image to the emulated USB drive. The default size of the USB drive is set to 5GB. If you need more space, you need to modify the kvmd-msd.sh script."
  - If there is only one image file in the /mnt/msd/user path, you can use this command directly.
  ```
     sudo bash /mnt/exec/release/lib/kvmd-msd.sh -c make
  ```
  - If there is more than one image file in the /mnt/msd/user path, you can specify the file using the following command. **xxx.iso** represents the image name. The number after -s is the size of the USB drive in GB, which can be modified according to your needs. The string after -n is the USB drive name.
  ```
    sudo bash /mnt/exec/release/lib/kvmd-msd.sh -c make -s 5 -n ventoy -f xxx.iso
  ```

!!! warning "The cp process is very slow, please be patient."

!!! info "5. Run the following command to connect the emulated USB drive to your controlled device."
  ```
    sudo bash  /mnt/exec/release/lib/kvmd-msd.sh -c conn
  ```

!!! info "6. Run the following command to eject the emulated USB drive from your controlled device."		
  ```
    sudo bash  /mnt/exec/release/lib/kvmd-msd.sh -c disconn
  ```

!!! info "7. Run the following command to clear the emulated USB drive, which will release the corresponding space."		
  ```
    sudo bash  /mnt/exec/release/lib/kvmd-msd.sh -c clean
  ```

!!! info "8. If everything is correct, you should now see the emulated USB drive in a PC system. Restart your PC through the web, then use the shortcut key (many computers use F2) to enter the BIOS, change the boot priority, and set the emulated USB drive device to the highest priority."		

!!! info "9. According to the BIOS system prompts, save and restart to enter the Ventoy boot interface for system reinstallation."

## General USB Drive
To transfer general files, note that the file names must be in English, as Chinese characters will appear garbled. The conn, disconn, and clean commands are still valid for general USB drives.
### Create a General USB Drive
The number after -s is the size of the general USB drive in GB. The larger the capacity, the longer the creation time. Please set it according to your actual situation. -t must be other.
```
sudo bash /mnt/exec/release/lib/kvmd-msd.sh -c make -s 4 -t other
```
### File Transfer from User Computer ==> KVM ==> Controlled Computer

1. First, you need to send the file from the user control computer to the KVM.
```
scp xxx blikvm@xxxx:/mnt/msd/user/
```
2. Synchronize the file to the controlled computer and connect it.
```
sudo bash /mnt/exec/release/lib/kvmd-msd.sh -c forward
```
For new content that needs to be transferred from the user computer to the controlled computer, repeat steps 1 and 2.

### File Transfer from Controlled Computer ==> KVM ==> User Computer
1. First, copy the file to the emulated virtual USB drive on the controlled computer, then execute the following command to copy the file to the /mnt/msd/user/ directory on the KVM.
```
sudo bash /mnt/exec/release/lib/kvmd-msd.sh -c rever
```
2. Copy the file from the KVM to the user computer.
```
scp blikvm@xxxx:/mnt/msd/user/*  .
```

## **Disabling Mass Storage**
In rare cases, if the BIOS/UEFI cannot correctly recognize and even refuses to use the USB keyboard and mouse, it may be necessary to disable mass storage emulation.
Edit the `enable` field in `/mnt/exec/release/config/app.json` to `false`, then restart the KVM to disable mass storage emulation.
```json
"msd": {
  "enable": true,
  "isoFilePath": "/mnt/msd/user",
  "shell": "./lib/kvmd-msd.sh",
  "stateFilePath": "/mnt/msd/config/msd.json",
  "tusPort": 10002
}
```
   
