# Руководство для версии BLIKVM HAT
## **Введение**

!!! info "Видео-демонстрация версии BLIKVM hat"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/SdpmMojDbGA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
Raspberry Pi IPKVM HAT является дополнительной платой для Raspberry Pi 4, созданной специально для KVM по IP. BLIKVM-RPI4 --- это Raspberry Pi 4 PoE KVM HAT. Главными особенностями этого устройства являются: захват видео, адаптер для ATX, PoE, OLED и RTC. Продукт имеет индивидуальный металлический корпус для отвода тепла и обеспечения защиты HAT. Устройство может быть легко установлено на стандартную стойку 1U. В настоящее время продукт полностью совместим с образом blikvm и pikvm.

 ![Image title](assets/images/BLIKVM-HAT/case.png){width="300"}
## **Требования к установке**
!!! note "Если у вас уже есть необходимый монтажный комплект, то вам понадобятся также следующие вещи"
    * Raspberry Pi 4B с 1 Гб ОЗУ или больше.
    * HDMI кабель.
    * Прямой кабель Ethernet (для подключения платы ATX).
    * Блок питания и кабель (5.1V 3A USB-C, рекомендованный для использования с Raspberry Pi).

## **Базовая настройка**
**1.** [Прошейте карту памяти или eMMC](./flashing_os.md) 

**2. Соберите BLIKVM** в соответствии с видео инструкцией или [иллюстрированными инструкциями](./BLIHAT-Installation.md):

??? info "Видео-руководство: пошаговая сборка металлического корпуса"
    <iframe width="560" height="315" src="https://www.youtube.com/embed/FaZBQUA7rAM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**3.** Установите плату адаптера ATX

!!! info "Плата оснащена стандартным кронштейном ввода-вывода PCIe и низкопрофильным кронштейном ввода-вывода PCIe. Выберите нужный в соответствии с вашей конфигурацией"
    ![IMG_8366](assets/images/BLIKVM-HAT/hat-install/IMG_8366.JPG){width="300"}
    ![IMG_8367](assets/images/BLIKVM-HAT/hat-install/IMG_8367.JPG){width="300"}

!!! info "Используйте соединительные кабели Dupont для подключения платы адаптера ATX к материнской плате и панели шасси. На плате имеются чёткие обозначения контактов для удобства подключения."
    ![IMG_8368](assets/images/BLIKVM-HAT/hat-install/IMG_8368.JPG){width="300"}
    ![IMG_8369](assets/images/BLIKVM-HAT/hat-install/IMG_8369.JPG){width="300"}

!!! info "Установите плату адаптера ATX в корпус"
    ![IMG_8370](assets/images/BLIKVM-HAT/hat-install/IMG_8370.JPG){width="300"}

!!! info "Используйте сетевой кабель RJ45 для подключения платы к интерфейсу CN-ATX на HAT"
    ![004d8da8059a57b87d2d40ce70174e7](assets/images/BLIKVM-HAT/hat-install/004d8da8059a57b87d2d40ce70174e7.png){width="300"}

**4.** подключите кабель HDMI

!!! info "Подключите выходной порт HDMI компьютера непосредственно к входному порту HDMI на HAT. Сквозной эмулятор EDID HDMI необязателен! Подключайте эмулятор EDID HDMI к выходному порту HDMI компьютера, если ваш компьютер выдает неправильный формат HDMI. Это позволяет вам настроить фиксированный формат вывода HDMI на вашем компьютере."
    ![30c484ad28e149b703ccc74c09e52db](assets/images/BLIKVM-HAT/hat-install/30c484ad28e149b703ccc74c09e52db.png){width="300"}
    ![IMG_8373](assets/images/BLIKVM-HAT/hat-install/IMG_8373.JPG){width="300"}

**5.** Установите кабель USB
!!! info "Подключите порт RPI 4 к Raspberry Pi 4"
    ![IMG_8374](assets/images/BLIKVM-HAT/hat-install/IMG_8374.JPG){width="300"}
    ![IMG_8375](assets/images/BLIKVM-HAT/hat-install/IMG_8375.JPG){width="300"}

!!! info "Подключите USB-порт к управляемому компьютеру"
    ![IMG_8376](assets/images/BLIKVM-HAT/hat-install/IMG_8376.JPG){width="300"}

!!! warning "При использовании источника питания PoE нет необходимости подключать порт PWR. Если источник питания PoE не используется, подключите порт PWR к стандартному USB-источнику питания 5В/3А."

**6.** Проверка
!!! info "Питание от PoE, HAT подключается к маршрутизатору через сетевой кабель"
    ![IMG_8377](assets/images/BLIKVM-HAT/hat-install/IMG_8377.JPG){width="300"}

