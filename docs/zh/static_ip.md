# **BliKVM OS设置静态IP**

## v1 v2 v3参考
1. 使用SSH连接到BliKVM的终端,如果是只读系统，请使用`rw`命令使系统可写。
2. 打开网络配置文件`/etc/dhcpcd.conf`以进行编辑：
   ```
   sudo vim /etc/dhcpcd.conf
   ```
3. 在文件末尾添加以下内容，替换为您想要设置的IP地址、网关和DNS服务器：
   ```
   interface eth0
   static ip_address=192.168.0.100/24
   static routers=192.168.0.1
   static domain_name_servers=192.168.0.1
   ```
   注意：根据您的网络设置，可能需要修改上述示例中的IP地址、网关和DNS服务器的值。
4. 保存文件并退出编辑器。
5. 重新启动BliKVM以使静态IP设置生效：
   ```
   sudo reboot
   ```

## v4参考
1. 使用SSH连接到BliKVM的终端,如果是只读系统，请使用`rw`命令使系统可写。
2. 打开网络配置文件`/etc/network/interfaces`以进行编辑：
   ```
   sudo vim /etc/network/interfaces
   ```
3. 在文件末尾添加以下内容，替换为您想要设置的IP地址、网关和DNS服务器：
   ```
   source /etc/network/interfaces.d/*
   auto eth0
   allow-hotplug eth0
   iface eth0 inet static
   address 192.168.0.100
   netmask 255.255.255.0
   gateway 192.168.0.1
   dns-nameservers 192.168.0.1
   ```
   注意：根据您的网络设置，可能需要修改上述示例中的IP地址、网关和DNS服务器的值。
4. 保存文件并退出编辑器。
5. 重新启动BliKVM以使静态IP设置生效：
   ```
   sudo reboot
   ```

根据您的网络环境和需求，您可以根据上述步骤自定义配置静态IP地址。请确保IP地址、网关和DNS服务器的设置与您的网络设置相匹配。