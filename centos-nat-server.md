# CentOS NAT Server

### Enable IP Forwarding

```bash
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.d/ip_forward.conf
sysctl -w net.ipv4.ip_forward=1
```

### Enable NAT

```bash
firewall-cmd --permanent --direct --passthrough ipv4 -t nat -I POSTROUTING -o eth0 -j MASQUERADE -s 10.0.0.0/24
firewall-cmd --add-masquerade --permanent 
firewall-cmd --reload
```



