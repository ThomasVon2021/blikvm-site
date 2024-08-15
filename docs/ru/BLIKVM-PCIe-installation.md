# Иллюстрированное руководство по сборке BLIKVM PCIe CM4

![PCIe_main](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/PCIe_main.jpg){width="500"}
## **1. Распакуйте и извлеките устройства**
!!! note "Перечень продукции"
    ![PCIe_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/PCIe_all.jpg){width="400"}

## **2. Установка основного устройства**
!!! note "Установите CM4 и 4 шестигранные проставки (в этой статье в качестве примера используется CM4 lite, используя образ на карте microSD, пользователю CM4 eMMC необходимо записать образ самостоятельно). Приклейте термопрокладку поверх CM4, снимите защитную пленку."
    ![Preparing_to_install_CM4](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Preparing_to_install_CM4.jpg){width="300"}
    ![install_cm4_and_4_spacers](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_cm4_and_4_spacers.jpg){width="300"}
    ![install_cm4_and_4_spacers_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_cm4_and_4_spacers_2.jpg){width="300"}
    ![Stick_a_heat_conductive_sheet](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Stick_a_heat_conductive_sheet.jpg){width="300"} 
    Установите металлический радиатор 
    ![Install_metal_heatsink](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_metal_heatsink.jpg){width="300"}

**Установка основного устройства завершена.**

## **3. Подключите USB и ATX**
!!! note "Материнская плата, используемая в этой статье --- Asus H520M-E, интерфейс материнских плат может отличаться, пожалуйста, обратитесь к руководству по эксплуатации своей материнской платы."
    ![connection_preparation](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connection_preparation.jpg){width="300"}
    ![connect_USB_and_ATX](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX.jpg){width="300"}
    ![connect_USB_and_ATX_motherboard](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX_motherboard-165941489982915.jpg){width="300"}
    ![pin_definition_atx](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/pin_definition_atx.jpg){width="300"}
    ![connect_USB_and_ATX_OK](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX_OK.jpg){width="300"}

## **4. Подсоедините OLED дисплей**
!!! note ""
    ![connect_OLED](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_OLED.jpg){width="400"}

## **5. Подсоедините HDMI кабель**
!!! note "Подключите выходной порт HDMI компьютера непосредственно к входному порту устройства при помощи HDMI кабеля. Сквозной эмулятор EDID HDMI необязателен! Подключайте эмулятор EDID HDMI к выходному порту HDMI компьютера, если ваш компьютер выдает неправильный формат HDMI. Это позволяет вам настроить фиксированный формат вывода HDMI на вашем компьютере."
    ![Connect_HDMI_cable_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_1.jpg){width="300"}
    ![Connect_HDMI_cable_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_2.jpg){width="300"}
    ![Connect_HDMI_cable_3](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_3.jpg){width="300"}

## **6. Подсоедините сетевой кабель**
!!! note "Стандарт гигабитного Ethernet порта: IEEE 802.3af входное напряжение PoE: 37-57В."
    ![Connect_the_network_cable](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_the_network_cable.jpg){width="400"}

!!! warning "При использовании источника питания PoE нет необходимости подключать порт PWR-IN."

## **7. Подключение PWR-IN**

![Connect_PWR-IN](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_PWR-IN.jpg){width="400"}

!!! warning "Если источник питания PoE не используется, подключите порт PWR-IN к стандартному USB-источнику питания 5В/3А."

## **8. Проверка**

!!! note "OLED-экран, показывающий IP-адрес устройства и другую информацию."
    ![find_IP](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/find_IP.jpg){width="300"}
    ![test_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/test_all.jpg){width="300"}
    Подключитесь к IP-адресу в браузере. После прохождения теста установите устройство в корпус компьютера.

## **9. Установите устройство в корпус компьютера**

!!! note "Отключите питание и отсоедините провода, установите устройство на материнскую плату и снова подключите кабели после завершения установки."
    ![blikvm_in_case](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/blikvm_in_case.jpg){width="300"}
    ![OLED_display_out](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/OLED_display_out.jpg){width="300"}
    ![finish_installation_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/finish_installation_1.jpg){width="300"}
    ![finish_installation_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/finish_installation_2.jpg){width="300"}

Enjoy!

## **Дополнение 1. Установка низкопрофильного кронштейна PCIe I/O**
!!! note
    ![remove_standard_bracket](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/remove_standard_bracket.jpg){width="300"}
    ![replace_low_bracket_1_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_1_1.jpg){width="300"}
    ![replace_low_bracket_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_2.jpg){width="300"}
    ![replace_low_bracket_3](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_3.jpg){width="300"}
    ![replace_low_bracket_4](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_4.jpg){width="300"}

## **Дополнение 2. Установка кулера**

!!! note "Обычно достаточно металлического радиатора и кулер бывает избыточен."
    ![install_fan_prepare](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_prepare.jpg){width="300"}
    ![install_fan_unscrew](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_unscrew.jpg){width="300"}
    ![place_4_nylon_spacers](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/place_4_nylon_spacers.jpg){width="300"}
    ![install_fan_ok](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_ok.jpg){width="300"}
    ![fan_power_polarity](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/fan_power_polarity.jpg){width="300"}
    ![install_fan_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_all.jpg){width="300"}

!!! info "кулер контролируется через CM4 по пину GPIO12."

## **Дополнение 3. Установка антенны Wi-Fi**
!!! note
    ![Install_wifi_antenna_prepare](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_wifi_antenna_prepare.jpg){width="300"}
    ![Install_wifi_antenna](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_wifi_antenna.jpg){width="300"}
