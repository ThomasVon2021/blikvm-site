# **Port forwarding**

After v1.5.7 version If your ISP provides an external IP address for the router, you can configure Port forwarding to access BliKVM:

* The HTTP protocol uses port 80, and the HTTPS protocol uses port 443. You can modify the configuration file `vim /mnt/exec/release/config/app.json` to change the default ports:
```
    "https_port": 443,
    "http_port": 80,
```

If you do not have an external IP address, we suggest trying to use [Tailscale VPN](./tailscale.md)。
