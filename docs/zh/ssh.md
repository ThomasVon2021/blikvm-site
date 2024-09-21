# SSH配置
在1.4.7版本及以后，web支持直接进入blikvm的ssh终端，默认进入终端的账号密码为 blikvm/blikvm， 如果修改了此用户的密码信息，需要在app.json文件中修改对应的账号密码
```
sudo -s
vim /mnt/exec/release/config/app.json
// 找到下面配置，修改成你修改后的。
"sshUser": "blikvm",
"sshPassword": "blikvm"
```