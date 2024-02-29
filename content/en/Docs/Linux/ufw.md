+++
title = "Uncomplicated Firewall (UFW)"
weight = 5
chapter = true
pre = "<b> - </b>"
+++

# UFW

## Installation:

Debian:

```
apt install ufw
```

## Check the status of UFW:

You can check the status of ufw by running:

```
ufw status
```

Without any changes it will most likely report back **'Status: Inactive'**

## Set up UFW to allow SSH or port 22:

Here we will set up UFW to allow port 22 (SSH) connections so that once the UFW is enabled you are still able to SSH into the machine.

- First lets deny all incoming connections by default.

```
ufw default deny incoming
```

- Now lets allow ssh or port 22 - there are 2 ways of doing this.

```
ufw allow in ssh
```

or

```
ufw allow in 22
```

- Once this is set we can enable the UFW.

```
ufw enable
```

## View all your rules:

```
ufw status verbose
```

## Delete a rule:

To delete a rule for example the SSH rule, run:

```
ufw delete allow in 'SSH'
```

Once the rule is deleted, reload UFW

```
ufw reload
```

## Disable UFW:

```
ufw disable
```