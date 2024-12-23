# 软件更新介绍

!!! info "如果您运行的是非常旧的版本，我们建议您先重新刷机，然后在靠近您的BliKVM设备时运行更新过程。"

## **介绍**

!!! note "BLIKVM项目目前可用版本托管在github仓库的release包里，更新软件功能需保持设备联网，更新软件目前提供两种方式"
    * 方式1，通过web界面点击更新按钮，程序自动进行更新,更新完需要重启。
    * 方式2，手动在KVM终端上运行脚本进行更新，更新完后需要重启。

!!! info "升级错误常见原因"
    * 设备未联网;
    * 网络访问github受限;

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
    - 其中v1 v2 v3硬件使用 release.tar.gz
    - v4硬件使用 release-h616-v4.tar.gz
    ssh进入设备终端，并使用`tar -zxvf release.tar.gz`解压release.tar.gz。
    ```
    sudo -i
    cd /your release path/
    python3 install_release.py --releasepath=./
    ```
    可以观察/usr/bin/blikvm/package.json前后的版本对比，若升级到了指定版本，则成功，重启生效。




