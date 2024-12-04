# **Encryption Certificate**
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

# **Let's Encrypt**
!!! info
    You need a publicly valid domain name to use Let's Encrypt. This example uses the domain blikvm.space.
1. Start applying for the certificate
Run the following command to start applying for the certificate:
```
certbot certonly --manual --preferred-challenges dns -d example.com
```
2. Add a DNS record in the domain console.
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
After executing the above command, you will see similar output. Follow the prompts to log in to the domain backend (such as Amazon Cloud, Alibaba Cloud, Tencent Cloud, etc.), add a TXT record named _acme-challenge.example.com, and use UyC2WAhvG9zDuyDPKAHovW6y-RxpZ1_KB8XnT4UyAnc as the record value.

3. When the DNS record takes effect, press Enter to continue.
!!! warn
    - DNS records do not take effect immediately, so press Enter later.
    - Use the command nslookup -type=TXT _acme-challenge.blikvm.space to verify if the DNS is effective, as shown below:
    ```
    root@blikvm(rw):/mnt/tmp# nslookup -type=TXT _acme-challenge.blikvm.space
    Server:		192.168.8.1
    Address:	192.168.8.1#53

    Non-authoritative answer:
    _acme-challenge.blikvm.space	text = "UyC2WAhvG9zDuyDPKAHovW6y-RxpZ1_KB8XnT4UyAnc"
    Authoritative answers can be found from:
    ```
You will receive a certificate application success prompt (similar to the following content):
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
4. Use the certificate
According to step 3, you can see that the certificate path is in /etc/letsencrypt/live/blikvm.space/. Modify the configuration file:
```
vim /mnt/exec/release/config/app.json
Replace the following key and cert with
"server": {
    "ssl": {
    "key": "/etc/letsencrypt/live/blikvm.space/privkey.pem",
    "cert": "/etc/letsencrypt/live/blikvm.space/fullchain.pem"
}
```
5. Set the local domain name for blikvm. Open /etc/hosts on the PC, and add the following line. The IP and domain name here depend on your actual situation.
```
192.168.8.16 blikvm.space
```

6. Then you can directly access blikvm using the domain name.
![](assets/images/https/letsencrypt.png){width="400"}
