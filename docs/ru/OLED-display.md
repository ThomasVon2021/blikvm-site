# OLED дисплей 
!!! abstract "Следуйте приведенному ниже методу, чтобы включить OLED."
    Если вы используете образ PiKVM, войдите в PiKVM и выполните следующие команды:
    ```
    # rw
    # systemctl enable --now kvmd-oled // Включить OLED
    # ro
    ```
!!! info "Версия BLIKVM CM4 дисплея OLED"
    Продукт поставляется в стандартной комплектации с монохромным OLED-дисплеем с разрешением 128x64, на чипе SSD1306.  
    Пользователь подключает дисплей к устройству при помощи проводов дисплея.

    ![Image title](assets/images/oled/BLIKVM-CM4-oled.png){width="300"}

    Модуль подключается к CM4 через интерфейс I2C. Распиновка указана на таблице ниже. 
    Используется библиотека для монохромных OLED-дисплеев, основанная на [SSD1306 драйверах.](https://github.com/adafruit/Adafruit_SSD1306)

    | Дисплей (SSD1306) | CM4               |
    | ----------------- | ----------------- |
    | GND               | GND               |
    | VCC               | 3.3V              |
    | SCL               | GPIO3(SCL1,I2C)   |
    | SDA               | GPIO2(SDA1,I2C)   |
