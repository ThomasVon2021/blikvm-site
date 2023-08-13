# Flasing the OS image

!!! warning "Micro-SD Card Requirements"
    * Minimum **16 Gb**
    * **Class 10** is strongly recommended

!!! Example "Why are there two versions of software, BLIKVM and PiKVM? What is the difference between the two versions? Which one should I choose? Can I use the official image of PiKVM?"
    * At the beginning of the BLIKVM project, the hardware was developed, and the software directly used PiKVM. With the continuous progress of the project, BLIKVM has developed its own software version of new architecture, which also lays the foundation for deeper cooperation with its own hardware;
    * The core functions of BLIKVM and PiKVM are the same for users. Some subdivision functions are not the same. For example, BLIKVM supports multiple languages;
    * Select according to your own use experience;
    * You can use the PiKVM official image, but you need to make some adaptations according to the different hardware, mainly involving screens, fans, etc. Since the PiKVM official image is always updated, the specific adaptations need to be seen according to the specific situation you encounter at that time;

## Download the image
### BLIKVM software
!!! info "You can find BliKVM v1 CM4, v2 PCIe, v3 HAT, v4 Allwinner BLIKVM software image, v1 v2 v3 use a same image."
    * **[BLIKVM image ](https://zcwrego195.feishu.cn/drive/folder/fldcn0KhmkuC2DC8nKWcHAMLA6f)**  
    The web UI style is as follows:  
    ![Image title](assets/images/flash_os/english-web-ui.png){width="300"}
    ![Image title](assets/images/flash_os/chinese-web-ui.png){width="300"}

### Base on PiKVM software
!!! info "Raspberry 4B and CM4 board use different PiKVM software image. After entering the link, you can see the image named with each hardware version (HAT CM4 PCIe)"
    * **[PiKVM image](https://drive.google.com/drive/folders/1DcpxSzjbhM7wijaldql2UI4pUyEhOTCJ?usp=share_link)**

## Flash the image

!!! tip
    Ignore request to format your sd card, this step is not nessessary. Choose the most suitable method for you.
    [How to flash the eMMC on a Raspberry Pi Compute Module 4](https://www.youtube.com/watch?v=jp_mF1RknU4)

### Board Link
First, use the jumper cap to short the boot pin.
!!! info "If you use BLIKVM CM4 version"
    Then connect the data cable to the USB OTG interface. Power on blikvm and observe the act light, the green light is always on.  
    ![Image title](assets/images/flash_os/flash_led-300x300.png){width="300"}
!!! info "If you use BLIKVM PCIe version"
    Then connect the data cable to the USB-PC interface. Power on blikvm and observe the ACT and PWR LED isn't light. 
    After initialize EMMC through the usbboot/rpiboot, the ACT and PWR LED light is always on.  
    ![Image title](assets/images/flash_os/pcie-flash-boot.jpg){width="300"}
    ![Image title](assets/images/flash_os/pcie_flash_after_rpiboot.jpg){width="300"}
    
!!! tip "EMMC knowledge"
    If you use raspberry pi computing modules such as CM3 or CM4 EMMC，you can initialize EMMC through the usbboot. Note that the EMMC version cannot directly use the SD card to start the image.
    From this video you can learn how to flash image quickly.[How to flash the eMMC on a Raspberry Pi Compute Module 4 video](https://www.youtube.com/watch?v=jp_mF1RknU4)

**Taking Ubuntu system as an example:**
###  Linux usbboot
If you use an Micro-SD Card, you don't need to care about that.
```
# sudo apt-get install libusb-1.0-0-dev  
# git clone --depth=1 https://github.com/raspberrypi/usbboot
# cd usbboot
# make
# sudo ./rpiboot
```
If the content shown in the figure below appears, it indicates that EMMC initialization is successful.  
![Image title](assets/images/flash_os/flash_rpiboot.png){width="300"}

### Using RPi Imager (Linux, MacOS and Windows)

1. Download and install **the latest version** of [RPi Imager](https://github.com/raspberrypi/rpi-imager/releases).

2. Run RPi Imager:  
![Image title](assets/images/flash_os/flash_rpi.png){width="300"}  

3. Press **CHOOSE OS** and select **Use custom** image at bottom of the list:  
![Image title](assets/images/flash_os/flash_choose_os.png){width="300"}

4. After clicking on this item, select the image file (`.img.xz`), then click **CHOOSE STORAGE**:  
![Image title](assets/images/flash_os/flash_img.png){width="300"}

5. Insert the memory card into the card reader. Choose the card reader from this list. **Be careful** 
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
    If an error occurs during flashing or booting PiKVM, repeat the process.