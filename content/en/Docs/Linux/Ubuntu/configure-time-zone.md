+++
title = "Configure time zone"
chapter = true
+++

### Check the current time zone
```
date
```

### Configuring the time zone used
To configure the timezone in ubuntu, timedatectl is used.

Find the time zone from the list using the command below
```
timedatectl list-timezones
```

Once you have the time zone name for the time zone required use the command below to set it, change America/Goose_Bay to your desired timezone.
```
sudo timedatectl set-timezone America/Goose_Bay
```

Now use the command listed in the first section again to check your new setting.