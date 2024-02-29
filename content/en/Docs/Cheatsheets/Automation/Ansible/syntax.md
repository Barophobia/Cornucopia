---
title: "Ansible Syntax"
date: 2023-09-05
author: "Barophobia"
tags: ["ansible", "syntax"]
categories: ["language", "programming", "automation"]
description: "Introduction to Ansible Syntax."
keywords: ""
draft: false
include_toc: true
---

# Ansible

### Playbooks

```
ansible-playbook <YAML> -i <HOSTSFILE>    # Run on all hosts from specified hosts file
ansible-playbook <YAML> -C                # Test run
ansible-playbook <YAML> -C -D             # Dry run
```


### Check Syntax

```
ansible-playbook --syntax-check <YAML>
```

### Execute commands on hosts

```
ansible <HOSTGROUP> -a <COMMAND>
```
Example:
```
ansible all -a "neofetch"
```
