# CentOS 7 System Preparation

## License

For each machine that will run Momentum send an email with the out put of the following command to `licensing@messagesystems.com`.

`ifconfig |grep -i "ether " |head -1`


## System Up to Date

Make sure all the systems that will run Momentum is up to date and running ntpd.

```
yum -y install groupinstall base sysstat ntp gdb lsof.x86_64 wget yum-utils vim cyrus-sasl-devel
yum update -y
chkconfig ntpd on
```



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

For a MTA with at least 64G RAM use the following settings. Tune the memory settings up or down depending on how much memory the MTA has
```
fs.file-max = 250000
kernel.shmmax = 68719476736
kernel.shmmni = 4096
net.core.netdev_max_backlog = 262144
net.core.optmem_max = 16777216
net.core.rmem_default = 67108864
net.core.rmem_max = 67108864
net.core.somaxconn = 8192
net.core.wmem_default = 67108864
net.core.wmem_max = 67108864
net.ipv4.ip_local_port_range = 5000 63000
net.ipv4.tcp_max_syn_backlog = 65535
net.ipv4.tcp_mem = 2885568 3847424 67108864
net.ipv4.tcp_rmem = 4096 87380 67108864
net.ipv4.tcp_wmem = 4096 65536 67108864
net.ipv4.tcp_tw_reuse = 1
net.ipv4.udp_mem = 2885568 3847424 67108864
net.ipv4.udp_rmem_min = 4096
net.ipv4.udp_wmem_min = 4096
vm.max_map_count = 768000

```

Load setting after change `/sbin/sysctl -p /etc/sysctl.conf`.

