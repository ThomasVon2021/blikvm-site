# **Tailscale VPN**

[Tailscale](https://tailscale.com/) can be used to access your BliKVM from the public internet. It is a convenient and free networking tool for setting up a small VPN network. This document provides an example for accessing your BliKVM over the internet, but you can also use Zerotier or other VPN solutions. The following is a basic example, and for any specific settings or functionalities, please refer to the Tailscale documentation.

## **BliKVM安装Tailscale**
First, make sure that your system has read-write access. If it's a read-only system, use the rw command to make it writable. Then, proceed with the Tailscale [installation](https://tailscale.com/download) by running the following command:
```
curl -fsSL https://tailscale.com/install.sh | sh
```
!!! warning "Note that in some regions, such as China, downloading Tailscale directly might be problematic due to network restrictions. Please configure your network accordingly."

## **Adding BliKVM to your Tailscale Network**
Register an account on the Tailscale website and generate your own keys in the settings. On the BliKVM terminal, use the following command to add BliKVM to your Tailscale network:
```
sudo tailscale up --authkey=your-auth-key --accept-routes
```
If everything goes well, you can run ip addr show tailscale0 on the BliKVM terminal to view the IP address assigned by Tailscale for the virtual network. Here's an example output:
```
3: tailscale0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1280 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/none
    inet 100.126.223.28/32 scope global tailscale0
       valid_lft forever preferred_lft forever
    inet6 fd7a:115c:a1e0:ab12:4843:cd96:627e:df1c/128 scope global
       valid_lft forever preferred_lft forever
    inet6 fe80::8955:99dc:4e7d:b08b/64 scope link stable-privacy
       valid_lft forever preferred_lft forever
```
The IP address, such as 100.126.223.28, can be used to access the BliKVM web interface from your host machine.

## **主机安装Tailscale**
[Download](https://tailscale.com/download) and install Tailscale from the Tailscale website on your controlling host machine. Log in with your Tailscale account, and then you can check the Tailscale [admin page](https://login.tailscale.com/admin/machines) to verify if both your machines are online. Once they are online, you can use the following address to access BliKVM from your controlling host machine:
```
http://<tailscale_kvm_ip>
```

