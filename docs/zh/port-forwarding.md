# **端口转发**

在v1.5.7版本后,如果您的ISP为路由器提供了外部IP地址，您可以配置端口转发以访问BliKVM。

* http协议，占用的是80端口，https协议占用的是443, 你可以修改配置文件`vim /mnt/exec/release/config/app.json`来修改默认端口:
```
    "https_port": 443,
    "http_port": 80,
```

如果您没有外部IP地址，我们建议尝试使用[Tailscale VPN](./tailscale.md)。
