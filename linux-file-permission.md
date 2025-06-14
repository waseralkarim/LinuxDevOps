# Linux File Permissions

# Creating User

```bash
# user creation
adduser <username>
# check users
cat /etc/passwd
# swithing user
su - <user_name>

```

Example:

```bash
su - dev
cd /tmp
vim helloworld.sh

```helloword.sh
#!/bin/bash
echo "Hello world"

```

su - qe
cd /tmp
ls -lrt
cat helloworld.sh
```

# User Permissions

```bash
r = read
w = write
x = execute

example:

d-rwx-rwx-rwx
here,
d = directory
1st rwx for user
2nd rwx for group
3nd rwx for others
```

```bash
chmod u=rwx <file_name>
```

## Numbering System

```bash
r = 4
w = 2
x = 1

ex: Add read and write permission to a file to all groups
chmod 666 <file_name>
```

# Changing Ownership

```bash
chown qe:qe <file_name> # Here first qe refers owner and 2nd one refers group that file belongs to
```
