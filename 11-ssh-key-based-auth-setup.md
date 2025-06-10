# **Setting Up SSH Key-Based Authentication**

A step-by-step guide to set up secure, passwordless SSH access using public key authentication.

---

### **Step 1: Generate SSH Key Pair**

Open a terminal on your local machine and run:

```bash
ssh-keygen -t rsa -b 2048
```
![keygen](https://github.com/user-attachments/assets/93d16dc3-2e30-4b49-9c9c-282526b4c959)


- This creates a 2048-bit RSA key pair.
- By default, keys are stored in `~/.ssh/id_rsa` (private) and `~/.ssh/id_rsa.pub` (public).

![Screenshot_2](https://github.com/user-attachments/assets/eaf20756-8bbf-4d7e-9ff5-5613940556b4)

### **Step 2: Copy Public Key to Remote Host**

Use `ssh-copy-id` to send your public key to the remote server:

```bash
ssh-copy-id username@hostname
```

- This appends your public key to `~/.ssh/authorized_keys` on the remote host.
- Replace `username` and `hostname` with your actual remote login details.

![passingkeys](https://github.com/user-attachments/assets/83dfdb1d-3c30-48d0-b658-2b30cd436903)

### **Step 3: Test SSH Connection**

Connect to your server to verify that public key authentication works:

```bash
ssh username@hostname
```

- If successful, you won't be prompted for a password.
- If a passphrase was set during key generation, you’ll be prompted for it.

![sshwithoutauthtest](https://github.com/user-attachments/assets/113edb22-2b61-4448-bb38-b211dc97380e)

### **Step 4: Optional – Create an SSH Config File**

Simplify repeated connections by creating or editing the SSH config file:

```bash
vim ~/.ssh/config
```

Add the following configuration (replace values as needed):

```
Host test-server
  HostName hostname_or_ip
  User username
  Port 5439
  IdentityFile ~/.ssh/key
```

- `myhost` is a custom alias for quick access.
- `IdentityFile` points to your private key path (e.g., `~/.ssh/id_rsa`).

![sshconfigfile](https://github.com/user-attachments/assets/b6e0e52c-383a-4504-bbdb-6be824762ead)

### **Step 5: Connect Using SSH Config Alias**

Now you can connect using the alias set in your config file:

```bash
ssh test-server
```

- No need to type full username, hostname, or port.
- Ideal for managing multiple servers easily.

![sshconfigtest](https://github.com/user-attachments/assets/453a0a99-5a0d-4a80-ad97-09569cbbc2bc)







