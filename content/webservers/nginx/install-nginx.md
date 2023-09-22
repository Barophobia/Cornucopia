+++
title = "Installing Nginx"
weight = 5
chapter = true
pre = "<b> - </b>"
+++

# Installing Nginx

## Installing nginx on Linux

Ubuntu:

```
apt install nginx
```

You may need to adjust UFW rules to allow access to the webserver.


## Checking if your webserver is running

```
systemctl status nginx
```

## Managing the nginx process

To stop nginx:
```
systemctl stop nginx
```

To start nginx:
```
systemctl start nginx
```

To restart nginx:
```
systemctl restart nginx
```

If you only make configuration changes you can reload without dropping connections:
```
systemctl reload nginx
``` 

