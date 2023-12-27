# **OLED display**

由于OLED长期运行，会出现烧屏等问题，故OLED有以下逻辑，首次启动时，oled_enable默认设置为1，即OLED屏幕会常亮。若oled_enable设置为0，则在设备启动300分钟,然后间隔5分钟显示一次，从而大大增加屏幕的生命周期。  
你可以在/usr/bin/blikvm/package.json配置文件中，找到下面配置，通过修改restart_show_time和interval_display_time时间，达到不同的控制效果，单位为分钟。
```
"oled":{
    "oled_enable": 1,
    "restart_show_time": 300,
    "interval_display_time": 5
}
```

