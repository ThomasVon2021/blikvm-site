[Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/) can be used to access your BliKVM device from the public internet. This is a convenient and free tool (for up to 50 users) that allows access to web services running on your internal network without needing a public IP.

## Prerequisites
1. You need to have a domain name;
2. [You need to modify the web service to an HTTP service](./https.md);
3. [Add your domain to Cloudflare](https://developers.cloudflare.com/fundamentals/setup/manage-domains/add-site/);
4. [Change your domain's nameservers to Cloudflare](https://developers.cloudflare.com/dns/zone-setups/full-setup/setup/).

## Steps Reference

You can directly refer to the [official documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/get-started/create-remote-tunnel/). Here are a few additional notes to keep in mind:

1. When creating a tunnel on the web, you will be asked to select the system and architecture. Choose Debian for the system and 64-bit for the architecture. Then, an installation command for cloudflared will appear. Copy the command to the SSH terminal of your BliKVM and install it.

2. When adding a public hostname, only fill in the domain, which is the domain you have added to Cloudflare. Do not add a path. For the service type, select HTTP, and for the URL, if the port has not been modified, enter localhost.

3. After the tunnel is created, as shown in the image below, you can directly use the domain to access your BliKVM in the browser. Note that if you have a model that supports H264, switch the video mode to H264 in the web interface for smoother performance.
![](assets/images/cf/tunnel.png){width="600"}