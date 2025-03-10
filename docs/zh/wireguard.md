WireGuard 是一个现代化的、简洁高效的 VPN 技术，它使用公钥加密和端到端的加密通信来保护网络流量。当你有公网服务器时，你可以通过 WireGuard 组建一个虚拟私有网络（VPN），你的每一台kvm都可以加入到WireGuard组建的虚拟局域网里，从而实现远程异地访问。

!!! warning "使用WireGuard组建虚拟局域网，延迟的大小，取决于你的公网服务器带宽和公网服务器的线路延迟"
    * 如果你的KVM需要进行异国访问，不清楚如果选择合适的服务器和线路，可以加入discord获得支持。

## **安装步骤**

### **安装 WireGuard**
1. 在 Linux 上安装 WireGuard
对于大多数基于 Debian 的系统（如 Ubuntu），可以运行以下命令安装 WireGuard,在KVM上安装即要参考此方法,KVM是只读系统，需要先试用`rw`指令改为可读写系统；
```
sudo apt update
sudo apt install wireguard
```
对于其他 Linux 发行版，可以根据相应的包管理器进行安装，或者使用 WireGuard 官方安装指南。

2. 在 Windows或者mac上安装WireGuard, 直接在[WireGuard官网](https://www.wireguard.com/install/)下载页面,下载适用于你PC系统的安装包。
完成安装后，通过图形界面进行配置。

### **配置 WireGuard**
WireGuard配置包括两部分：
服务器端配置：运行 WireGuard服务器的机器。(一般是指公网服务器)
客户端配置：连接到 WireGuard VPN 的客户端机器。(一般是指KVM设备和用来的控制电脑（不是被控电脑）)

!!! info "配置服务器"
    * 在服务器上生成 WireGuard 的私钥和公钥，在任意你可以读写的路径，执行下面命令，会得到server_private_key和server_public_key文件。
    ```
        wg genkey | tee server_private_key | wg pubkey > server_public_key
    ```
    * 创建或编辑 /etc/wireguard/wg0.conf 文件，配置 WireGuard 接口。下面是一个示例配置：
    ```
        [Interface]
        PrivateKey = <服务器私钥>
        Address = 10.0.0.1/24  # 这是 VPN 网络中的 IP 地址池，10.0.0.1 是 WireGuard 服务器的虚拟 IP
        ListenPort = 51820  # WireGuard 默认端口，可以更改为需要的端口

        # 允许的客户端1，假设是一台KVM
        [Peer]
        PublicKey = <客户端公钥>
        AllowedIPs = 10.0.0.2/32  # 客户端的 IP 地址
        这里的 PrivateKey 是服务器端生成的私钥，Address 是服务器在 VPN 网络中的地址。

        # 允许的客户端2，假设是一台MAC
        [Peer]
        PublicKey = <客户端公钥>
        AllowedIPs = 10.0.0.3/32  # 客户端的 IP 地址
        这里的 PrivateKey 是服务器端生成的私钥，Address 是服务器在 VPN 网络中的地址。
    ```
    * 这里**服务器私钥**是指上面生成的server_private_key内容，你需要将server_private_key内容复制粘贴到配置文件里，而不是填写文件路径；
    * 这里的**客户端公钥**是后面步骤中，在客户端生成的client_public_key的内容，你需要将client_public_key内容复制粘贴到配置文件里；
    * 需要注意的是，每增加一个客户端，服务端的配置都需要对应增加一个[Peer]部分

!!! info "配置客户端"
    在客户端上生成 WireGuard 的私钥和公钥,以KVM的linux系统为例子:
    ```
        wg genkey | tee client_private_key | wg pubkey > client_public_key
    ```
    创建或编辑 /etc/wireguard/wg0.conf 文件，配置 WireGuard 的客户端接口, Windows/macOS 图形界面配置,配文件内容是一样的。
    ```
        [Interface]
        PrivateKey = <客户端私钥>
        Address = 10.0.0.2/32  # 客户端的 IP 地址

        [Peer]
        PublicKey = <服务器公钥>
        Endpoint = <服务器 IP 地址>:51820  # 服务器的 IP 和端口
        AllowedIPs = 10.0.0.0/24  # 路由所有流量通过 VPN
        PersistentKeepalive = 25  # 保持连接的间隔时间，适合 NAT 网络
    ```
    * **客户端私钥**是上面client_private_key文件的内容，**服务器公钥**为配置服务器部分生成的server_public_key文件内容;
    * 同理假设在MAC上配置，配置文件内容如下:
    ```
        [Interface]
        PrivateKey = <客户端私钥>
        Address = 10.0.0.3/32  # 客户端的 IP 地址

        [Peer]
        PublicKey = <服务器公钥>
        Endpoint = <服务器 IP 地址>:51820  # 服务器的 IP 和端口
        AllowedIPs = 10.0.0.0/24  # 路由所有流量通过 VPN
        PersistentKeepalive = 25  # 保持连接的间隔时间，适合 NAT 网络
    ```

### **启动 WireGuard**
启动WireGuard服务器,在服务器上（例子服务器为ubuntu系统），启动 WireGuard 服务,可以使用以下命令
```
sudo wg-quick up wg0
```
这将根据 /etc/wireguard/wg0.conf 配置文件启动服务器端接口。

启动客户端,在客户端上，启动 WireGuard 服务,以KVM上为例，其他如MAC或者windows图形化界面启动方式一般是UI操作。
```
sudo wg-quick up wg0
```

### 配置防火墙（如果需要）
    * 服务器端放开上面服务端配置文件中的ListenPortdu端口；
    * 如果出现了，各个客户端可以ping通服务器，但是客户端之间ping不通，那么需要打开服务器的转发功能，使用以下命令：
    ```
    echo "net.ipv4.ip_forward=1" | tee -a /etc/sysctl.conf
    sysctl -p
    ```

### 测试连接
在KVM客户端上，使用 ping 命令测试与服务器和MAC的连接：
```
# 10.0.0.1和服务器进行测试
ping 10.0.0.1 
# 10.0.0.3和MAC进行测试
ping 10.0.0.3
```
另外，你可以直接使用命令查看状态:
```
sudo wg show
```
如果一切配置正确，你应该能看到客户端成功连接并交换密钥。

### 开机自启动
为了确保 WireGuard 配置在系统重启后自动启动，可以使用以下命令：
```
sudo systemctl enable wg-quick@wg0
```

## 总结
通过 WireGuard 组网涉及安装、配置密钥、配置接口、启动服务，并确保路由和防火墙配置正确。只要每个客户端和服务器的配置都正确，并且网络允许，它们就能够通过 WireGuard VPN 成功建立连接。


