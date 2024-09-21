# SSH Config
Starting from version 1.4.7, the web interface supports direct access to the blikvm SSH terminal. The default username and password to access the terminal are blikvm/blikvm. If you have changed the password for this user, you will need to update the corresponding username and password in the app.json file.

```
sudo -s
vim /mnt/exec/release/config/app.json
# Locate the following configuration and update it with your new credentials.
"sshUser": "blikvm",
"sshPassword": "blikvm"

```