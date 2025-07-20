# Nginx Server Deploy

## Installation

```bash
sudo apt update -y
sudo apt install nginx -y
sudo systemctl restart nginx-service
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
```
<img width="1105" height="345" alt="image (4)" src="https://github.com/user-attachments/assets/f8564d7f-7047-4d1b-80ae-0811e348a765" />

We can access the default nginx page by hitting the ip address on our browser.

<img width="872" height="282" alt="nginxdefault" src="https://github.com/user-attachments/assets/1d0d4af2-84f8-4885-ab3b-47d414ecfe82" />

If firewall is activated, we can check the list and allow them:

```bash
sudo ufw app list
sudo ufw allow <service name> # Nginx Full allows both http(80) and https(403)
```

Access the nginx files:

```bash
cd /etc/nginx/
```

## Simulate DNS with /etc/hosts

Edit your hosts file:

### On Linux:

```bash
sudo vim /etc/hosts
```

Add:

```
<ip address> mypractice.local
```

### On Windows:

1. **Open the hosts file:**
    - Inside Notepad, click **File ➔ Open**.
    - Navigate to:
        
        ```
        C:\Windows\System32\drivers\etc\
        ```
        
    - In the file open window:
        - You won't see any files because it's showing only `.txt` files.
        - In the bottom right, change from "**Text Documents (.txt)**" ➔ "**All Files (*.*)**".
    - Then you will see a file named **hosts** — open it.
2. **Add your mapping at the bottom:**
Add this line:
    
    ```
    <ip address> mypractice.local
    ```
    
3. **Save the file.**
(Because you opened Notepad as Admin, it will let you save directly.)

<img width="861" height="224" alt="image (5)" src="https://github.com/user-attachments/assets/93ae6f6f-e319-4faf-a476-97f56fbd1146" />

Open a browser and visit:

```
http://mypractice.local
```

It should show your test page. This simulates DNS resolution locally.

### Nginx server configurations

```bash
# Default Server Configuration Format
server {
	
        # SSL configuration
        #listen 80;
        # listen [::]:443 ssl default_server;

        root /var/www/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.php;

        server_name mypractice.local;

	access_log /var/log/nginx/mypractice.local.access.log;
	error_log /var/log/nginx/mypractice.local.error.log;

        location / {
                #limit_conn concurrent 5;
                #limit_req zone=mylimit burst=5 nodelay;
                try_files $uri $uri/ /index.html?$args;
        }

        
	#Client Side Cashing Configuration
        location ~* \.(js|jpg|jpeg|gif|png|css|tgz|gz|rar|bz2|doc|pdf|ppt|tar|wav|bmp|rtf|swf|ico|flv|txt|woff|woff2|svg)$ {
        expires 90d;
        add_header Pragma public;
        add_header Cache-Control public;
        add_header Vary Accept-Encoding;
        }

        location @/ {
        rewrite ^/(.+)$ /index.html?_route_=$1 last;
        }

    	# Block a single IP address
    	#deny 103.120.35.2;

        location ~ /\.env {
                deny all;
        }

	location ~ /\. {
        deny all;
	}

}

```
<img width="1228" height="691" alt="image (6)" src="https://github.com/user-attachments/assets/82309a1e-3799-4c77-b0bc-91138fb284db" />

### Short link DNS

```bash
sudo ln -s /etc/nginx/sites-available/<dns name> /etc/nginx/sites-enabled/
```

Then reload:

```bash
sudo nginx -t
sudo nginx -s reload #soft reloads the nginx service (recommended)
sudo systemctl restart nginx.service #not recommended for production server
```
<img width="1245" height="313" alt="nginxconf2" src="https://github.com/user-attachments/assets/0db45912-1d10-48b6-b522-f146a5c56beb" />

### Now we need to configure the html file

It is located at: /var/www/html

We have our index.html and styles.css file on the local folder. Which contains a static website page. We transfer the files from our local host or we can create the files on the server.

### Transferring file using SCP

```bash
scp <file location> our-username@your-server-ip:/var/www/
```
<img width="1102" height="192" alt="scptransfer" src="https://github.com/user-attachments/assets/e4001698-61ee-4011-b398-c3a2d071aed2" />

Unzip the .tar file using this command:

```bash
tar -xvf <tarfile name>
```
<img width="1111" height="78" alt="untar" src="https://github.com/user-attachments/assets/aac7bf5f-c938-405c-86ba-730191075c47" />

Now remove the html file and rename the file (mypracticelocal) to html.

```bash
sudo rm -rf html/
sudo mv <moved file name>/ html
```
<img width="1096" height="155" alt="renamedhtml" src="https://github.com/user-attachments/assets/3a36b2bb-9066-49dc-a9f8-06d02d02c728" />

Now if we reload the browser, we will be able to see the new webpage.

<img width="1919" height="993" alt="newwebpage" src="https://github.com/user-attachments/assets/9b7b8708-02ba-4ffd-bcaf-774bf8c64a7a" />






