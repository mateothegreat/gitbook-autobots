# Cisco

## Common Commands

```bash
> enable
# show config
# show running-config
# show interface status
```

### Configuring DHCP

```bash
ip dhcp pool pool1
   network 10.0.25.0 255.255.255.0
   domain-name some.domain.com
   dns-server 1.1.1.1
   default-router 10.0.25.1 
```

### Configuring Access Mode

```bash
interface GigabitEthernet0/1
   switchport access vlan 20
   switchport mode access

```

### Linking two Switches

```bash
interface GigabitEthernet0/27
   switchport access vlan 20
   switchport trunk encapsulation dot1q
   switchport mode access

```

