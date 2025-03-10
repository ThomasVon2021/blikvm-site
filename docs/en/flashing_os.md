# Flasing the OS image

!!! warning "Micro-SD Card Requirements"
    - Minimum **16 Gb**
    - **Class 10** is strongly recommended
    - When flashing an image, if using tools such as RPi Imager, please do not make any presets before flashing, otherwise it will cause the image to fail to start.

!!! Example "Why are there two versions of software, BLIKVM and PiKVM? What is the difference between the two versions? Which one should I choose? Can I use the official image of PiKVM?"
    - At the beginning of the BLIKVM project, the hardware was developed, and the software directly used PiKVM. With the continuous progress of the project, BLIKVM has developed its own software version of new architecture, which also lays the foundation for deeper cooperation with its own hardware;
    - The core functions of BLIKVM and PiKVM are the same for users. Some subdivision functions are not the same. For example, BLIKVM supports multiple languages;
    - Select according to your own use experience;
    - You can use the PiKVM official image, but you need to make some adaptations according to the different hardware, mainly involving screens, fans, etc. Since the PiKVM official image is always updated, the specific adaptations need to be seen according to the specific situation you encounter at that time;

## Download the image

!!! info "Users who need to run PiKVM on v4 by yourself can refer to this [doc](https://github.com/RainCat1998/Bli-PiKVM)."

### BliKVM Versions and Software Image Compatibility

!!! info "The following BliKVM versions use the same BliKVM v1-3 software image:"
    [BliKVM v1 CM4 BliKVM v2 PCIe BliKVM v3 HAT](https://zcwrego195.feishu.cn/drive/folder/JgKdfGYX0lxLQ9ddqCscxwFnnhb?from=from_copylink)

!!! info "BliKVM v4 Allwinner, uses a separate Allwinner BliKVM image."
    [BliKVM v4](https://zcwrego195.feishu.cn/drive/folder/MhU7f2LFKlIe4JdJjKMcXDzDnoc?from=from_copylink)

!!! info "Web UI"
    The web UI is consistent across all supported versions for easy remote administration. 
    ![Image title](assets/images/flash_os/english-web-ui.png){width="300"}
    ![Image title](assets/images/flash_os/chinese-web-ui.png){width="300"}

### Base on PiKVM software

!!! info "Raspberry 4B and CM4 board use different PiKVM software image. After entering the link, you can see the image named with each hardware version (HAT CM4 PCIe)"
    * **[PiKVM image](https://zcwrego195.feishu.cn/drive/folder/fldcntj64syIznoYuTdRFattP2f)**

## Flash the image

!!! tip
    Ignore request to format your sd card, this step is not nessessary. Choose the most suitable method for you.
    [How to flash the eMMC on a Raspberry Pi Compute Module 4](https://www.youtube.com/watch?v=jp_mF1RknU4)

### Board Link

If you use a CM4 with eMMC (like the CM4102016). You can use the v1 or v2 board to flash the eMMC. If your CM4 doesn't have eMMC, your device can just use a SD card to boot from. You don't need to look into this any further. Just flash to the SD card instead.
First, use the jumper cap to short the boot pin (allowing you flash the EMMC memory).
!!! info "If you use BLIKVM CM4 version"
    Then connect the data cable to the USB OTG interface. Power on blikvm and observe the act light, the green light is always on.  
    ![Image title](assets/images/flash_os/flash_led-300x300.png){width="300"}
!!! info "If you use BLIKVM PCIe version"
    Then connect the data cable to the USB-PC interface. Power on blikvm and observe the ACT and PWR LED isn't light.
    After initialize EMMC through the usbboot/rpiboot, the ACT and PWR LED light is always on.  
    ![Image title](assets/images/flash_os/pcie-flash-boot.jpg){width="300"}
    ![Image title](assets/images/flash_os/pcie_flash_after_rpiboot.jpg){width="300"}

!!! tip "EMMC knowledge"
    If you use Raspberry Pi compute modules such as CM3 eMMC or CM4 eMMC version，you can initialize eMMC through the [usbboot](https://github.com/raspberrypi/usbboot) project. Note that the eMMC board version **cannot** use the SD card to boot the image.
    Instead, you need to flash the eMMC storage by using the usbboot project that emulates USB Mass Storage Device (MSD).
    From this video you can learn how-to flash the image quickly. [How to flash the eMMC on a Raspberry Pi Compute Module 4 video](https://www.youtube.com/watch?v=jp_mF1RknU4)

**Taking Ubuntu system as an example:**

### Linux usbboot

If you use an Micro-SD Card, you can skip the following steps and go to the next chapter down below.

```bash
sudo apt install git libusb-1.0-0-dev pkg-config build-essential
git clone --depth=1 https://github.com/raspberrypi/usbboot
cd usbboot
make
sudo ./rpiboot
```

If the content in the image below appears, that indicates that the eMMC initialization was successful. The next step is to flash the image to your eMMC chip.
![Image title](assets/images/flash_os/flash_rpiboot.png){width="300"}

### Flash the Image (Linux, MacOS and Windows)

!!! warning "Please do not make any additional settings to the image in RPi Imager, as this will most likely cause the image to fail to boot or repeatedly restart."

We are using the "RPi Imager" application to flash the image in this example.

1. Download and install **the latest version** of [RPi Imager](https://github.com/raspberrypi/rpi-imager/releases).

2. Run RPi Imager:  
![Image title](assets/images/flash_os/flash_rpi.png){width="300"}

3. Press **CHOOSE OS** and select **Use custom** image at bottom of the list:  
![Image title](assets/images/flash_os/flash_choose_os.png){width="300"}

4. After clicking on this item, select the image file (`.img.xz`), then click **CHOOSE STORAGE**:  
![Image title](assets/images/flash_os/flash_img.png){width="300"}

5. Insert the memory card into the card reader. Choose the card reader from this list (or eMMC flash storage, in case you are using a Raspberry Pi Compute module with a eMMC chip). **Be careful**
and choose the right device:

    ![Image title](assets/images/flash_os/flash_storage.png){width="300"}

6. After choosing the memory card, press the **WRITE** button. Confirm the operation when you are asked about it:  
![Image title](assets/images/flash_os/flash_write.png){width="300"}

7. Wait for the process to finish. Get yourself a coffee or do some stretching :)  
!!! tip
    The process may hang at 99% for a long time, this is okay, just wait for it to complete
![Image title](assets/images/flash_os/flash_wait_process.png){width="300"}

8.Remove the memory card after successful completion:  

![Image title](assets/images/flash_os/flash_write_successful.png){width="300"}

!!! tip
    If an error occurs during flashing or booting, repeat the process.
