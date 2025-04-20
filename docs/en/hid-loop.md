# **Throughput for local keyboard and mouse**

Starting from version v1.5.8, BliKVM supports connecting local keyboards and mice to the KVM's USB 2.0 or USB 3.0 ports, allowing unified management of keyboard and mouse data through the KVM.
This feature is disabled by default. To enable it, edit the `pass_through` field in `/mnt/exec/release/config/app.json`, setting `enabled` to `true`. The `mouse_sensitivity` field adjusts the physical mouse sensitivity; you can modify this value if the mouse feels too sluggish or too sensitive.
```
    "pass_through": {
      "enabled": false,
      "mouse_sensitivity": 0.3
    },
```
After configuring, restart the service with the following command for the changes to take effect:
```
    systemctl restart kvmd-web
```

!!! warn "Due to the physical mouse passthrough only working in relative mouse mode, you can only set the mouse mode to dual mouse mode or single relative mouse mode."
    With the keyboard and mouse loopback feature, if you set the mouse to single relative mouse mode, the target device will only show one virtual keyboard and mouse device from the KVM.