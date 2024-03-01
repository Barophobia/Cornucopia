+++
title = "Updating Oracle Linux"
weight = 5
chapter = true
pre = "<b> - </b>"
+++

## Check your current Oracle Linux Version:

```
cat /etc/oracle-release
```

The output of this command will be the version of your machine.

## With internet:
With internet updating and upgrading oracle linux is as simple as using the following command

```
sudo yum update -y && sudo yum upgrade -y
```

This will check you have the latest update information.
The upgrade command will actually upgrade the software on your machine.

## Without internet:
To complete an offline upgrade of an oracle linux system there is a requirement that you have the oracle ISO file that is a higher version.

- Mount the ISO to a mount point (I am using /mnt/iso)

```
mkdir /mnt/iso
mount -o ro ORACLE_ISO.iso /mnt/iso
```

- Disable the Online repository

```
sudo vi /etc/yum.repos.d/public.repo
```
Inside this file there will be a list of repos, change the enable variable to 0 (enable=0)


- Create a local repo

```
sudo vi local.repo
```

Inside the new file write this:

```
[localRepo]
name=localRepo
baseurl=file:///mnt/iso/
gpgcheck=0
enabled=1
```

Now save and exit the file.

-  Clean the yum package manager cache

```
sudo yum clean all
```

- Check the local repo is enable and being used

```
sudo yum repolist all
```

In the output you should see the localRepo and it should be enabled.

- Now update the system

```
sudo yum update -y --skip-broken
```

- Restart the system to ensure the updates are installed as expected.

```
sudo reboot
```
or

```
systemctl reboot
```

### After offline update clean up

- unmount the ISO 

```
umount /mnt/iso
```

- clean the yum cache

```
yum clean all
```

- Remove the ISO 

```
rm ORACLE_ISO
```

After completing these steps you could go further and remove the local repo but I wouldn't recommend it as you can use the same repo in the future to make upgrades a bit smoother as long as you mount in the same directory.