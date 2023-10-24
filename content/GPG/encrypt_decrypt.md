+++
title = "Encrypt/Decrypt Files"
weight = 5
chapter = true
+++

## Encrypt a file:
This will encrypt a file, the -r flag is the recipient of the file to use this locally you can provide your own username.

```
gpg -e -r "USER" example.txt 
```

## Decrypt a file:
This will decrypt the gpg file provided in the command once you have provided the passphrase.

```
gpg -d -o example.txt example.txt.gpg 
```

