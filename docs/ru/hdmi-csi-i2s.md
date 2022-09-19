# Руководство по подключению HDMI к мосту CSI и I2C
> Преобразование сигнала HDMI в сигнал CSI и аудиосигнал I2S.

## **Введение**
Этот модуль принимает входящий сигнал HDMI и преобразует его в отдельный сигнал CSI и аудиосигнал I2S. Вход HDMI поддерживает разрешение до 1080P при 60 Гц. Он хорошо работает на Raspberry Pi, существует три версии этого модуля (C779, C780, C790). C790 --- является последней версией. C790 имеет пониженную обратную мощность HDMI, а также имеет два канала csi и четыре канала csi одновременно.
![](assets/images/hdmi-csi-i2s/c790.png)

## **Особенности**
### **C790**
!!! note "аппаратные параметры оборудования"
    * HDMI вход: поддерживает разрешение до 1080P при 60 Гц на Raspberry Pi
    * HDMI-CSI-2 мостовой чип: Toshiba TC358743XBG
    * 4 CSI-2 канала и тактовый генератор
    * Интерфейс CSI-2 с 15-контактным гнездом FPC с шагом 1.0 мм расположен на передней панели модуля C790.
    * Интерфейс CSI-2 с 22-контактным гнездом FPC с шагом 0.5 мм расположен на задней панели модуля C790.
    * Размеры: 30 x 45 мм
    * Установка: 4 x M2.5
    * Блок питания: 3.3 В
    * Вес: 10 г

!!! note "интерфейс"
    ![](assets/images/hdmi-csi-i2s/c790-interface.png){width="400"}  
    C790 имеет два выходных интерфейса csi. Спереди C790 интерфейс CSI-2 представляет собой 15-контактное гнездо FPC с шагом 1.0 мм. Сзади C790 интерфейс CSI-2 представляет собой 22-контактное гнездо FPC с шагом 0.5 мм.
    ![](assets/images/hdmi-csi-i2s/c790-i2s-connect.png){width="400"}  

!!! note "размеры"
    ![](assets/images/hdmi-csi-i2s/c790-size.png){width="400"}  

### **C780**
??? info "Параметры C780A"
    * HDMI вход: поддержка до 1080P на 50 Гц на Raspberry Pi (ограничено количеством каналов CSI-2)
    * HDMI-CSI-2 мостовой чип: Toshiba TC358743XBG
    * 2 CSI-2 канала и тактовый генератор
    * Интерфейс CSI-2: 15-контактное гнездо FPC с шагом 1.0 мм
    * Размеры: 30 x 65 мм (размер цельной печатной платы); 30 x 45 мм (размер разъединённой печатной платы)
    * Установка: 6 x M2.5
    * Блок питания: 3.3 В
    * Вес: 10 г
??? info "Параметры C780B"
    * HDMI вход: поддержка до 1080P на 60 Гц на Raspberry Pi
    * HDMI-CSI-2 мостовой чип: Toshiba TC358743XBG
    * 4 CSI-2 канала и тактовый генератор
    * CSI-2 интерфейс: 22-контактное гнездо FPC с шагом 0.5 мм
    * Размеры: 30 x 65 мм (размер цельной печатной платы); 30 x 45 мм (размер разъединённой печатной платы)
    * Установка: 6 x M2.5
    * Блок питания: 3.3 В
    * Вес: 10 г
??? info "интерфейс"
    ![](assets/images/hdmi-csi-i2s/2-4.png){width="400"}  
    Схема подключения аудиосистемы показана на рисунке.  
    ![](assets/images/hdmi-csi-i2s/2-8.png){width="400"}
??? info "размеры"
    Размеры C780 показаны на рисунке. Имеется 6 монтажных отверстий диаметром 2.75 мм, которые подходят под винты М2.5.
    ![](assets/images/hdmi-csi-i2s/2-1.png){width="400"}  
    Как показано на рисунке, пользователь может непосредственно закрепить модуль на Raspberry Pi Zero. C780 спроектирован так, чтобы его можно было разъединить, расстояние между отверстиями перед разрывом идеально подходит для большинства серий Raspberry Pi.
    ![](assets/images/hdmi-csi-i2s/2-2.png){width="400"}

