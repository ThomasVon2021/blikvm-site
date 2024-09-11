# 加密证书

blikvm v1.4.4版本后,开始支持http和https两种模式, 默认以http形式启动，如果需要以https启动，需要修改以下配置:
```
sudo -s
vim /mnt/exec/release/config/app.json
```
找到下面配置内容，将protocol字段对应http改为https，port端口由80改为443，其中key和cert在 /mnt/exec/release/lib/https/ 此路径，用户可以自己进行替换。
```
"server": {
    "protocol": "http",
    "port":80,
    "ssl": {
    "key": "./lib/https/key.pem",
    "cert": "./lib/https/cert.pem"
}
```