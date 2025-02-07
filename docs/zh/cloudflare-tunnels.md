[Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/)可用于公网下来访问你的BliKVM设备。这是一个方便且免费的（适用于 50 个用户）工具，允许访问内部网络上运行的 Web 服务，无需公网ip。

## 前提条件
1. 你需要有一个域名;
2. [你需要修改web服务为http服务](./https.md);
3. [将你的域名添加到 Cloudflare](https://developers.cloudflare.com/fundamentals/setup/manage-domains/add-site/);
4. [将你的域名服务器更改为 Cloudflare](https://developers.cloudflare.com/dns/zone-setups/full-setup/setup/)。

## 步骤参考

可以直接参考[官方文档](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/get-started/create-remote-tunnel/),这里有几点需要注意的补充说明一下:

1. 在网页创建隧道时，会让你选择系统和架构，系统选择Debian，架构选择64-bit，然后会出现安装cloudflared命令,复制命令到blikvm的ssh终端，进行安装即可。

2. 在添加公共主机名时，只需要填域，即你已经添加到Cloudflare的域名,路径不能添加;服务类型选择http,url在端口没有修改的情况下，填写localhost即可；

3. 创建完成后的隧道如下图所示, 然后你就可以直接在浏览器使用域名访问你的BliKVM了，注意如果是支持H264的型号，在进入web界面后，将video模式切换到h264使用更加流畅。
![](assets/images/cf/tunnel.png){width="600"}