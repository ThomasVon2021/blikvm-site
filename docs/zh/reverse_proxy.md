# **反向代理**

反向代理允许您通过您的 Web 服务器将请求传递到另一个站点或程序。反向代理会使 BliKVM Web UI 看起来像是您现有站点中的一个页面。

这在以下情况下特别有用：

* 您需要在端口 `80` 或 `443` 上访问 WebUI，但您已经在同一设备上托管了一个网站。

* 您希望与现有站点共享 SSL 证书。

* 您希望与现有设置共享身份验证。

-----
## **BliKVM 配置**

BliKVM 在最新版本中支持反向代理。对于旧版本，请先进行[更新](./update.md)。



默认情况下，BliKVM 将所有来自 HTTP 端口 `80` 的请求重定向到带有自签名证书的 HTTPS 端口 `443`。对于最简单的配置，您可以保持默认设置，并在您的 Web 服务器上终止来自 BliKVM 的 SSL 流量。

或者，您可以更改 BliKVM 上的 HTTP 和 HTTPS 端口，或者完全禁用 HTTPS 以仅传递 HTTP 流量到您的服务器。

在这两种情况下，您都应该为您的 Web 服务器自行处理 SSL 证书。

??? example "更改 HTTP/HTTPS 设置的各种示例"

    * 更改 HTTP 和 HTTPS 端口。将此配置放置在 BliKVM 的 `/mnt/exec/release/config/app.json` 中：

        ```json
            "protocol": "https",
            "https_port": 443,
            "http_port": 80,
        ```

-----
## **服务器配置**

如果您可以访问您的 Web 服务器配置，请使用以下示例将服务器上的位置 `/` 传递到托管在 HTTPS 端口 `443` 上的 `https://blikvm_ip` 的 BliKVM Web UI。

### **Nginx**

??? info "如何在服务器上安装 nginx？如何为您的域名申请证书？"
    * 在 Ubuntu 服务器上安装 nginx
    ```
        apt update
        apt install nginx -y
    ```
    * 为 nginx 添加配置，您可以在 `/etc/nginx/sites-available/` 中创建一个文件，例如
    ```
        vim /etc/nginx/sites-available/reverse-proxy
    ```
    * 一些有用的命令：
    ```
    # 检查配置
    nginx -t    
    # 更新配置后，需要重启 nginx
    systemctl restart nginx
    ```
    * 申请证书
    ```
    apt install certbot python3-certbot-nginx -y
    certbot renew --dry-run
    ```

Nginx 默认不验证证书。在下面给出的示例中，关于域名和证书，您需要使用您自己的实际信息。

```nginx
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name www.blikvm.space;
    ssl_certificate /etc/letsencrypt/live/www.blikvm.space/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/www.blikvm.space/privkey.pem;
    location / {
    rewrite ^/$ / break;
    rewrite ^/\?(.*)$ ?$1 break;
    rewrite ^//(.*)$ /$1 break;
    proxy_redirect ~^(/.*)$ /$1;
    proxy_pass https://10.0.0.2;

    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Scheme $scheme;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-Port $server_port;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    # 对于某些处理程序（如 MJPEG），应禁用缓冲
    postpone_output 0;
    proxy_buffering off;
    proxy_ignore_headers X-Accel-Buffering;

    # 某些处理程序（以 /ws 结尾）是 WebSockets
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_connect_timeout 7d;
    proxy_send_timeout 7d;
    proxy_read_timeout 7d;

    # 某些其他处理程序需要大的 POST 负载
    client_max_body_size 0;
    proxy_request_buffering off;
    }
}
```
