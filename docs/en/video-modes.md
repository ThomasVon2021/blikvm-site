BliKVM v1, v2, and v3 are based on HDMI-CSI capture cards and currently support two video stream modes: H264 and MJPEG, which can be switched on the web interface. BliKVM v4 is based on a USB video capture card and only supports MJPEG mode.

!!! tip "Video Parameter Recommendations"
    * It is recommended to use H264 mode for v1, v2, and v3 as it has low latency and requires less bandwidth.
    * H.264 Mbps (bitrate) - The higher the value, the better the video quality, but it will increase network traffic. Adjust according to network bandwidth in public networks.
    * H.264 GOP (Group of Pictures) - The number of frames that must forcibly add reference frames. Set to 0 in good network conditions and 30 in poor network conditions.

## **WebRTC H.264 Mode**
It uses efficient H.264 encoding to save bandwidth. The video is transmitted via the WebRTC protocol, which you might have encountered during video calls on Discord or Google Chat. Since WebRTC does not use HTTP to transmit video, establishing a connection is more complex (but BliKVM automates 99% of the process). If you encounter issues while using WebRTC mode, please refer to [this guide](./webrtc.md).

!!! info "Pros/Cons"
    * ✅ Supported by all modern browsers.
    * ✅ Supports audio.
    * ❌ Video may be lost due to poor connection (e.g., mobile internet, bad Wi-Fi, etc.) or low WebRTC priority due to router settings.
    * ❌ It may be completely blocked in some networks. If there are many network restrictions during public transmission and STUN fails, the image may not be obtained.
    * ❌ Due to the peculiarities of WebRTC handling in all browsers, latency may sometimes slightly increase.

## **Traditional MJPEG Mode**
Classic Motion JPEG. This is the way IP cameras have transmitted video to browsers since ancient times. The stream is just an infinite queue of JPEG images that replace each other in the <img> HTML tag. If one of the previous modes works fine, there is no need to use this now.

!!! info "Pros/Cons"
    * ✅ Sometimes, due to OS permission restrictions (e.g., in Red Hat Linux or Debian), H.264 is disabled in the browser. But MJPEG always works.
    * ✅ It is not blocked by firewalls as it looks like regular HTTPS traffic.
    * ✅ Low latency if the network is good.
    * ❌ Does not support audio.
    * ❌❌❌ Consumes a lot of bandwidth.

## **Video Saving**
To be updated.
