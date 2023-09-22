+++
title = "Install KMS"
date = 2021-09-07
chapter = true
+++

### Installing KMS

These steps remain the same whether you are installing on Windows Server 2008 R2, 2012, 2012 R2, 2016, 2019 or 2022.

#### Pre-requisites

- Decide which server will host the KMS. It is recommended to utilise the latest server version you have access to, with the highest patch level.
- Administrator access to CMD

#### Installation process

Logon to the server and open an elevated command prompt (without the elevation you will not be able to complete the process)

change directory to the system32 folder:
```
cd C:\windows\system32
```

Install your product key:
```
cscript slmgr.vbs /ipk *PRODUCT_KEY*
```


```
cscript slmgr.vbs /ato
```

The KMS should now function as expected.

To validate that clients are being activated use:
```
cscript slmgr.vbs /dlv
```