### **C779**
??? info "аппаратные параметры  оборудования"
    * HDMI вход: поддержка до 1080P на 50 Гц на Raspberry Pi (ограничено количеством каналов CSI-2)
    * HDMI-CSI-2 мостовой чип: Toshiba TC358743XBG
    * 2 CSI-2 канала и тактовый генератор
    * Интерфейс CSI-2: 15-контактное гнездо FPC с шагом 1.0 мм
    * Размеры: 35 x 50 мм 
    * Установка: 4 x M2.5
    * Блок питания: 3.3 В
    * Вес: 10 г

??? info "размеры"
    Размеры C779 показаны на рисунке. Имеются 4 монтажных отверстия диаметром 2.75 мм, которые подходят под винты М2.5. 
    ![](assets/images/hdmi-csi-i2s/c779-size.png){width="400"}  

## **Демонстрация программного обеспечения**
Руководство пользователя C790/C780/C779 зависит от используемой вами официальной версии Raspberry Pi OS. Разные версии имеют разные методы использования. Если у вас есть вопросы, то присоединяйтесь к нашему [BLIKVM дискорд сообществу](https://discord.com/invite/9Y374gUF6C)!

Чтобы использовать драйверы ядра, пожалуйста, обновите свою систему. Есть несколько моментов, которые изменились с ядром 5.4, поэтому эти инструкции предназначены для версии 5.4 или более поздней версии. Если команда “uname -a” сообщает о другом, тогда сначала исправьте это, перед тем как продолжить.  
``` 
pi@raspberrypi:~ $ uname -a
Linux raspberrypi 5.10.63-v7l+ #1459 SMP Wed Oct 6 16:41:57 BST 2021 armv7l GNU/Linux
```
!!! note "1. Выполните обновление системы Raspberry Pi (может занять много времени, в зависимости от разных стран)"
    ``` 
    sudo apt-get update
    sudo apt-get upgrade
    ``` 
!!! note "2. Включите модуль камеры (камера включена по умолчанию в Raspberry Pi Bullseys OS)"
    ```
    sudo raspi-config
    sudo reboot
    ```
    Перейдите в раздел ‘Interfacing Options’ и нажмите Enter. Теперь выберете опцию ‘Camera’, нажмите клавишу Enter чтобы включить её. Выберете “Finish” и перезагрузите Raspberry Pi. **перезагрузка является обязательной!!**
!!! note "3. Отредактируйте /boot/config.txt (для это потребуются права суперпользователя sudo)"
    ```
    sudo nano /boot/config.txt
    ```
    Добавьте строку:
    ```
    dtoverlay=tc358743
    ```
    Добавьте следующую строку, если ваш экран поддерживает аудио, например C780 или C790.
    ```
    dtoverlay=tc358743-audio
    ```
    добавьте следующую строку только в том случае, если у вас имеется устройство, такое как C780 или C790, которое поддерживает 22-контактное гнездо со всеми 4 подключенными полосами, и если используется модуль с CAM1 коннектором, в котором также подключены все четыре полосы:
    ```
    dtoverlay=tc358743,4lane=1
    ```
!!! note "4. Проверьте объем памяти, назначенный куче CMA, с помощью команды “dmesg | grep cma”. Первая строка должна быть в соответствии с"
    ```
    pi@raspberrypi:~ $ dmesg | grep cma
    [0.000000] cma: Reserved 256 MiB at 0x000000001ec00000
    ```
    Если команда сообщает об объеме меньшем чем 96MB для CMA, тогда отредактируйте /boot/cmdline.txt и добавьте в начало строки. 
    НЕ добавляйте никаких возвратов каретки.
    ```
    cma=96M
    ```
!!! note "5. Перезагрузитесь. Если все прошло хорошо, то отобразится устройство /dev/video0, а команда “v4l2-ctl –list-devices” покажет, что оно предоставляется Unicam. После подключения всех кабелей, включите Raspberry Pi, при нормальной работе, индикатор C790 горит зелёным, после открытия терминала в Raspberry Pi, введите следующие команды:"
    ```
    pi@raspberrypi:~ $ ls /dev/video0
    /dev/video0
    pi@raspberrypi:~ $ v4l2-ctl --list-devices
    bcm2835-codec-decode (platform:bcm2835-codec):
        /dev/video10
        /dev/video11
        /dev/video12
        /dev/video18
        /dev/media1
    bcm2835-isp (platform:bcm2835-isp):
        /dev/video13
        /dev/video14
        /dev/video15
        /dev/video16
        /dev/media0
    unicam (platform:fe801000.csi):
        /dev/video0
        /dev/video1
        /dev/media2
    ```
!!! note "6. Этот драйвер передает все управление в руки пользователя или пользовательского приложения. По умолчанию в чип не загружается EDID, позволяющий ему сообщать источнику HDMI какие разрешения поддерживаются. Если вы создадите файл edid.txt, тогда вы можете отправить это на устройство для использования. Блок к файлу edid.txt:"
    ```
    00ffffffffffff005262888800888888
    1c150103800000780aEE91A3544C9926
    0F505400000001010101010101010101
    010101010101011d007251d01e206e28
    5500c48e2100001e8c0ad08a20e02d10
    103e9600138e2100001e000000fc0054
    6f73686962612d4832430a20000000FD
    003b3d0f2e0f1e0a2020202020200100
    020321434e041303021211012021a23c
    3d3e1f2309070766030c00300080E300
    7F8c0ad08a20e02d10103e9600c48e21
    0000188c0ad08a20e02d10103e960013
    8e210000188c0aa01451f01600267c43
    00138e21000098000000000000000000
    00000000000000000000000000000000
    00000000000000000000000000000000
    ```
    ```
    cd ~
    sudo nano edid.txt
    # скопируйте блок выше в файл edid.txt, сохраните и выйдите;
    pi@raspberrypi:~ $ v4l2-ctl --set-edid=file=edid.txt --fix-edid-checksums
    
    CTA-861 Header
      IT Formats Underscanned: yes
      Audio:                   yes
      YCbCr 4:4:4:             no
      YCbCr 4:2:2:             no
    
    HDMI Vendor-Specific Data Block
      Physical Address:        3.0.0.0
      YCbCr 4:4:4 Deep Color:  no
      30-bit:                  no
      36-bit:                  no
      48-bit:                  no
    
    CTA-861 Video Capability Descriptor
      RGB Quantization Range:  yes
      YCC Quantization Range:  no
      PT:                      Supports both over- and underscan
      IT:                      Supports both over- and underscan
      CE:                      Supports both over- and underscan
    ```
!!! note "7. Драйвер НЕ переключается автоматически на обнаруженное разрешение. Используйте команду:"
    ```
    pi@raspberrypi:~ $ v4l2-ctl --query-dv-timings
	Active width: 1280
	Active height: 720
	Total width: 1650
	Total height: 750
	Frame format: progressive
	Polarities: -vsync -hsync
	Pixelclock: 74250000 Hz (60.00 frames per second)
	Horizontal frontporch: 0
	Horizontal sync: 370
	Horizontal backporch: 0
	Vertical frontporch: 0
	Vertical sync: 30
	Vertical backporch: 0
	Standards: 
	Flags: 
    ```
    Вы ДОЛЖНЫ установить тайминги через “v4l2-ctl –set-dv-bt-timings”. Вы можете передать индекс в обнаруженный режим или использовать:
    ```
    v4l2-ctl --set-dv-bt-timings query
    ```
    чтобы выбрать обнаруженные в данный момент тайминги.
    ```
    v4l2-ctl -V
    ```
    теперь должно быть отражено обнаруженное разрешение.

!!! note "8. Чип поддерживает два формата --- BGR3 (по умолчанию) и UYVY. BGR3 --- 24bpp, а UYVY --- YUV4:2:2 16bpp."
    По обычным 2 полосам CSI-2 скорость передачи данных такова, что BGR3 может работать максимум с разрешением 1080p30, в то время как UYVY будет работать до 1080p50. Используйте следующую команду, чтобы выбрать UYVY, однако ваше приложение может переопределить это.
    ```
    v4l2-ctl -v pixelformat=UYVY
    ```
!!! note "9. Убедитесь, что аудиодрайверы / карта доступны для ALSA."
    ```
    pi@raspberrypi:~ $ arecord -l
    **** List of CAPTURE Hardware Devices ****
    card 1: tc358743 [tc358743], device 0: bcm2835-i2s-dir-hifi dir-hifi-0 [bcm2835-i2s-dir-hifi dir-hifi-0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    ```
    Замечание: card 1 означает, что номер карты для TC358743XBG равен “1”, но он может отличаться.

!!! note "10. Установите GStreamer."
    ```
    sudo apt install gstreamer1.0-tools
    ```
    Проверьте версию gstreamer:
    ```
    pi@raspberrypi:~ $ gst-launch-1.0 --version
    gst-launch-1.0 version 1.18.4
    GStreamer 1.18.4
    http://packages.qa.debian.org/gstreamer1.0
    ```
    Замечание:
    Разные версии имеют разные параметры командной строки, что очень раздражает.

!!! note "11. Используйте gstreamer для записи видео и аудио"
    ```
    #GStreamer v1.14 command
    gst-launch-1.0 v4l2src io-mode=5 ! video/x-raw, format=UYVY, framerate=25/1 ! v4l2h264enc output-io-mode=4 ! video/x-h264,profile=high ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    ```
    foo.mkv --- выходной файл.
    Если ваш gstreamer имеет версию 1.8 или выше, вы можете попробовать следующую тестовую команду. Также, alsasrc device=hw:1 представляет звуковую карту TC358743, вы можете использовать “arecord -l” для запроса.
    ```
    # Команда для записи видео со звуком. (GStreamer 1.18.4)
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=30/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    # Образец команды для записи видео без звука. (C779 не поддерживает звук)
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=30/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv
    Press CTRL+C to end recording.
    ```
    PS: рекомендуется изменить указанный выше параметр частоты кадров на фактическую частоту кадров вашего сигнала HDMI, где фактическое значение частоты кадров взято из результата команды ’v4l2-ctl –query-dv-timings'.
    
    ![Image title](assets/images/hdmi-csi-i2s/v4l2-rate.png){width="400"}
    
    Для устройства HDMI выше, частота кадров равна 60, поэтому мы изменяем параметр частоты кадров на 60, в последующей команде. Записать только видео:
    ```
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=60/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv
    ```
    Запись видео со звуком: (если ваш экран поддерживает звук)
    ```
    gst-launch-1.0 -vvv v4l2src ! "video/x-raw,framerate=60/1,format=UYVY" ! v4l2h264enc extra-controls="controls,h264_profile=4,h264_level=13,video_bitrate=256000;" ! "video/x-h264,profile=high, level=(string)4.2" ! h264parse ! queue ! matroskamux name=mux ! filesink location=foo.mkv alsasrc device=hw:1 ! audio/x-raw,rate=48000,channels=2 ! audioconvert ! avenc_aac bitrate=48000 ! aacparse ! queue ! mux.
    ```
    Замечание: alsasrc device=hw:1 --- “1” означает номер аудио карты. Вы должны поменять это число на ваше.
    (Запрос номера карты осуществляется через команду ‘arecord –l’, см. пункт 9)

## **Комплектация**
??? info "C790"
    ![](assets/images/hdmi-csi-i2s/c790-packing-list.png){width="400"}

## **Видео с тестированием**
[Тестирование C780A](https://www.youtube.com/watch?v=ecqyINoiHNQ)

[Тестирование C780B](https://www.youtube.com/watch?v=nc-hwPT2Uak&t=15s)

## **Ссылка для покупки**
Купить：<a href="https://www.aliexpress.com/item/1005002861310912.html?pdp_ext_f=%7B%22sku_id%22:%2212000022635165947%22,%22ship_from%22:%22CN%22%7D&gps-id=pcStoreJustForYou&scm=1007.23125.137358.0&scm_id=1007.23125.137358.0&scm-url=1007.23125.137358.0&pvid=8e29d7e9-f257-4f20-a0b2-c2bff6a048d6&spm=a2g0o.store_pc_home.smartJustForYou_6000897758043.1" target="_blank">C790 и C780</a>

Купить：<a href="https://www.aliexpress.com/item/1005003033156483.html?spm=a2g0o.productlist.0.0.36f93cc2DFaouV&algo_pvid=2bfab2d1-a9c7-4c29-9434-2f451401d0e1&algo_exp_id=2bfab2d1-a9c7-4c29-9434-2f451401d0e1-9&pdp_ext_f=%7B%22sku_id%22%3A%2212000023351081819%22%7D" target="_blank">C779</a>
