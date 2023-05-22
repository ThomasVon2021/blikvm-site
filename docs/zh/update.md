# 软件更新介绍
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
!!! info "ssh进入设备终端"
    ```
    rw
    sudo -i
    cd /opt/bin/blikvm/
    git pull --rebase
    python3 /opt/bin/blikvm/script/update.py
    ro
    ```
    观察终端输出，当看到升级升级成功消息提醒时，终端输入reboot，重启生效。
    
## **Web界面更新**

!!! info "点击更多选项按钮后，找到**检查更新**按钮并点击,若发现可用版本，会出现下图中的弹框，点击**OK**,即进入升级，升级过程中web界面暂时不可操作。通过手动刷新页面，查看目前更新状态。当出现更新成功的消息提醒时，即表示更新已成功，点击重启按钮，新版本软件就会生效。"
    ![IMG_8366](assets/images/update/update_button.png){width="300"}
    ![IMG_8366](assets/images/update/update_info.png){width="300"}
    ![IMG_8366](assets/images/update/upgrading.png){width="300"}
    ![IMG_8366](assets/images/update/update_reboot.png){width="300"}




