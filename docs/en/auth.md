# Authentication

!!! warning "BliKVM comes with the following default passwords"

    * **Linux OS-level admin** (SSH, console...):
        * Username: `blikvm`
        * Password: `blikvm`

    * **KVM user** (Web Interface):
        * Username: `admin`
        * Password: `admin`
        * No 2FA code

    **They are two separate accounts with independent passwords.**

!!! danger "Don't forget to change BOTH passwords on the new device"

    This page describes how to do this and enable two-factor authentication.

    The 2FA is also strongly recommended if you plan to expose BliKVM to the internet
    or use it in untrusted networks.

-----
## Root access in the Terminal
```
sudo -s
```


-----
## Changing the Linux password

```console
[root@blikvm ~]# rw
[root@blikvm ~]# passwd root
[root@blikvm ~]# ro
```


-----
## Changing the KVM password

This password is used, among the Web UI login (if enabled)
and other functions that do not concern the OS shell.
You can change your account password through the user management interface on the web.
The default account password file is saved in `/mnt/exec/release/config/user.json`


-----
## Two-factor authentication

The 2FA a new method of strengthening the protection of BliKVM, available since `version >= v1.5.3`.
It is strongly recommended to enable it if you expose the BliKVM in the big and scary Internet.

!!! warning
    Please note that 2FA does not concern the Linux OS access for the `root` user, so take care of a strong password
    for it for SSH access (or setup the [key access](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server)).

??? example "Enabling 2FA on BliKVM"
    2FA can be enabled and disabled in the UI management interface of the web.

All Web UI users will be required to enter a one-time password on login.
In other words, **the secret is the same for all users**.

----
## Whitelist Mode

By default, all IPs can access the system. When the whitelist mode is enabled, only the specified IPs in the list can access. The list format is: `["xxx.xxx.xxx.xxx","xxx.xxx.xxx.xxx"]`.

Edit the configuration file to enable this feature: `vim /mnt/exec/release/config/app.json`
```
    "ipWhite": {
      "enable": false,
      "list": []
    }
```

----
## Session expiration

developing.



----
## Disabling authentication

If necessary, you can disable authentication for KVM access (Web UI. except SSH).

Modifying the `auth` field in `/mnt/exec/release/config/app.json` to `false`. Please ensure that you are in a sufficiently secure environment before disabling login authentication.