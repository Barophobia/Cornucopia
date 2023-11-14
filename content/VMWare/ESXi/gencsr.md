+++
title = "Generating a CSR using CLI"
chapter = true
+++

In this guide I will be using the openssl pre-installed on the ESXi host to generate the CSR, if you have openSSL elsewhere you can use that, just make sure you take the rui.key file with the configuration.

- SSH to the ESXi host
- Create a directory called that will be used to temporarily house the config and key. (the /etc/vmware/ssl folder can reset itself back to default so it isn't recommended to store anything there). This directory can be removed once the certificate is imported.
```
mkdir /csrstore
```
- Change directory to the new folder
```
cd /csrstore
```
- create an openssl.cnf file and use the example below to fill it out. The fields that should be changed are - 
  
                      - subjectAltName
                      - CountryName
                      - stateOrProvinceName
                      - LocalityName
                      - 0.organizationName
                      - organizationalUnitName
                      - commonName
- Create the openssl.cnf file and open it in the vi text editor
```
vi openssl.cnf
```

*SAMPLE OPENSSL CONFIG*
```
[ req ]
default_bits = 2048
default_keyfile = rui.key
distinguished_name = req_distinguished_name
encrypt_key = no
prompt = no
string_mask = nombstr
req_extensions = v3_req

[ v3_req ]
basicConstraints = CA:FALSE
keyUsage = digitalSignature, keyEncipherment, dataEncipherment
extendedKeyUsage = serverAuth, clientAuth
subjectAltName = DNS:esxihost, IP:10.0.1.10, DNS:esxihost.vmware.com

[ req_distinguished_name ]
CountryName = US
stateOrProvinceName = StreetCorner
LocalityName = Alleyway
0.organizationName = CompanyX
organizationalUnitName = ITGuys
commonName = esxihost.vmware.com
```

- Generate a new rui.key to be used with your new certifate
```
openssl genrsa -out rui.key 2048
```

- Now generate the CSR based on your config and rui.key
```
openssl req -new -node -out rui.csr -key rui.key -config openssl.cnf
```

- Now take the CSR and sign it.

If you need to know how to import the signed certificate go here - [Applying to certificates to ESXi Hosts]({{< ref "applying-certificates" >}})