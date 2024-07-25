# OLED display 

Due to prolonged operation, issues such as screen burn-in may occur with the OLED. Therefore, the OLED has the following logic: upon initial startup, oled_enable is set to 1 by default, meaning the OLED screen will remain constantly on. If oled_enable is set to 0, the screen will display every 5 minutes after the device has been running for 300 minutes, significantly extending the screen's lifespan.

To customize this behavior, you can locate the following configuration in the "/usr/bin/blikvm/package.json" file. Modify the values of "restart_show_time" and "interval_display_time" in minutes to achieve different control effects.

```
"oled":{
    "oled_enable": 1,
    "restart_show_time": 300,
    "interval_display_time": 5
}
```


# BliKVM v4 Allwinner
To power ON/OFF the the display manually, please press and hold the `SW2` button on the front pannel.
