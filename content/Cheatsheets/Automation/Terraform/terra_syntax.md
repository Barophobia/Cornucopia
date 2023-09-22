---
title: "Terraform Cheatsheet"
date: 2023-09-06
author: "Barophobia"
tags: ["terraform", "introduction"]
categories: ["language", "programming"]
description: "Introduction to Terraform syntax and advantages."
keywords: "terraform"
draft: false
include_toc: true
---

# Terraform

```
terraform plan          # dry run
terraform apply         # apply configuration changes
terraform refresh       # synchronise state with the resource
terraform destroy       # destroy current configuration
```

### State management

```
terraform state list # this will show the resources in the state file
terraform state rm <RESOURCE> # remove a resource from the state list
```
### Correcting formatting

```
terraform fmt #reformats .tf files for better readability
```

### Remote Exec

This is used for remotely executing a command.

```
provisioner "remote-exec" {
    inline = [
         "apt install neofetch"
    ]
}
```

