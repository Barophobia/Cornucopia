+++
title = "Disabling Cipher Suites"
chapter = true
+++

## Check active cipher suites using powershell

```
Get-TlsCipherSuite | format-table Name
```

This will give you a list of active cipher suites on the device.

## Disabling a cipher suite

For this example I will disable the 'TLS_RSA_WITH_3DES_EDE_CBC_SHA' cipher suite as this is classed as vulnerable to a SWEET32 attack.

```
Disable-TlsCipherSuite -Name "TLS_RSA_WITH_3DES_EDE_CBC_SHA"
```

The command will not give any terminal output but you can use the Get-TlsCipherSuite command to make sure it is deactivated.