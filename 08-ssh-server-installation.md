# SSH Server

Through SSH (Secure Shell) we can access or login into remote systems in a secure manner over the network. When an SSH server runs on a system it waits for incoming connection requests while performing SSH authentication for remote users.

> SSH communication is done through encrypted channel. So, it is safer than other protocols like telnet which uses the plain text communication method.

![SSHarchitecture](https://github.com/user-attachments/assets/bb7ef682-a228-4539-80cc-de9ec00cf435)

# SSH Installation

### 1. **Updating the system packages**

```bash
sudo apt update -y
```

### 2. **Install OpenSSH Server**

```bash
sudo apt install openssh-server -y
```

### 3. **Check SSH service status**

```bash
sudo systemctl status ssh
```

### 4. **Start & Enable SSH**

```bash
sudo systemctl start ssh
sudo systemctl enable ssh
```
![Screenshot 2025-04-11 221127](https://github.com/user-attachments/assets/80e8551a-d58d-4df3-9e7b-9c27b5655597)

It will look something like this after properly going through all the steps.

