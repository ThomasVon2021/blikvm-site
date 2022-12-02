# Перепрошивка образа ОС

!!! warning "Требования к картам microSD"
    * Минимум **16 Гб**
    * **Класс 10** настоятельно рекомендуется

## Загрузка образа

* **[PiKVM image (BLIKVM-CM4)](https://drive.google.com/file/d/1EauTgw3TKsVGRtxka3BcU2O-DRcNZgbE/view?usp=sharing)**
* **[PiKVM image (BLIKVM-PCIe)](https://drive.google.com/file/d/1EauTgw3TKsVGRtxka3BcU2O-DRcNZgbE/view?usp=sharing)**
* **[PiKVM image (BLIKVM-HAT)](https://drive.google.com/file/d/1bsronRZoaimy8MLIMhAAoKvtStGXub2O/view?usp=sharing)**

## Прошивка

!!! tip
    Игнорируйте запрос на форматирование вашей SD-карты, этот шаг не является необходимым. Выберите наиболее подходящий для вас метод.
    [Как прошить eMMC на Raspberry Pi 4](https://www.youtube.com/watch?v=jp_mF1RknU4)

### Подключение платы
Сначала используйте колпачок перемычки, чтобы закоротить загрузочный пин.
!!! info "Если вы используете версию BLIKVM CM4"
    Подключите кабель для передачи данных к интерфейсу USB OTG. Включите blikvm и следите за индикатором выполнения (ACT), зеленый индикатор всегда горит.  
    ![Image title](assets/images/flash_os/flash_led-300x300.png){width="300"}
!!! info "Если вы используете версию BLIKVM PCIe"
    Подключите кабель для передачи данных к интерфейсу USB-PC. Включите blikvm и следите за индикатором выполнения (ACT), PWR LED не горит. 
    После инициализации EMMC через usbboot/rpiboot индикатор ACT и PWR LED всегда горят.  
    ![Image title](assets/images/flash_os/pcie-flash-boot.jpg){width="300"}
    ![Image title](assets/images/flash_os/pcie_flash_after_rpiboot.jpg){width="300"}
    
!!! tip "Информация о EMMC"
    Если вы используете raspberry pi, такие как CM3 или CM4 с EMMC, вы можете инициализировать EMMC через usbboot. Обратите внимание, что версия EMMC не может напрямую использовать SD-карту для запуска образа. Из этого видео вы можете узнать, как быстро прошить образ. [Видео: Как прошить eMMC на Raspberry Pi 4](https://www.youtube.com/watch?v=jp_mF1RknU4)

**Возьмем в качестве примера систему Ubuntu:**
###  Linux usbboot
Если вы используете карту microSD, вам не нужно беспокоиться об этом.
```
# sudo apt-get install libusb-1.0-0-dev  
# git clone --depth=1 https://github.com/raspberrypi/usbboot
# cd usbboot
# make
# sudo ./rpiboot
```
Если появляется содержимое, показанное на рисунке ниже, это означает, что инициализация EMMC прошла успешно.  
![Image title](assets/images/flash_os/flash_rpiboot.png){width="300"}

### Использование RPi Imager (на Linux, MacOS и Windows)

1. Скачайте и установите **последнюю версию** [RPi Imager](https://github.com/raspberrypi/rpi-imager/releases).

2. Запустите RPi Imager:  
![Image title](assets/images/flash_os/flash_rpi.png){width="300"}  

3. Нажмите **CHOOSE OS** и выберете **Use custom** кастомный образ внизу списка:  
![Image title](assets/images/flash_os/flash_choose_os.png){width="300"}

4. После нажатия на этот пункт выберите файл образа (`.img.xz`), затем нажмите **CHOOSE STORAGE** (выбрать хранилище):  
![Image title](assets/images/flash_os/flash_img.png){width="300"}

5. Вставьте карту памяти в устройство чтения карт. Выберите устройство чтения карт памяти из этого списка. **Будьте осторожны** и выберете правильную карту:   

    ![Image title](assets/images/flash_os/flash_storage.png){width="300"}

6. После выбора нужной карты, нажмите на кнопку **WRITE** (запись). Подтвердите операцию, когда вас спросят об этом:  
![Image title](assets/images/flash_os/flash_write.png){width="300"} 

7. Дождитесь завершения процесса. Налейте себе кофейку или сделайте зарядку :) 
!!! tip
    Процесс может зависнуть на 99% в течение длительного времени, это нормально, просто дождитесь его завершения
![Image title](assets/images/flash_os/flash_wait_process.png){width="300"}

8. Извлеките карту памяти после успешного завершения: 

![Image title](assets/images/flash_os/flash_write_successful.png){width="300"}

!!! tip
    Если во время перепрошивки или загрузки PiKVM возникает ошибка, повторите процесс.
