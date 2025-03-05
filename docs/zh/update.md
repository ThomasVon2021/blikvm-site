# 软件更新介绍

!!! info "如果您运行的是非常旧的版本，我们建议您先重新刷机，然后在靠近您的BliKVM设备时运行更新过程。"

## **介绍**

!!! note "BLIKVM项目目前可用版本托管在github仓库的release包里，更新软件功能需保持设备联网，更新软件目前提供两种方式"
    * 方式1，手动在KVM终端上运行脚本进行更新。
    * 方式2，手动下载软件包，然后在KVM终端上运行安装更新。

!!! info "升级错误常见原因"
    * 设备未联网;
    * 网络访问github受限;
    * 你的本地版本可能会与最新版本不兼容，若发生更新成功，但运行异常情况，需要重新烧录最新系统恢复；

!!! warning "我们强烈建议您在靠近要升级的BliKVM硬件时执行更新。原因是，如果出现任何问题，你可以进行干预。"
    * 如果您熟悉命令行操作，建议您手动更新可以实时查看命令行状态。
    * 若更新异常，web界面无法退出更新状态，可以终端ssh进入kvm后重启恢复。

## **手动运行脚本更新**
!!! info "ssh进入设备终端。若当前系统终端可以看到ro关键字，为只读系统，需使用`rw`让系统为可写权限。"
    ```
    sudo -i
    curl -L https://raw.githubusercontent.com/ThomasVon2021/blikvm/master/script/update.py -o /tmp/update.py && python3 /tmp/update.py
    ```
    观察终端输出，当看到升级升级成功消息提醒时，终端输入reboot，重启生效。

!!! warning "若您因网络原因，一直无法更新成功，可以采用在其它网络ok的PC上下载最新的release包，然后按照以下命令进行安装。"
    - 下载地址: https://github.com/ThomasVon2021/blikvm/releases
    - 其中v1 v2 v3硬件使用 blikvm-v1-v2-v3.deb
    - v4硬件使用 blikvm-v4.deb
    ssh进入设备终端，并使用`dpkg -i xxx.deb`
    可以观察/usr/bin/blikvm/package.json前后的版本对比，若升级到了指定版本，则成功，重启生效。




