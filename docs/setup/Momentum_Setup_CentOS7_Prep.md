# CentOS 7 System Preparation

## License

For each machine that will run Momentum send an email with the out put of the following command to `licensing@messagesystems.com`.

`ifconfig |grep -i "ether " |head -1`


## System Up to Date

Make sure all the systems that will run Momentum is up to date.

`yum update -y`


## Stop Conflicting Services

```
systemctl stop  postfix.service
systemctl disable postfix.service

systemctl stop  qpidd.service
systemctl disable qpidd.service
```

In `/etc/selinux/config` sure SELinux is set to `disabled`. Then run `/usr/sbin/setenforce 0`


## Important Systems Settings


Add the following to `/etc/sysctl.conf`. You may need to create the file if it does not exist.


```
vm.max_map_count = 768000
net.core.rmem_default = 32768
net.core.wmem_default = 32768
net.core.rmem_max = 262144
net.core.wmem_max = 262144
fs.file-max = 250000
net.ipv4.ip_local_port_range = 5000 63000
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_tw_recycle = 1
kernel.shmmax = 68719476736
net.core.somaxconn = 1024
vm.nr_hugepages = 10
kernel.shmmni = 4096
```

Load setting after change `/sbin/sysctl -p /etc/sysctl.conf`.

