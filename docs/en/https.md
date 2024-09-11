# Encryption Certificate

Starting from version 1.4.4, BlikVM supports both HTTP and HTTPS modes. By default, it starts in HTTP mode. To start in HTTPS mode, modify the following configuration:

```
sudo -s
vim /mnt/exec/release/config/app.json
```

Find the configuration below and change the protocol field from http to https, and change the port from 80 to 443. The key and cert are located in /mnt/exec/release/lib/https/, and users can replace them with their own.

```
"server": {
    "protocol": "http",
    "port":80,
    "ssl": {
    "key": "./lib/https/key.pem",
    "cert": "./lib/https/cert.pem"
}
```