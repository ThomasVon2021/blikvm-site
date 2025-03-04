# **Reverse Proxy**

A reverse proxy allows you to pass requests through your web server to another site or program.
The reverse proxy will make it look like BliKVM Web UI is a page within your existing site.

This is especially useful if:

* You need to access the WebUI on port `80` or `443` but you already host a website on the same device.

* You want to share SSL certificates with an existing site.

* You want to share authentication with an existing setup.


-----
## **BliKVM Configuration**

BliKVM supports reverse proxying in the latest version. For older version, please update OS first:

{!update.md!}

By default, BliKVM redirects all requests from HTTP port `80` to HTTPS port `443` with self-signed
certificate. For the simplest configuration, you can leave it as it is, and terminate
SSL traffic from BliKVM on your web server.

Alternatively, you can change the HTTP and HTTPS ports on BliKVM or disable HTTPS at all
to deliver HTTP-only traffic to your server.

In both cases you should take care of your own SSL certificate for your web server.

??? example "Various examples with changing HTTP/HTTPS settings"

    * Changing HTTP and HTTPS ports. Place this config to `/mnt/exec/release/config/app.json` on BliKVM:

        ```json
            "protocol": "https",
            "https_port": 443,
            "http_port": 80,
        ```

-----
## **Server Configuration**

If you have access to your web server’s configuration use the following examples
to pass the location `/` on the server to BliKVM Web UI hosted on `https://blikvm_ip`
on HTTPS port `443`.


### **Nginx**

??? info "How to install nginx on server? How to certificate your domain?"
    * Install nginx on ubuntu server
    ```
        apt update
        apt install nginx -y
    ```
    * Add a config for nginx, you can touch a file in `/etc/nginx/sites-available/`,like
    ```
        vim /etc/nginx/sites-available/reverse-proxy
    ```
    * Some useful command:
    ```
    # check config
    nginx -t    
    # when you update the config, you need to restart the nginx
    systemctl restart nginx
    ```
    * Apply for certificate
    ```
    apt install certbot python3-certbot-nginx -y
    certbot renew --dry-run
    ```

Nginx does not validate certificates by default. In the example given below, regarding domain names and certificates, you need to use your own actual ones.

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

    # For some handles (like MJPEG) buffering should be disabled
    postpone_output 0;
    proxy_buffering off;
    proxy_ignore_headers X-Accel-Buffering;

    # Some handles (ends with /ws) are WebSockets
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_connect_timeout 7d;
    proxy_send_timeout 7d;
    proxy_read_timeout 7d;

    # Some other handles requires big POST payload
    client_max_body_size 0;
    proxy_request_buffering off;
    }
}
```
