# 视频 键盘 鼠标

# **视频**

视频目前支持两种模式，mjepg和web-rtc(h264), 启动视频传输的脚本路径在`/usr/bin/blikvm/kvmd-video.sh`, 使用`/usr/bin/blikvm/ustreamer.bin`作为可执行程序，其中带有`--h264-sink=demo::ustreamer::h264`适用于Pi系列平台(v1,v2,v3)，带有`--format=MJPEG`的那一行适用于非Pi平台(v4)。 由于图像质量和网络带宽存在不同需求，你可以通过命令行的方式调整一些参数。如
```
#传输分辨率，你可以修改为其它分辨率，如1280x720，修改更低分辨率会降低传输带宽需求，同时降低画面质量；
--resolution=1920x1080
#传输帧率，你可以修改更低分辨率，可以有效降低传输带宽。
--desired-fps=30
```

??? info "再测试时，可以先使用如 `ps -aux | grep ustreamer` 命令将现有的图像传输进程kill掉，手动修改脚本后，重新终端运行`bash /usr/bin/blikvm/kvmd-video.sh`来重新启动图传进程，参数调整符合需求后，可以重新使用`systemctl restart kvmd-video.service`此命令后台运行图传进程"


## **键盘**
虚拟键盘支持组合键使用，具体方法如下，用鼠标点住对应虚拟按键，按下不放，拖到虚拟键盘外再松开，即可完成组合按键的操作。如使用ctrl+alt+del组合键,效果如下:
![](assets/images/hid/virtually.png){width="500"} 

!!! warning "目前mac电脑cmd+其它按键，同时按下，当松开cmd时，其它按键不会松开，此bug尚未修复。用户可通过点击虚拟键盘未被正确释放的按键先解决此问题"

