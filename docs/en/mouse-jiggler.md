# **Mouse Jiggler**

A mouse jiggler is a function used to simulate computer mouse movement.
It can prevent the computer from entering sleep mode, standby mode, or activating the screensaver.
It is very useful when there are some time-consuming processes running on the target host (e.g., software installation), and the user needs to monitor it without manually moving the mouse to avoid the screensaver.

-----
## **Using the Jiggler**

In the latest BliKVM operating system, the jiggler can be directly enabled in the mouse configuration of the Web UI. If you do not see this switch, please update the software to the latest version.

-----
## **Jiggler Settings**

Usually, this is not necessary, but some parameters of the jiggler can be changed.
Edit the following parameters in `/mnt/exec/release/config/app.json`, where `jigglerTimeDiff` is the interval between two jiggles, in seconds:
```
    "mouseJiggler": false,
    "jigglerTimeDiff": 60,
```

-----
## Algorithm Description

When the jiggler is activated, BliKVM calculates the time elapsed since the last user input:
any operation of the keyboard or mouse. If there is no operation for the set time,
the jiggler will perform a mouse movement and wait for another set time in seconds until the next iteration.

The jiggler works on the BliKVM device side, even if the Web UI is closed.

An important feature of the jiggler is that it does not interfere with normal user work.
If the user is actively using the keyboard and mouse, the jiggler will not interfere
until it detects an inactivity time exceeding the set threshold.
