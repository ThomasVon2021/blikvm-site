## 策略
在版本 v1.5.0 之后, 为了避免 OLED/LCD 显示屏烧屏，显示屏的开启时间仅根据其配置进行控制。

## 配置
```
// 所有时间参数均以秒为单位，且必须为 5 的整数倍。
// 配置文件路径在/mnt/exec/release/config/app.json
"display":{
    "mode": "boot",              
    "onBootTime": 3600,     
    "cycleInterval": 300,
    "displayTime": 30,
}
```
mode共有4个值，具体内容如下：

## 所有 BliKVM 版本

|mode|描述|
|-|-|
|off|关闭OLED|
|always|始终开启，不考虑任何参数|
|boot|显示屏保持开启 `onBootTime` 秒，然后关闭。取决于 "onBootTime"|
|interval|每个 `cycleInterval` 周期内，显示屏开启 `displayTime` 秒，然后关闭。:rotating_light: 取决于 "cycleInterval" 和 "displayTime"|

## 仅 BliKVM v4 Allwinner
* 由于 v4 具有 sw1 按钮，如果设置模式为 1。
行为：
* 启动时：显示屏开启 `onBootTime` 秒，然后自动关闭。
* 按下按钮 (sw1)：按下 sw1 显示屏开启 `displayTime` 秒。如果显示屏已经开启，按下 sw1 将没有任何影响。
