# SSH Key Based Authentication

## Authentication Methods

SSH supports two primary authentication methods:

- **Public Key**
- **Password**

---

### **Public Key Authentication**

The SSH/SFTP authentication method known as public key authentication enables secure account login through the use of cryptographic key pairs instead of traditional passwords. The authentication system provides improved security measures that organizations and individuals use across different environments.

---

### **Here's how it works:**

1. **Key Generation**:
    
    Your local machine needs to create a key pair which includes both a public key and a private key. Your system securely stores the private key while the public key can be distributed for sharing purposes.
    
2. **Public Key Placement**:
    
    You must add your public key to the remote machine by inserting its content into the ~/.ssh/authorized_keys file.
    
3. **Authentication**:
    
    During connection the SSH client displays the public key to the server. The server verifies if the presented key exists within the `authorized_keys` file before sending an encrypted challenge. 
    
4. **Private Key Usage**:
    
    The challenge gets decrypted by your client through the use of its private key before your client responds. The server grants access when it successfully verifies the response through the public key.
    

---

### **Advantages of Public Key Authentication**

- **Enhanced Security**: The method provides better security because it eliminates both password sniffing and brute-force attack vulnerabilities.
- **Convenience**: An SSH agent enables easy logins through its convenience features.
- **Automation**: The system works best for running automated scripts together with tasks that need no human interaction.

### **Best Practices for Public Key Authentication**

**Protect Your Private Key**: Store it securely and use a strong passphrase.

**Rotate Keys Regularly**: Replace keys periodically to reduce the impact of potential leaks.

**Limit Access**: Only allow public keys from trusted users in the `authorized_keys` file.

![sshworkflow](https://github.com/user-attachments/assets/6c9ee2bb-3804-4324-8b20-e7313f24f504)

