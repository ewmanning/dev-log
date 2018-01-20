# Docker 

## Docker container restart policy
docker update --restart=always <container>

## Issue #01
NO ROUTE TO HOST network request from container to host-ip:port published from other container.

**Response:** 

This is a “known” bug. Everyone can access in this port, except for container in the same host. You have to allow it with firewall (yes this is a firewall/docker issue).

**Resolution:**

Issue is bigger than expected - Full issue is explained here: https://github.com/moby/moby/issues/16137#issuecomment-271615192
```
nmcli connection modify docker0 connection.zone trusted
systemctl stop NetworkManager.service
firewall-cmd --permanent --zone=trusted --change-interface=docker0
systemctl start NetworkManager.service
nmcli connection modify docker0 connection.zone trusted
systemctl restart docker.service
```


