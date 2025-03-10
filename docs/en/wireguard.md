WireGuard is a modern, simple, and efficient VPN technology that uses public key encryption and end-to-end encrypted communication to protect network traffic. When you have a public server, you can use WireGuard to create a virtual private network (VPN), and each of your KVMs can join the virtual LAN created by WireGuard, enabling remote access from different locations.

!!! warning "The latency of the virtual LAN created using WireGuard depends on your public server's bandwidth and the public server's line latency."
    * If your KVM needs to access from different countries and you are unsure how to choose the appropriate server and line, you can join Discord for support.

## **Installation Steps**

### **Install WireGuard**
1. Install WireGuard on Linux
For most Debian-based systems (such as Ubuntu), you can run the following commands to install WireGuard. To install on KVM, refer to this method. KVM is a read-only system, so you need to use the `rw` command to change it to a readable and writable system first:
```
sudo apt update
sudo apt install wireguard
```
For other Linux distributions, you can install it according to the corresponding package manager or use the official WireGuard installation guide.

2. Install WireGuard on Windows or macOS
Directly download the installation package suitable for your PC system from the [WireGuard official website](https://www.wireguard.com/install/). After installation, configure it through the graphical interface.

### **Configure WireGuard**
WireGuard configuration includes two parts:
Server-side configuration: The machine running the WireGuard server (usually the public server).
Client-side configuration: The client machine connecting to the WireGuard VPN (usually the KVM device and the control computer, not the controlled computer).

!!! info "Configure the Server"
    * Generate the WireGuard private key and public key on the server. In any path you can read and write, execute the following command to get the server_private_key and server_public_key files.
    ```
        wg genkey | tee server_private_key | wg pubkey > server_public_key
    ```
    * Create or edit the /etc/wireguard/wg0.conf file to configure the WireGuard interface. Here is a sample configuration:
    ```
        [Interface]
        PrivateKey = <server private key>
        Address = 10.0.0.1/24  # This is the IP address pool in the VPN network, 10.0.0.1 is the virtual IP of the WireGuard server
        ListenPort = 51820  # WireGuard default port, can be changed to the required port

        # Allowed client 1, assuming it is a KVM
        [Peer]
        PublicKey = <client public key>
        AllowedIPs = 10.0.0.2/32  # Client's IP address

        # Allowed client 2, assuming it is a MAC
        [Peer]
        PublicKey = <client public key>
        AllowedIPs = 10.0.0.3/32  # Client's IP address
    ```
    * The **server private key** here refers to the content of the server_private_key generated above. You need to copy and paste the content of the server_private_key into the configuration file, not the file path.
    * The **client public key** here is the content of the client_public_key generated in the client-side configuration step. You need to copy and paste the content of the client_public_key into the configuration file.
    * Note that for each additional client, the server configuration needs to add a corresponding [Peer] section.

!!! info "Configure the Client"
    Generate the WireGuard private key and public key on the client. Taking the KVM Linux system as an example:
    ```
        wg genkey | tee client_private_key | wg pubkey > client_public_key
    ```
    Create or edit the /etc/wireguard/wg0.conf file to configure the WireGuard client interface. The configuration file content is the same for Windows/macOS graphical interface configuration.
    ```
        [Interface]
        PrivateKey = <client private key>
        Address = 10.0.0.2/32  # Client's IP address

        [Peer]
        PublicKey = <server public key>
        Endpoint = <server IP address>:51820  # Server's IP and port
        AllowedIPs = 10.0.0.0/24  # Route all traffic through the VPN
        PersistentKeepalive = 25  # Keepalive interval, suitable for NAT networks
    ```
    * The **client private key** is the content of the client_private_key file above, and the **server public key** is the content of the server_public_key file generated in the server configuration section.
    * Similarly, assuming the configuration on a MAC, the configuration file content is as follows:
    ```
        [Interface]
        PrivateKey = <client private key>
        Address = 10.0.0.3/32  # Client's IP address

        [Peer]
        PublicKey = <server public key>
        Endpoint = <server IP address>:51820  # Server's IP and port
        AllowedIPs = 10.0.0.0/24  # Route all traffic through the VPN
        PersistentKeepalive = 25  # Keepalive interval, suitable for NAT networks
    ```

### **Start WireGuard**
Start the WireGuard server. On the server (example server is Ubuntu system), start the WireGuard service using the following command:
```
sudo wg-quick up wg0
```
This will start the server-side interface according to the /etc/wireguard/wg0.conf configuration file.

Start the client. On the client, start the WireGuard service. Taking KVM as an example, other systems like MAC or Windows usually start through UI operations.
```
sudo wg-quick up wg0
```

### Configure Firewall (if needed)
    * Open the ListenPort port in the server-side configuration file on the server side.
    * If the clients can ping the server but cannot ping each other, you need to enable forwarding on the server using the following command:
    ```
    echo "net.ipv4.ip_forward=1" | tee -a /etc/sysctl.conf
    sysctl -p
    ```

### Test Connection
On the KVM client, use the ping command to test the connection with the server and MAC:
```
# Test with the server at 10.0.0.1
ping 10.0.0.1 
# Test with the MAC at 10.0.0.3
ping 10.0.0.3
```
Additionally, you can directly use the command to check the status:
```
sudo wg show
```
If everything is configured correctly, you should see the client successfully connected and exchanging keys.

### Enable Auto-Start on Boot
To ensure the WireGuard configuration automatically starts after a system reboot, use the following command:
```
sudo systemctl enable wg-quick@wg0
```

## Summary
Setting up a network with WireGuard involves installation, key configuration, interface configuration, starting the service, and ensuring correct routing and firewall configuration. As long as each client and server configuration is correct and the network allows, they can successfully establish a connection through the WireGuard VPN.
