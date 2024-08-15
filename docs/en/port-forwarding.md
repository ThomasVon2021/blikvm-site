# **Port forwarding**

If your ISP provides an external IP address for the router, you can configure Port forwarding to access BliKVM:

* The web interface uses the HTTP protocol and occupies port 80;
* If your hardware is v1 v2 v3 and you are using web rtc transmission, the port is 8188;
* If your hardware is v4 and you are using mjepg transmission, the port is 8008;
* Note that the port does not support modification and can only be configured for forwarding;

If you do not have an external IP address, we suggest trying to use [Tailscale VPN](./tailscale.md)。
