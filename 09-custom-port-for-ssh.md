# Custom Port Setup for SSH

Important: In case something goes wrong it is best to backup the current configuration file of the SSH.

```bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config_backup
```

### **Edit SSH Configuration**

```bash
sudo vim /etc/ssh/sshd_config
```
![Image](https://github.com/user-attachments/assets/c85daaf5-ed1d-4905-9535-b7db831970d6)

Then we have to set our desired port number in the port section. For example, we’ve edited the port to 2222 from 22.

> Recommended range: **1024–65535** (to avoid system reserved ports)

```bash
sudo systemctl restart ssh.service
```

### **Allow New Port in Firewall**

```bash
sudo ufw allow 2222/tcp
```

### **Connect Using New Port**

```bash

ssh -p 2222 username@server_ip
```
![Image](https://github.com/user-attachments/assets/7637be81-f298-4b0a-805e-6cb1165f4fdc)

