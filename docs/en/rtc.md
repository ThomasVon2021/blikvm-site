# **RTC Clock**

The purpose of an RTC (Real-Time Clock) is to provide real-time information about the current date and time for a device or system. It is an independent clock chip or module that has its own power source, allowing it to maintain accurate time even when the device is powered off or experiences a power outage. Due to shipping restrictions on international deliveries, the RTC hardware is shipped without a battery, and users need to purchase a CR1220 button cell battery themselves. The specific RTC clock model used in different versions of BliKVM may vary, and the usage methods may differ slightly.

## **BliKVM V2 PCIe and BliKVM V3 Hat - pcf8563**

!!! info "1. Check if the pcf8563 RTC clock hardware is properly recognized on the i2c bus. The pcf8563 RTC clock has an i2c address of 0x51. Execute the following command as root to verify if the rtc clock is correctly detected on the i2c bus:"
    ```
    root@mangopimcore:~# i2cdetect -y 1
        0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
    00:                         -- -- -- -- -- -- -- --
    10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    50: -- 51 -- -- -- -- -- -- -- -- -- -- -- -- -- --
    60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    70: -- -- -- -- -- -- -- --
    ```
!!! info "2. Register a new i2c device with the Linux system's i2c subsystem. The device is a pcf8563 with an i2c address of 0x51. Use the command `ls /dev | grep rtc` to verify if the rtc1 device appears, indicating a successful registration."
    ```
    echo pcf8563 0x51 > /sys/class/i2c-adapter/i2c-1/new_device
    ```

!!! info "3. Set the current system time to the RTC clock time."
    ```
    hwclock -f /dev/rtc0 -w
    ```
!!! info "4. Read the time from the RTC clock. If the time can be read, it indicates that the RTC module is functioning correctly."
    ```
    root@mangopimcore:~# hwclock -f /dev/rtc0 -r
    2023-05-28 05:04:08.679152-02:30
    ```

## **BliKVM V4 - pcf8563**

!!! info "1. Check if the pcf8563 RTC clock hardware is properly recognized on the i2c bus. The pcf8563 RTC clock has an i2c address of 0x51. Execute the following command as root to verify if the rtc clock is correctly detected on the i2c bus:"
    ```
    root@mangopimcore:~# i2cdetect -y 0
        0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
    00:                         -- -- -- -- -- -- -- --
    10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    50: -- 51 -- -- -- -- -- -- -- -- -- -- -- -- -- --
    60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    70: -- -- -- -- -- -- -- --
    ```
!!! info "2. Register a new i2c device with the Linux system's i2c subsystem. The device is a pcf8563 with an i2c address of 0x51. Use the command `ls /dev | grep rtc` to verify if the rtc1 device appears, indicating a successful registration."
    ```
    echo pcf8563 0x51 > /sys/class/i2c-adapter/i2c-0/new_device
    ```

!!! info "3. Set the current system time to the RTC clock time."
    ```
    hwclock -f /dev/rtc1 -w
    ```
!!! info "4. Read the time from the RTC clock. If the time can be read, it indicates that the RTC module is functioning correctly."
    ```
    root@mangopimcore:~# hwclock -f /dev/rtc1 -r
    2023-05-28 05:04:08.679152-02:30
    ```
