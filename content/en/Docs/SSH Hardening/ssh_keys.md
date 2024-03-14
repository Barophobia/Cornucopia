+++
title = "SSH Keys (Passwordless Authentication)"
weight = 5
chapter = true
pre = "<b> - </b>"
+++

## Generate ed25519 SSH Key

```
ssh-keygen -t ed25519 
```

## Copy Public key to servers

```
ssh-copy-id USER@IPADDRESS
```

On connection the server will request the password to the user and then you will be able to SSH without the use of the password.