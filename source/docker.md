### Docker 

Docker container restart policy:

docker update --restart=always <container>

## Issue #01
NO ROUTE TO HOST network request from container to host-ip:port published from other container.

**Response:** 

This is a “known” bug. Everyone can access in this port, except for container in the same host. You have to allow it with firewall (yes this is a firewall/docker issue).

**Resolution:**

```
firewall-cmd --permanent --zone=trusted --change-interface=docker0
firewall-cmd --permanent --zone=trusted --add-port=4243/tcp
firewall-cmd --reload
```
