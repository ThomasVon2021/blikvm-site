## Principle
After v1.5.0 version, to avoid OLED/LCD display burn-in the display's on-time is only turned on according to its configuration.

## Configuration 
```
// All time-parameters are in seconds, and are required to be integer multiples of 5.
"Display":{
    "isActive": true,
    "mode": 1,              
    "onBootTime": 3600,     
    "cycleInterval": 300,
    "displayTime": 30,
}
```
Use `isActive` to activate the display :rotating_light:  . While `"isActive": "false"`, the display will not function.

## All BliKVM versions

|mode||
|-|-|
|0|always on, doesn't care about any of the paramters|
|1|Display remains on for `onBootTime` seconds,  after which the display turns off. Depends on "onBootTime"|
|2|Every period of `cycleInterval`, the display turns on for `displayTime` seconds`, then turns off. :rotating_light: Depends on "cycleInterval"and "displayTime"|

## Only BliKVM v4 Allwinner
* Since v4 has the sw1 buttons, if set mode to 1.
Behavior:
* On Boot: the display turns on for `onBootTime` seconds, then automatically turns off.
* On Button Press (sw1): Pressing sw1 turns on the display for `displayTime` seconds. If the display is already on, pressing sw1 will have no impact at all.

