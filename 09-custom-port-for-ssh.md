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

## SSH Security Best Practices

| Best Practice | Why It's Important |
| --- | --- |
| 🔐 Change default port | Reduces risk of automated bot attacks |
| 👤 Disable root login | Prevents attackers from brute-forcing root |
| 🗝 Use key-based auth | Stronger than passwords and resistant to brute-force |
| 📛 Disable password auth | Prevents login if key is missing/stolen |
| 🛑 Limit user access | Only allow specific users or groups |
| 🚪 Use firewall | Controls who can connect to SSH |
| 🛡 Install fail2ban | Blocks IPs after repeated failed login attempts |
| 📋 Monitor logs | Check `/var/log/auth.log` or `/var/log/secure` for suspicious activity |

### SSHD Config Hardening

Edit `/etc/ssh/sshd_config` and ensure the following lines are set:

```bash
PermitRootLogin no
PasswordAuthentication no
AllowUsers yourusername
LoginGraceTime 30
MaxAuthTries 3
PermitEmptyPasswords no
X11Forwarding no
UseDNS no
```

