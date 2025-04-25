# Wifi功能
!!! warning "由于BLIKVM有多款硬件，支持不同的OS，如BLIKVM OS和PiKVM OS，不同OS链接wifi方式不一定相同，请在使用本文档方法前，请确认自己硬件和使用OS的情况。"
    1. 请确认你使用的硬件支持wifi功能，如CM400200版本不带wifi功能；
    2. 若KVM硬件的SOC为CM4，请确认是否连接了wifi天线；
    3. PiKVM OS为arch linux；
    4. BLIKVM OS树莓派系列为debian系统，v4系列为armbian系统；

## **v1，v2，v3硬件使用的为树莓派debian系统，使用raspi-config进行wifi链接**

1. 登录ssh,命令: ssh blikvm@ip
2. 系统重加载为可写, 命令: rw
3. 启动raspi-config, 命令: sudo raspi-config
4. 选择 System Options
5. 选择 Wireless LAN
6. 选择wifi所在国家,中国选CN, 如果以前设置过,这一步会跳过直接到7
7. 输入Wi-Fi的ssid(名称)
8. 输入Wi-Fi的密码,如果没有密码直接回车
9. 这时会回到步骤4的界面,按tab键选择<Finish>,回车
10. 查看是否连上wifi, 命令: ifconfig wlan0 ,如果看到获取到ip就是已经连上了
11. 将系统挂载为只读, 命令: ro

## **v4硬件使用的为armbian系统，使用armbian-config**
!!! info "如果出现连接错误，您可以修改配置文件并重新连接"
    ```bash
        sudo vim /etc/NetworkManager/NetworkManager.conf
        # make sure ifupdown if true
        [main]
        dns=none
        plugins=ifupdown,keyfile

        [ifupdown]
        managed=true

        [device]
        wifi.scan-rand-mac-address=no
    ```
    ```
        systemctl restart NetworkManager
    ```

1. 登录ssh,命令: ssh blikvm@ip，登录到 Armbian 系统. 如果是只读系统需要先使用命令`rw`变为可读写,并且使用命令`sudo chmod 777 -R /etc/NetworkManager/system-connections`给对应文件夹权限, 修改权限后需要重启NetworkManager服务生效 `systemctl restart NetworkManager`.
2. 输入以下命令以启动 `armbian-config` 工具：
   ```
   sudo armbian-config
   ```
3. 在 `armbian-config` 菜单中，使用方向键和回车键导航和选择选项。
4. 使用方向键向下滚动到 "Network" 选项，并按回车键进入子菜单。
5. 在 "Network" 子菜单中，选择 "Wireless" 选项并按回车键进入 Wi-Fi 配置菜单。
6. 在 Wi-Fi 配置菜单中，选择 "Connect to Wi-Fi" 选项并按回车键进入 Wi-Fi 连接设置。
7. `armbian-config` 将列出可用的无线网络接口和已配置的网络。选择要连接的无线网络接口并按回车键。
8. `armbian-config` 将显示可用的 Wi-Fi 网络列表。使用方向键选择要连接的 Wi-Fi 网络并按回车键。
9. 如果 Wi-Fi 网络受到密码保护，`armbian-config` 将提示您输入 Wi-Fi 密码。输入密码并按回车键。
10. 等待片刻，Armbian 系统将尝试连接到指定的 Wi-Fi 网络。如果连接成功，您将在屏幕上看到相应的消息。
11. 退出 `armbian-config` 工具。

请注意，上述步骤中的菜单选项和配置可能会根据不同版本的 Armbian 系统略有不同。确保根据您的系统版本和配置进行相应的操作。

