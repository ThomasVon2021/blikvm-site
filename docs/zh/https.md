# **加密证书**

blikvm v1.5.6版本后,默认为https启动，即使你使用http访问，也会被重定向为http协议;
```
sudo -s
vim /mnt/exec/release/config/app.json
```
找到下面配置内容，其中key和cert在 /mnt/exec/release/lib/https/ 此路径，用户可以自己进行替换；
如果希望使用http协议，将protocol字段改为http；
修改配置后，命令行使用`systemctl restart  kvmd-web`重启即可；
```
"server": {
    "protocol": "https",
    "ssl": {
    "key": "./lib/https/key.pem",
    "cert": "./lib/https/cert.pem"
}
```

# Let's Encrypt申请合法证书:
!!! info
    你需要有一个公网合法的域名才能使用Let's Encrypt,本说明以blikvm.space域名为例
1. 开始申请证书
执行如下命令开始申请证书：
```
certbot certonly --manual --preferred-challenges dns -d example.com
```
2. 在域名控制台中添加解析记录.
```
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator manual, Installer None
Requesting a certificate for blikvm.space
Performing the following challenges:
dns-01 challenge for blikvm.space

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please deploy a DNS TXT record under the name
_acme-challenge.blikvm.space with the following value:

UyC2WAhvG9zDuyDPKAHovW6y-RxpZ1_KB8XnT4UyAnc

Before continuing, verify the record is deployed.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Press Enter to Continue
```
执行完上面命令后,会有如上类似输出，根据上面提示，登录域名后台（比如亚马逊云，阿里云、腾讯云等等），添加名为 _acme-challenge.example.com 的 TXT 记录，并使用 UyC2WAhvG9zDuyDPKAHovW6y-RxpZ1_KB8XnT4UyAnc 作为记录值。 

3. 当DNS记录生效后，点击回车继续  
!!! warn
    - 由于 DNS 记录不会马上生效，所以稍后再按回车键。
    - 使用 nslookup -type=TXT _acme-challenge.blikvm.space 命令验证 DNS 是否生效，生效如下:
    ```
    root@blikvm(rw):/mnt/tmp# nslookup -type=TXT _acme-challenge.blikvm.space
    Server:		192.168.8.1
    Address:	192.168.8.1#53

    Non-authoritative answer:
    _acme-challenge.blikvm.space	text = "UyC2WAhvG9zDuyDPKAHovW6y-RxpZ1_KB8XnT4UyAnc"
    Authoritative answers can be found from:
    ```
将会收到证书申请成功的提示（类似如下内容）：
```
Waiting for verification...
Cleaning up challenges
Subscribe to the EFF mailing list (email: info@blicube.com).

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/blikvm.space/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/blikvm.space/privkey.pem
   Your certificate will expire on 2025-03-04. To obtain a new or
   tweaked version of this certificate in the future, simply run
   certbot again. To non-interactively renew *all* of your
   certificates, run "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le
```
4. 使用证书
根据步骤3可以看到证书路径在/etc/letsencrypt/live/blikvm.space/，修改配置文件：
```
vim /mnt/exec/release/config/app.json
将下面key和cert替换为
"server": {
    "ssl": {
    "key": "/etc/letsencrypt/live/blikvm.space/privkey.pem",
    "cert": "/etc/letsencrypt/live/blikvm.space/fullchain.pem"
}
```
5. 设置blikvm的局域网域名，在pc上打开/etc/hosts,如可以增加下面这一行，这里的ip和域名根据你的实际情况而定
```
192.168.8.16 blikvm.space
```

6. 然后你就可以直接用域名访问blikvm。
![](assets/images/https/letsencrypt.png){width="400"} 