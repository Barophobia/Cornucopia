+++
title = "Applying Certificates"
chapter = true
+++

## Applying certificates to ESXi Hosts
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
