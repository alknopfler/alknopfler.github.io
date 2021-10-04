---
title: "Firewalld connecting 2 libvirt network"
date: "2021-10-04"
categories: 
  - "firewalld"
  - "libvirtd"
  - "networking"
tags: 
  - "firewalld"
  - "connection"
  - "libvirtd"
  - "networking"
---

# Situation
You have hypervisor with libvirtd and you want to connect 2 libvirt networks.
Also, you're gonna deploy vm and you need to install some software from internet. So the requirements are:

- Connection between network
- Connection through firewall to reach internet

# Scenario

Two networks are created:
```bash
$ kcli list network
Listing Networks...
+----------+--------+------------------+------+----------+------+
| Network  |  Type  |       Cidr       | Dhcp |  Domain  | Mode |
+----------+--------+------------------+------+----------+------+
| bare-net | routed | 192.168.150.0/24 | True | bare-net | nat  |
| default  | routed | 192.168.122.0/24 | True | default  | nat  |
+----------+--------+------------------+------+----------+------+
```

By default if you have firewalld active, the libvirtd rules will be active so you cannot connect both networks but the vm in each network will be able to connect to internet. So we have isolated networks.

- First try is stop firewalld:
  ```
  systemctl stop firewalld
  ```

The problem now is that we have access to internet:
```bash
[centos@test-ci-installer ~]$ ping www.google.es
PING www.google.es (172.253.122.94) 56(84) bytes of data.
64 bytes from bh-in-f94.1e100.net (172.253.122.94): icmp_seq=1 ttl=51 time=29.7 ms
64 bytes from bh-in-f94.1e100.net (172.253.122.94): icmp_seq=2 ttl=51 time=29.8 ms
```
But unfourtunately, the firewall is blocking the connection between network, so I cannot reach the other VM in the other network.

# Solution

We need to configure the firewall to allow a pass-thorugh connection between their input and output brigdes. With that configuration, firewalld will allow a passthrough connection between libvirtd to have connectivity i/o in this interfaces, so the real thing is that we could connect to internet as well as the other networks:

```
firewall-cmd --permanent --direct --passthrough ipv4 -I FORWARD -i virbr0 -j ACCEPT
firewall-cmd --permanent --direct --passthrough ipv4 -I FORWARD -o virbr0 -j ACCEPT
firewall-cmd --permanent --direct --passthrough ipv4 -I FORWARD -i br0 -j ACCEPT
firewall-cmd --permanent --direct --passthrough ipv4 -I FORWARD -o br0 -j ACCEPT
systemctl restart firewalld
```

# Security guys...

Don't look this ;)


# Tools used in this document

- [kcli](https://kcli.readthedocs.io/en/latest/) is a very useful tool to manage libvirtd as well as other many things. 
  