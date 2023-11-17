# **ZeroTier VPN**

[ZeroTier](https://www.zerotier.com/) allow secure access to your BliKVM even throught NAT on both sides. It lets you build modern, secure multi-point virtualized networks of almost any type. This document provides an example for accessing your BliKVM over the internet, but you can also use Tailscale or other VPN solutions. The following is a basic example, and for any specific settings or functionalities, please refer to the [ZeroTier documentation](https://docs.zerotier.com/).

## **Installing ZeroTier on BliKVM**
First of all, prepare account and VPN network at ZeroTier with instructions here: [Create a Network](https://docs.zerotier.com/start) , save Network ID for later usage. Next, connect with BliKVM terminal using SSH protocol, and check for read-write access. If it's a read-only system, use the rw command to make it writable.
Now install ZeroTier client using command below:
```
curl -s https://install.zerotier.com | sudo bash
```
!!! warning "Note that in some regions, such as China, downloading ZeroTier directly might be problematic due to network restrictions. Please configure your network accordingly."

## **Adding BliKVM to your ZeroTier Network**
On the BliKVM terminal, use the following command to add BliKVM to your ZeroTier network (using ZeoroTier Network ID, for example d5e04297a16fa690):
```
sudo zerotier-cli join d5e04297a16fa690
```
If everything goes well, you can run ip addr show zerotier network device (name is starting with zt) on the BliKVM terminal to view the IP address assigned by ZeroTier for the virtual network. Here's an example output:
```
3: zt6ovrlscs: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 2800 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether d6:e4:eb:ae:db:64 brd ff:ff:ff:ff:ff:ff
    inet 172.25.96.75/16 brd 172.25.255.255 scope global zt6ovrlscs
       valid_lft forever preferred_lft forever
    inet6 fe80::d4e4:ebff:feae:db64/64 scope link 
       valid_lft forever preferred_lft forever
```
The IP address, such as 172.25.96.75, can be used to access the BliKVM web interface from your host machine.

## **Installing ZeroTier on client computer**
Go to [Download](https://www.zerotier.com/download/) section at ZeroTier website and install ZeroTier on your controlling host machine. Join your ZeroTier Network ID, and then you can check your [network page](https://my.zerotier.com/) to verify if both your machines are online. Check if they are authorzied to connect to network there (Auth? column). Once they are online, you can use the following address to access BliKVM from your controlling host machine:
```
http://<zerotier_kvm_ip>
```

