
### R2
```
konfiguracja

ROUTING: router ospf 1 log-adjacency-changes network 192.168.0.0 0.0.0.15 area 0 network 192.168.0.16 0.0.0.15 area 0 network 10.10.10.16 0.0.0.3 area 0 network 10.10.10.12 0.0.0.3 area 0 network 10.10.10.0 0.0.0.3 area 0

DHCP: interface GigabitEthernet0/2 ip address 192.168.0.17 255.255.255.240 ip helper-address 10.10.10.25 -> forwarding pakietow do centralnego serwera DHCP
```



