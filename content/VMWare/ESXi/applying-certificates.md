+++
title = "Applying Certificates"
chapter = true
+++

## Applying certificates to ESXi Hosts through the web UI
- Log in with root.
- Go to Manage > Security & Users > Certificates.
- Select Import new Certificate > Generate FQDN request.
- Copy and paste FQDN request into a text file and rename it with the .csr extension.
- Send file over to CA host so the CA can sign it.
    - Note: You can add the IP address of the ESXi host to the Subject Alternate Name to allow secure connections by specifying the FQDN (set to the CN) or the IP (set to the SAN).
- Send back signed cert in .pem format (Base64 ASCII encoded).
- Open the certificate file with a text editor.
- Back in ESXi under root privilege, go to Manage > Security & Users > Certificates.
- Select Import new Certificate.
- Copy and paste the .pem content into an empty box and select Import.

### Apply certificates to ESXi Hosts through the CLI

This assumes you have already generated a CSR and signed it using a CA. If you haven't use the guide here - [Generating a CSR for ESXi]({{< ref "gencsr" >}})

- SSH to the host.
- Change directory /etc/vmware/ssl
  ```
  cd /etc/vmware/ssl

  ```
- Open rui.key in vi and paste the key you used to create your CSR, then save and quit using :wq
- Open rui.cer in vi and paste the signed certificate contents into the box. (Make sure the certificate is in Base64)
- Once complete reboot the host and navigate to the webpage to see if the certificate was succesfully imported.
- Delete the /csrstore, made if you used my guide to create the CSR.