+++
title = "Troubleshooting vCenter"
chapter = true
+++

## vCenter booting to a login prompt
If vCenter is booting to a login prompt these are the steps you can take to troubleshoot and fix the issue:

### First method
- try to navigate to <IP_ADDRESS>:5480 in your web browser, from this page you should be able to remediate any issues, check health and running services.

### Second method
- Log into the vCenter using root and the password set when creating the appliance (Reset the root password using the GRUB reset method if required)
- type:
```
service-control --start --all
```
- Once the services have started you should be able to get to the web address, if this doesn't work go to the next method.

### Third Method
  
- In the vCenter shell enter:
```
systemctl --list-unit-files | grep masked
```
- If services are showing as masked then run this command to unmask them:
```
find /etc/systemd/system/ -lname '/dev/null' -exec rm {} \\;
```
- Now check all the services are unmasked and run:
```
service-control --start --all
```
