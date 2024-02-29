+++
title = "How to configure NXLog"
weight = 5
chapter = true
pre = "<b> - </b>"
+++

# How to configure NXLog

### Windows

- Edit the nxlog.conf file inside C:\Program Files (x86)\nxlog\conf

- At the bottom of the notepad will be some commented out lines that are similar to the lines below, remove the hashes so they arent commented out and make sure the output is correctly configured to the syslog server's IP using the correct Module (TCP/UDP) and Port.

- When you edit the nxlog.conf file make sure you restart the nxlog service.


```
# Modules section
<Input in>
    Module  im_msvistalog
</Input>

<Output out>
    Module  om_udp
    Host    IP_ADDRESS
    Port    514
    Exec    to_syslog_snare();
</Output>

# Route section
<Route 1>
    Path    in => out
</Route>
```


### Sending Logs as JSON

- Edit nxlog.conf and change the Extension and Output to look like the lines below

```
<Extension json>
    Module    xm_json
</Extension>

<Output out>
    Module    om_tcp
    Host      IP_ADDRESS
    Port      514
    Exec      to_json();
</Output>
```