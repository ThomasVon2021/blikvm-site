It uses efficient H.264 encoding to save bandwidth. Video is streamed via the WebRTC protocol, which you might have encountered when using Discord or Google Chat for video calls.

It is compatible with BliKVM v1, v2, v3, and all DIY devices based on the HDMI-CSI bridge.

You can switch video modes in the system menu of the Web UI. If you don't see the switch option, it might be because your browser does not support H.264 video.

## **How It Works**
MJPEG video is streamed via an HTTP connection similar to fetching the Web UI. This means for remote access, you only need to forward ports 80 and 443 on your router (if it has a public external IP address).

In contrast, WebRTC is a completely different video transmission method. It uses P2P connections and UDP. This reduces network load but makes the connection more complex—BliKVM needs to understand your network configuration to use it correctly: public IP, NAT type, etc.

To achieve this, BliKVM checks which network interface is used for the default gateway and tries to find out your external IP address using Google's STUN server.

!!! tip "Choosing Google's STUN server is for reliability reasons."
    If you don't want to use it, you can choose any other public STUN server or set up your own server. If you find that you can't get an image under public network, please check the configuration below:
    Edit /opt/janus/etc/janus/janus.jcfg (example):
    ```
        stun_server = "stun1.l.google.com"
        stun_port = 19302
    ```
    Then restart the entire service using systemctl restart kvmd-web.