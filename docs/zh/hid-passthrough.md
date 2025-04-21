# **键盘鼠标环出**

BliKVM 从v1.5.8版本开始，支持将本地的键盘鼠标接到KVM的USB2.0或者USB3.0的口上，然后统一可以通过KVM对键盘鼠标的数据进行管理。
默认此功能是关闭的，如果需要此功能，通过编辑 `/mnt/exec/release/config/app.json`中的 `pass_through`字段开启，其中`enabled`设置为`true`会开启此功能，`mouse_sensitivity`为物理鼠标的灵敏度，如果感觉迟钝或者灵敏，可以通过对这个数字进行调整。
```
    "pass_through": {
      "enabled": false,
      "mouse_sensitivity": 0.3
    },
```
配置完后，可以通过下面命令重启服务生效：
```
    systemctl restart kvmd-web
```

!!! warn "由于透传的物理鼠标，只能在相对鼠标模式下工作，所有你只能讲鼠标模式设置为双鼠标模式，或者单相对鼠标模式"
    通过键盘鼠标环出功能，如果你将鼠标设置为单相对鼠标模式，目标设备就只会出现KVM虚拟的一个键盘和鼠标设备。