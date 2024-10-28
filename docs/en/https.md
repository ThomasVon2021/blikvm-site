# Encryption Certificate
From version v1.4.9, blikvm defaults to HTTPS. Even if you access via HTTP, it will automatically redirect to HTTPS:
```
sudo -s
vim /mnt/exec/release/config/app.json
```
Find the following configuration content. The key and cert are located in the path /mnt/exec/release/lib/https/. Users can replace them as needed.
```
"server": {
    "ssl": {
    "key": "./lib/https/key.pem",
    "cert": "./lib/https/cert.pem"
}
```