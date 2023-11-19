# OLED display 

Due to the potential issues like screen burn-in during prolonged OLED usage, the display follows the following logic: upon initial startup, it defaults to continuous display for 300 minutes, followed by a 5-minute interval display. This approach significantly enhances the screen's overall lifespan.  

To customize this behavior, you can locate the following configuration in the "/usr/bin/blikvm/package.json" file. Modify the values of "restart_show_time" and "interval_display_time" in minutes to achieve different control effects.

```
"oled":{
    "oled_enable": 1,
    "restart_show_time": 300,
    "interval_display_time": 5
}
```



