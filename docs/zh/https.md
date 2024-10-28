# 加密证书

blikvm v1.4.9版本后,默认为https启动，即使访问http也会自动被重定向到https:
```
sudo -s
vim /mnt/exec/release/config/app.json
```
找到下面配置内容，其中key和cert在 /mnt/exec/release/lib/https/ 此路径，用户可以自己进行替换。
```
"server": {
    "ssl": {
    "key": "./lib/https/key.pem",
    "cert": "./lib/https/cert.pem"
}
```