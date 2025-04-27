# BLIKVM CM4 руководство

!!! info "BLIKVM CM4 видео"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/2av-JFFkF6I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## **Требования к установке**
!!! note "Если у вас есть необходимый монтажный комплект, вам понадобятся также следующие вещи"
    * Raspberry CM4 с 1 Гб ОЗУ или больше.
    * MicroSD карта (не менее 16 Гб, рекомендуется класс 10).
    * Кабель USB-C в USB-A.
    * Кабель HDMI.
    * Прямой кабель Ethernet (для подключения платы ATX)..
    * Блок питания (5.1V 3A USB-C, рекомендованный для использования с Raspberry Pi).

!!! warning "Источник питания"
    Вы должны использовать именно кабель USB-C к USB-A. Использование кабеля USB-C в USB-C не сработает. Это несовместимость в аппаратном обеспечении, она будет исправлена в более поздней версии.

## **Базовая настройка**
**1.** [Прошейте карту памяти или eMMC](./flashing_os.md) 

**2. Соберите BLIKVM** в соответствии с инструкциями:

??? info "Видео-руководство: пошаговая сборка металлического корпуса"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/aehOawHklGE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
??? info "Видео от Geerling Engineering"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/3OPd7svT3bE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  
??? info "Видео от Ortimo: BLIKVM with Raspberry PI CM4 16GB EMMC setup"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/xypeC7Fne6Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
**3.** Подключите BLKVM к компьютеру в соответствии с приведенной ниже схемой:
![Image title](assets/images/blikcm-cm4-interface.png){width="400"}

* Вход HDMI и порт otg должны быть подключены к компьютеру. ATX тоже, но это необязательно, читайте ниже. Между BLKVM и компьютером не должно быть USB хаба, так как некоторые UEFI/BIOS не могут обнаружить их на этапе загрузки. BLKVM поддерживает разрешение 1080p60Hz или ниже относительно источника HDMI.
* Подключите Ethernet к сети и PWR IN к блоку питания BLIKVM.

## **Подключение ATX**
![Image title](assets/images/BLKVM-CM4/ATX-interface.png){width="400"}

Для управления питанием компьютера, необходимо подключить к компьютеру порт CNA-ATX. Пользователь может использовать кабель ATX, входящий в комплект поставки устройства, для подключения устройства к коммутатору ATX материнской платы управляемого компьютера. Длина кабеля ATX составляет 60 см, вы также можете использовать кабели Dupont типа мама-мама.

![Image title](assets/images/BLKVM-CM4/atx-cable-computer.png){width="400"}

## **Аппаратные характеристики**
![Image title](assets/images/BLKVM-CM4/blikvm-cm4-hardware-features.png)

* 1、HDMI IN порт с I2S
* 2、Интерфейс контроллера ATX (включение/выключение питания, управление перезагрузкой, светодиоды PWR и HDD ACT LEDs)
* 3、USB3.0 порты x 2
* 4、USB-C OTG
* 5、Часы Реального Времени (RTC)
* 6、Гигабитный Ethernet
* 7、LED индикация активности
* 8、Гнездо для карты microSD
* 9、LED индикатор питания
* 10、Разъем дисплея I2C
* 11、Перемычка nRPI_BOOT
* 12、Вход питания USB-C
* 13、Разъем кулера 5 В
* 14、Переключатель каналов передачи данных CSI-2
* 15、Разъемы модуля CM4

## ** Поддержка 1080p60hz входа HDMI **
Во-первых, в версии V2.2 есть переключатель каналов CSI. Этот переключатель предназначен для переключения 2 каналов csi или 4 каналов csi. В других версиях переключатель устарел. Более новый сохраняет заводское состояние, игнорируйте этот переключатель. Переключатель можно использовать только при выключенном питании устройства, в противном случае это может привести к необратимому повреждению! Четыре маленьких переключателя должны быть подняты или опущены одновременно.

![Image title](assets/images/BLKVM-CM4/kvm-cm4-switch.png){width="400"}
Функция кодирования видео в Raspberry Pi реализована с помощью чипа Toshiba TC358743 HDMI-to-CSI bridge, который поддерживает до 4 каналов передачи данных CSI-2. Интерфейс камеры Raspberry Pi 4B поддерживает только 2 полосы передачи данных CSI-2 (до 1080P 50Hz), Raspberry Pi CM4 может поддерживать 4 полосы передачи данных CSI-2 (до 1080p60Hz). В настоящее время PiKVM использует только два канала CSI-2.

1. Найти файл EDID:
```
rw
vim /etc/kvmd/tc358743-edid.hex
```
запишите следующий EDID 1080p 60 Гц в файл tc358743-edid.hex.
```
00FFFFFFFFFFFF0031D8888800888888
1C150103800000780AEE91A3544C9926
0F50543FCD0001000101010101010101
010101010101011D007251D01E206E28
5500C48E2100001E8C0AD08A20E02D10
103E9600138E2100001E000000FC0050
694B564D0A20202020202020000000FD
003B3D0F2E0F1E0A202020202020013C
02031E434F041303021211012021A23C
3D3E1F1066030C00300080E2007F8C0A
D08A20E02D10103E9600C48E21000018
8C0AD08A20E02D10103E9600138E2100
00189729A0D051842230509816009A01
11000018000000000000000000000000
00000000000000000000000000000000
0000000000000000000000000000001C
```
2. Добавить 4 полосы csi. Редактировать файл /boot/config.txt, изменить "dtoverlay=tc358743" на "dtoverlay=tc358743,4lane=1"
```
vim /boot/config.txt
ro
```
Теперь перезагрузите BLIKVM, можно тестировать 1080p 60 Гц вход.

![](https://github.com/blikvm/pikvm-CM4-Board/blob/main/images/wiki/60hz.jpg)  
