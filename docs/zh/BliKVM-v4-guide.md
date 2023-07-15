# **BliKVM v4 Allwinner**

![](assets/images/v4/BliKVM-v4-front.png){width="300"}
![](assets/images/v4/BliKVM-v4-back.png){width="300"}  
BliKVM v4是一款生产就绪、即插即用的 KVM-over-IP 设备，为专业用户提供了**远程服务器或工作站管理**的便捷解决方案。 它基于Linux并且完全开源。 借助 BliKVM，您可以轻松**打开/关闭电源、重新启动计算机、配置 UEFI/BIOS 设置以及使用模拟大容量存储设备执行操作系统重新安装**。 BliKVM 模拟键盘、鼠标和显示器，所有这些都可以通过 Web 浏览器访问，确保无缝的用户体验。 **其硬件级访问保证独立于特定的远程端口、协议或服务**，使其成为专业人士高度灵活且可靠的远程管理解决方案！

* [BliKVM V4 Datasheet](./Datasheet-BliKVM-v4.md)

## **安装要求**
!!! note "除v4套件外，您还需自备以下设备"
    * 电源适配器（5V 3A, USB-A端口或12V 2ADC端口）,若你计划使用PoE供电，或者所的被控计算机USB口有充足的供电能力，则也不需要单独的电源适配器；
    * HDMI 线缆(至少一根)，若您同时需要使用HDMI环出接口，则需要2根；
    * 网线（结合您需求自备）,使用ATX开关机功能需一根，使用网线上网功能需一根；
    * USB-C转USB-A线缆一根（用于鼠标和键盘数据传输）.

!!! info "BliKVM v4 拆箱，连接，使用参考视频"
    <iframe src="//player.bilibili.com/player.html?aid=488438623&bvid=BV1NN41127g9&cid=1195577253&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

## **安装步骤**
**1.** 打开v4套件包装，根据下面所示的连接示意图，将BliKVM和被控计算机连接起来；
![](assets/images/v4/v4-Connection-Diagram.png)

**ATX连接**
请参考[ATX连接指南](./atx.md)。

**2.** 在所有连接线连接好后,对BliKVM进行上电，直到显示屏出现画面，即设备正常启动。

**3.** 仔细阅读[**“第一步”**](./first_steps.md)指南-如何在网络上查找设备、如何登录、更改密码等等。按照上面描述的步骤操作，然后返回本页。

**4.** **尝试使用 Web 界面管理计算机的 BliKVM。** 确保您可以看到图像并且键盘和鼠标都正常工作。如果遇到任何问题，请查看我们的[常见问题](./faq.md)（它非常有用）。如果没有任何帮助，请在我们的[Discord聊天室](https://discord.com/invite/9Y374gUF6C)寻求支持。

**5.** 您可以查看wiki其他的页面，探索BliKVM的更多功能，祝您玩的开心！

## **视频模式**
v4最高支持4K30Hz的视频输入，传输分辨率默认为1920x1080。

### 发货清单

| BLIKVM v4 Allwinner版本            | 1    |
| -------------------------------------- | ---- |
| BLIKVM v4               | 1    |
| WiFi天线               | 1    |
| ATX适配板               | 1    |
| ATX杜邦线缆 8pin 母对母 60cm | 1    |
| ATX杜邦线缆 8pin 母对公 60cm | 1    |
| 1U安装挂耳             | 2   |
| M2.5x5螺丝               | 8   |
| 硅胶防撞粒              | 1   |




