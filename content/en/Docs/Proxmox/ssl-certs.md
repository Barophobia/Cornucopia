+++
title = "SSL Certification Process"
chapter = true
+++

By default each Proxmox host creates its own self-signed Certificate Authority (CA) which then generates and signs the hosts certificates. These certificates are used for encrypted communication with the cluster pveproxy service and the shell/console feature.

## Using local CA certificates

Signed certifcates and keys can be uploaded through the Proxmox Web GUI by selecting the host, dropping down the system settings, clicking certificates and then clicking upload Custom Certificate. Using this option requries the full chain if you use a CA with an intermediary certification process.

## nginx Certificates

If you are using nginx to redirect to another port from the default (8006) for example redirecting to port 443 from port 8006, you will need to update the configuration with the new certificate and key as well as restarting the process.

edit the config in the location below:
```
/etc/nginx/conf.d/proxmox.conf
```

inside the config will be the ssl_certificate and ssl_certificate_key entries edit them to the following:
```
ssl_certificate /etc/pve/local/pveproxy-ssl.pem;
ssl_certificate_key /etc/pve/local/pveproxy-ssl.key;
```

save the config file and restart the nginx process using the following command:
```
systemctl restart nginx
```

This will disconnect any shell or consoles that are currently open and the connections will need to be re-established once the service is back.

## Reverting to self-signed certificates

In some circumstances the pveproxy service may not be able to restart and you will no longer have GUI access, to fix this SSH into the host and run the following command:
```
cd /etc/pve/local ; rm pve*ssl.* ; pvecm updatecerts --force ; service pveproxy restart
```

Once this command has been run you should be able to access the Web GUI again.