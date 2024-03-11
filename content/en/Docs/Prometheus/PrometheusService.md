+++
title = "Prometheus as a service (systemd)"
weight = 5
chapter = true
pre = "<b> - </b>"
+++

Create a prometheus service file.

```
sudo vi /etc/systemd/system/prometheus.service
```

Copy the following content to the file. Change the ExecStart location if you want to start the application from elsewhere.

```
[Unit]
Description=Prometheus Server
Documentation=https://prometheus.io/docs/introduction/overview/
After=network-online.target

[Service]
User=root
Restart=on-failure

ExecStart=/home/root/prometheus/prometheus --config.file /home/root/prometheus/prometheus.yml

[Install]
WantedBy=multi-user.target
```

Step 3: Reload the systemd service to register the prometheus service and start the prometheus service.

```
sudo systemctl daemon-reload
sudo systemctl start prometheus
```

Check the prometheus service status using this command:

```
sudo systemctl status prometheus
```

The status should show the active state

If you want prometheus to start automatically use this command:

```
sudo systemctl enable prometheus
```

### Issues that could happen

When creating the service file ensure to use absolute paths otherwise the service will not function correctly.