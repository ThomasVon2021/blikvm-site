# **Mouse**

The mouse device has two modes: absolute mode and relative mode.

In absolute mode, the input device transmits the exact coordinates `(X,Y)` where the cursor should move. This is how touchscreens or drawing tablets work.

In relative mode, only the relative offset `(dX,dY)` from the current position is transmitted, and the input device itself does not know the current position. This is how a regular mouse works.

By default, BliKVM uses absolute positioning mode because it is the most convenient for users and software.
However, this is not always supported by BIOS/UEFI.
For such cases, support for relative mode is provided and can be enabled in the configuration.

When using relative mode, clicking once in the BliKVM stream window will cause the browser to exclusively capture your mouse.
Pressing the `Esc` key will release the mouse from the browser.

-----
## **Important Note**

- Relative mouse generates a large number of events, which may not be transmitted over the network or may be perceived very slowly by BIOS/UEFI drivers.
- Using dual mouse mode means that two mouse devices will appear on your controlled computer, while using single mouse mode means only one mouse device will appear on your controlled computer.

### **Dual Mode**

Using dual mouse mode, you can switch between absolute and relative mouse in the `System` menu without reloading.
From version v1.5.8-alpha onwards, dual mode is enabled by default. If you encounter issues where the keyboard works but the mouse does not, try switching to single mode. Note that switching between single and dual modes requires restarting the KVM.

1. Use the command `rw` to switch the file system to RW mode.

2. Edit the `mouseMode` field in `/mnt/exec/release/config/app.json`, where `dual` stands for dual mouse mode:
    ```
        "mouseMode": "dual"
    ```

3. Execute `reboot`. Then restart your PC.

### **Single Relative Mode**

1. Use the command `rw` to switch the file system to RW mode.

2. Edit the `mouseMode` field in `/mnt/exec/release/config/app.json`. There are two single mouse modes: `absolute` (single absolute mouse mode) and `relative` (single relative mouse mode):
    ```
        "mouseMode": "absolute"
    ```

3. Execute `reboot`. Then restart your PC.
