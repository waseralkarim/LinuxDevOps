# Changing the IP address to Static IP

It is highly recommended to use static ip address on our server. Because the domain which we will set it’ll be based on that ip address. So, for some reason if we have to restart the server. It’ll get a new ip from the DHCP and then there will be a miss match with the domain ip. 

To check if our server is getting ip from DHCP pool and if we want to change ip address to static we can edit a YAML file located at /etc/netplan/

```bash
cat /etc/netplan/<YAML FILE NAME>
```

It’ll show something like this below:

```bash
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: true
```

We can edit this file in order to disable the DHCP and add a new static ip address by using this command:

```bash
cat /etc/netplan/<YAML FILE NAME>
```

After that the vim editor will open and based on our configurations we set edit the netplan YAML file:

```bash
sudo vim /etc/netplan/<YAML FILE NAME>
```

```bash
network:
  version: 2
  renderer: networkd
  ethernets: 
    <interface_name>: # ens33
      dhcp4: no
      addresses:
        - <your_static_ip>/<subnet_prefix> # 192.168.10.245/24 as example
      routes:
        - to: default
          via: <your_gateway_ip> # 192.168.10.1
      nameservers:
          addresses: [<dns1>, <dns2>] #[8.8.8.8, 8.8.4.4]
```

To apply the changes use this command after configuration.

```bash
sudo netplan apply
```

| Key | Meaning |
| --- | --- |
| `version: 2` | Netplan config version (always 2) |
| `renderer` | Backend to apply settings (`networkd` or `NetworkManager`) |
| `ethernets` | Block for wired interfaces |
| `enp0s3` | Actual interface name (`ip a` to check yours) |
| `dhcp4: no` | Disable DHCP (use static IP) |
| `addresses` | Static IP in CIDR format (e.g., `192.168.1.50/24`) |
| `routes` | Set default gateway route |
| `nameservers` | DNS servers (e.g., Google, Cloudflare) |

![Screenshot 2025-04-09 165739](https://github.com/user-attachments/assets/3e736912-ac24-4573-afa3-bd09563b21d8)

After applying the new ip address we have to reconnect with the new static ip address which we’ve set. 
