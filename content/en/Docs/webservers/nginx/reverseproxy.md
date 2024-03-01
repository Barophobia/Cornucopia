+++
title = "Creating a reverse proxy"
weight = 5
chapter = true
pre = "<b> - </b>"
+++

In this example I will be making a reverse proxy for a calibre server so anywhere it references that service is a variable of whatever service you are setting up.

- Create a new file inside /etc/nginx/sites-available/calibre

- Now edit the file and add the following

```
server {
    listen 80;
    client_max_body_size 64M; # To upload large books (Change where required)
    server_name calibre.example.com ;

    location / {
        proxy_pass http://127.0.0.1:8080;
    }
}
```

You can now navigate to the server_name address you set and it will work as expected.

It is recommended to issue a cert and use HTTPS this can be done with certbot.