!!! info "На экране отображается текущее состояние устройства, включая IP-адрес устройства"
    ![IMG_8379](assets/images/BLIKVM-HAT/hat-install/IMG_8379.JPG){width="300"}

!!! info "Получите доступ к IP-адресу HAT через браузер. Enjoy!"
    ![image-20220621174207504](assets/images/BLIKVM-HAT/hat-install/image-20220621174207504.png){width="300"}

## **Спецификация**
![Image title](assets/images/BLIKVM-HAT/specification.png){width="600"}

??? note "**HDMI вход**"
    Мостовой чип Toshiba TC358743 поддерживает как видео, так и аудио (I2S), максимальное входное разрешение составляет 1080p при 50 кадрах в секунду. Исправлена проблема с обратным питанием HDMI.

??? note "**CN-ATX**"
    Интерфейс CN-ATX подключается к плате адаптера ATX (аксессуар для HAT) через сетевой кабель, который может включать, выключать и перезагружать управляемый компьютер.

??? note "**Дисплей**"
    Белый OLED-дисплей с разрешением 128x32, на чипе --- SSD1306. Этот дисплей может отображать температуру, IP-адрес и другую информацию о Raspberry Pi.

??? note "**PoE**"
    - **Стандарт:** IEEE 802.3af PoE
    - **Входное напряжение:** 37-57 В DC
    - **Выходная мощность:** 5 В DC/2.4 А
    - Подключите крышку перемычки PoE, чтобы включить питание PoE

??? note "**Кулер**"
    IP KVM HAT оснащен небольшим кулером, который управляется Raspberry Pi через GPIO12. 

??? note "**Часы Реального Времени (RTC)**"
    Raspberry Pi управляет тактовым чипом PCF8563 через I2C интерфейс. Батарея-монетка установлена под модулем HDMI IN.

## **Аксессуары**

### **Плата адаптера ATX**

![Image title](assets/images/BLIKVM-HAT/ATX-A-B.png){width="300"}

Эта плата подключается к порту коммутатора на материнской плате управляемого компьютера с помощью кабелей DuPont. Плата имеет два варианта кронштейнов: стандартный PCIe I/O и низкопрофильный PCIe I/O.

### **USB/PWR сплиттер**
![Image title](assets/images/BLIKVM-HAT/usb-spiltter.png){width="300"}

- Подключение порта RPI 4 к вашей Raspberry Pi 4.
- Подключение USB-порта к управляемому компьютеру.
- При использовании источника питания PoE нет необходимости подключать порт PWR. Если источник питания PoE не используется, подключите порт PWR к стандартному USB-источнику питания 5В/3А.

### **HDMI EDID эмулятор**

![Image title](assets/images/BLIKVM-HAT/edid-emulator.png){width="300"}

Данный аксессуар необходимо использовать, если управляемый компьютер неправильно выводит изображение через HDMI. Подключите порт источника к управляемому компьютеру, подключите порт приемника к HAT. Затем вы можете установить правильный выход HDMI на управляемом компьютере.

### **Металлический корпус**

![Image title](assets/images/BLIKVM-HAT/metal-case.png){width="300"}
Металлический корпус защищает HAT и улучшает отвод тепла. На корпусе имеется маркировка портов.

Корпус может быть легко установлен на стандартную стойку 1U.

## **Список**

### **Перечень необходимой продукции**
![Image title](assets/images/BLIKVM-HAT/product-list.png){width="300"}

| Raspberry Pi IPKVM HAT                 | 1    |
| -------------------------------------- | ---- |
| Плата адаптера ATX                     | 1    |
| USB/PWR сплиттер                       | 1    |
| HDMI EDID эмулятор                     | 1    |
| Металлический корпус                   | 1    |
| TF-карта памяти на 32 Гб               | 1    |
| Кабель USB Type-C 30 см                | 1    |
| Dupont кабель 8 пин папа-папа 40 см    | 1    |
| Dupont кабель 8 пин папа-мама 40 см    | 1    |
| Крестообразная отвертка                | 1    |
| Втулка гаечного ключа                  | 1    |

### **Перечень элементов, подготавливаемых пользователем**

| Raspberry Pi 4                                                | 1    |
| ------------------------------------------------------------- | ---- |
| RJ45 сетевой кабель                                           | 2    |
| Кабель USB Type-A в USB Type-C                                | 2    |
| Кабель HDMI                                                   | 1    |
| Оборудование для подключения к сети PoE или USB-адаптер 5В/3А | 1    |
| Батарейка-монетка CR1220                                      | 1    |
