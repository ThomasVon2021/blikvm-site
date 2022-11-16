
## 自動拡張の設定
イメージの作成を始める前に

```
sudo vim /boot/cmdline.txt
##  rootwait の後に追加
quiet init=/usr/lib/raspberrypi-sys-mods/firstboot
## 例: console=serial0,115200 console=tty1 root=PARTUUID=b1214a26-02 rootfstype=ext4 fsck.repair=yes rootwait quiet init=/usr/lib/raspberrypi-sys-mods/firstboot

## resize2fs_once ファイルを追加
sudo vim /etc/init.d/resize2fs_once

## resize2fs_once ファイルを下記のように編集

#!/bin/sh
### BEGIN INIT INFO
# Provides:          resize2fs_once
# Required-Start:
# Required-Stop:
# Default-Start: 3
# Default-Stop:
# Short-Description: Resize the root filesystem to fill partition
# Description:
### END INIT INFO
. /lib/lsb/init-functions
case "$1" in
  start)
    log_daemon_msg "Starting resize2fs_once"
    ROOT_DEV=$(findmnt / -o source -n) &&
    resize2fs $ROOT_DEV &&
    update-rc.d resize2fs_once remove &&
    rm /etc/init.d/resize2fs_once &&
    log_end_msg $?
    ;;
  *)
    echo "Usage: $0 start" >&2
    exit 3
    ;;
esac

```