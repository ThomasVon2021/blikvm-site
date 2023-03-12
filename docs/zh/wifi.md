# Wifi功能
!!! warning "由于BLIKVM有多款硬件，支持不同的OS，如BLIKVM OS和PiKVM OS，不同OS链接wifi方式不一定相同，请在使用本文档方法前，请确认自己硬件和使用OS的情况。"
    1. 请确认你使用的硬件支持wifi功能，如CM400200版本不带wifi功能；
    2. 若KVM硬件的SOC为CM4，请确认是否连接了wifi天线；
    3. PiKVM OS为arch linux；
    4. BLIKVM OS树莓派系列为debian系统，H616系列为armbian系统；

## **在树莓派debian系统上使用raspi-config进行wifi链接**

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

