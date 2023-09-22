+++
title = "Full Custom Certification"
chapter = true
+++

This document will detail how to change to custom certificate mode and then apply a custom certificate to vCenter and ESXi hosts. In some environments there may be the requirement to have all services certified by a trusted CA and not be able to have a subordinate CA (Hybrid Mode) this solution allows you to certify your hosts as required.

Before changing vCenter to custom certificate mode, the vCenter will try to apply its own certificates to the hosts it manages, changing to custom certificate mode stops this behaviour and allows the administrator to apply custom certificates to the host without them being overwritten when connected to a vCenter instance.

## Changing vCenter's certificate mode 
- Select your vCenter system in vSphere Client.
- Click Configure and under Settings, click Advanced Settings.
- Click Edit Settings.
- click the Filter icon in the name column and in the field enter: 
```
vpxd.certmgmt
```
- Change the value of vpxd.certmgmt.mode to custom.
- Restart the vCenter Server Service.

	
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
