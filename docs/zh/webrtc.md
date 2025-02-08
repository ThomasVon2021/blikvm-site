它使用高效的 H.264 编码来节省流量。视频通过 WebRTC 协议进行流传输，你可能在使用 Discord 或 Google Chat 进行视频通话时遇到过该协议。

它适用于 BliKVM v1、v2、v3 以及所有基于 HDMI-CSI 桥接的 DIY 设备。

可以在 Web UI 的系统菜单中切换视频模式。如果你没有看到切换选项，可能是你的浏览器不支持 H.264 视频。

## **工作原理**
MJPEG 视频通过类似于获取 Web UI 的 HTTP 连接进行视频流传输。这意味着对于远程访问，你只需要在路由器上转发端口 80 和 443（如果它有公共外部 IP 地址）。

相比之下，WebRTC 是一种完全不同的视频传输方式。它使用 P2P 连接和 UDP。这减少了网络负载，但使连接变得困难——BliKVM 需要了解你的网络配置才能正确使用它：公共 IP、NAT 类型等。

为此，BliKVM 会检查哪个网络接口用于默认网关，并尝试使用 Google STUN 服务器找出你的外部 IP 地址。

!!! tip "选择 Google STUN 服务器是出于可靠性考虑。"
    如果你不想使用它，可以选择任何其他公共 STUN 服务器，或者设置你自己的服务器。如果你发现公网下拿不到图像，也请检查下面配置
    编辑 /opt/janus/etc/janus/janus.jcfg（示例）：
    ```
        stun_server = "stun1.l.google.com"
        stun_port = 19302
    ```
    然后使用 systemctl restart kvmd-web 重启整个 服务。