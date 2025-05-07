# What is Shell?

A shell is a command-line interface that allows users to interact with an operating system by executing commands.

Shell allows us to login into our local or remote servers or systems. Both graphical and text mode consoles are supported. 

Here are some of the popular tools for remote login and management in Linux:

1. MobaXterm
2. OpenSSH
3. PuTTY
4. Terminator
5. Cockpit
6. Ansible

### SSH into the shell

For these hands on sessions we are going to use the MobaXterm and default terminal as our remote login tool. After installing the Ubuntu Server on the VirtualBox we can SSH onto that server. So first of all, we have to check the ip address of the ubuntu server using this command:

Terminal:

Check the ip of the VM/Instance.

```bash
ip a
```

Run this command to establish the ssh remote login:

```bash
ssh <username>@<ip address>
# Use this command if the ssh key is required
ssh -i <.pem file location> <username>@<ip address> 
```

![sshonterminal](https://github.com/user-attachments/assets/66e7ac09-7515-41bd-93b6-29886aa0687c)


MobaXterm:

![ubuntuserver_ssh](https://github.com/user-attachments/assets/50cef9fd-8ad0-4ecd-b5c5-9fa1c291a5e7)

1. Click the session button
2. Then the SSH button
3. Input the ip address of the server
4. Press ok the open the ssh session
