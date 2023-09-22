+++
title = "Setup Headless Raspberry Pi"
+++

# Setup a headless Raspberry Pi

**Requirements**
- Raspberry Pi with power supply 
- SD Card

## Imaging the SD Card:

Download Raspbian lite (this has no DE, if you want a DE download the full iso image not lite)
[Raspbian Downloads](http://www.raspberrypi.org/downloads)

Use an application like [EthcherBalena](https://www.balena.io/etcher/) to write to the SD Card.

## Steps to take once the image is written to the SD Card:
Once the image is written to the SD Card open a terminal and browse to the the SD Card (Usually /Volumes/boot/).

If you want to enable SSH then make a file called 'ssh' make sure the file has no extensions if you are doing this on windows.

**Enable SSH:**
Linux or mac:
```
touch ssh
```
Windows:
```
New-Item ssh
```

Now add create a file called wpa_supplicant.conf and add the config below changing the network information to your own.

```
network={
    ssid="ssid_name"
    psk="password"
}
```

Once these steps are completed, plug the SD Card in and boot the Raspberry Pi.

Now there are two options to accessing the device:

```
ssh pi@raspberry.local
```

or

Find the IP on your router or use nmap to find the IP then:

```
ssh pi@<IPADDRESS>
```

The default password is **raspberry**.

You should now have access to your device without having to plug in a monitor.
