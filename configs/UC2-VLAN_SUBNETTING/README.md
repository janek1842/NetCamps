
```
Vlan -> vlan 10
name vlan10
int range fa0/1-24
switchport mode access vlan 10 
i tak na każdym switchu z odpowiednim numerem vlanu 
 
Spanning tree
spanning-tree mode Rapid-pvst

Trunki:
Na odpowiednim interfejsie łączącym router z switchem:
Switchport mode trunk 
Switchport mode trunk native vlan 10
Switchport mode trunk allowed vlan 1,10,20,30,40,50,60
```



