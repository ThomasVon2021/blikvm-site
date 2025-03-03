# 认证

!!! warning "BliKVM 配备了以下默认密码"

    * **Linux 操作系统级管理员**（SSH，控制台...）：
        * 用户名：`blikvm`
        * 密码：`blikvm`

    * **KVM 用户**（Web 界面）：
        * 用户名：`admin`
        * 密码：`admin`
        * 无 2FA 代码

    **它们是两个独立的账户，拥有独立的密码。**

!!! danger "不要忘记在新设备上更改这两个密码"

    本页面描述了如何更改密码并启用双因素认证。

    如果您计划将 BliKVM 暴露在互联网上或在不受信任的网络中使用，强烈建议启用 2FA。

-----
## 在终端中获取 root 访问权限
```
sudo -s
```


-----
## 更改 Linux 密码

```console
[root@blikvm ~]# rw
[root@blikvm ~]# passwd root
[root@blikvm ~]# ro
```


-----
## 更改 KVM 密码

此密码用于 Web UI 登录 以及其他与操作系统 shell 无关的功能。
您可以通过 Web 用户管理界面更改账户密码。
默认账户密码文件保存在 `/mnt/exec/release/config/user.json` 中。

-----
## 双因素认证

2FA 是一种增强 BliKVM 保护的新方法，自 `version >= v1.5.3` 起可用。
如果您将 BliKVM 暴露在互联网中，强烈建议启用它。

!!! warning
    请注意，2FA 不涉及 Linux 操作系统的 `root` 用户访问，因此请为 SSH 访问设置一个强密码（或设置 [密钥访问](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server)）。

??? example "在 BliKVM 上启用 2FA"
    可以在 Web 的 UI 管理界面中启用和禁用 2FA。

所有 Web UI 用户在登录时都需要输入一次性密码。
换句话说，**所有用户的密钥是相同的**。

----
## 会话过期

开发中。

----
## 禁用认证

如有必要，您可以禁用 KVM 访问（Web UI，除 SSH 外）的认证。

将 `/mnt/exec/release/config/app.json` 中的 `auth` 字段修改为 `false`。在禁用登录认证之前，请确保您处于足够安全的环境中。
