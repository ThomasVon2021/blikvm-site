## Principle
After v1.5.9 version, to avoid OLED/LCD display burn-in the display's on-time is only turned on according to its configuration.

## Configuration 
```
// All time-parameters are in seconds, and are required to be integer multiples of 5.
// This json file is on /mnt/exec/release/config/app.json
"Display":{
    "mode": "boot",              
    "onBootTime": 3600,     
    "cycleInterval": 300,
    "displayTime": 30,
}
```
The `mode` parameter has 4 possible values, detailed as follows:

## All BliKVM versions

|mode||
|-|-|
|off|display off|
|always|always on, doesn't care about any of the paramters|
|boot|Display remains on for `onBootTime` seconds,  after which the display turns off. Depends on "onBootTime"|
|interval|Every period of `cycleInterval`, the display turns on for `displayTime` seconds`, then turns off. :rotating_light: Depends on "cycleInterval"and "displayTime"|

## Only BliKVM v4 Allwinner
* Since v4 has the sw1 buttons, if set mode to 1.
Behavior:
* On Boot: the display turns on for `onBootTime` seconds, then automatically turns off.
* On Button Press (sw1): Pressing sw1 turns on the display for `displayTime` seconds. If the display is already on, pressing sw1 will have no impact at all.

