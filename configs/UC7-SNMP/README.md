## SNMP configuration

Simple Network Management Protocol (SNMP) is an Internet Standard protocol for collecting and organizing information about managed devices on IP networks. 

> As a user, I want to enable network administrator to manage posessed devices via the SNMP commands 

SNMP, which stands for Simple Network Management Protocol, is a widely used protocol for managing and monitoring network devices and systems. SNMP enables network administrators to monitor the performance, health, and configuration of network devices, such as routers, switches, servers, printers, and more. It is an integral part of network management systems and is designed to be simple and extensible.

## Demo

Below demo presents a list of steps that allow to test an exemplary SNMP confogiration
 - Checking a selected parameter of the network device (hostname value on **routerAlfa**)
 - Obtaining this value from Admin PC by the SNMP protocol
 - Setting new value **RAlfa** from SNMP client
 - Veryfying the succesfull effect on the managed device

![20231215234928](https://github.com/janek1842/NetCamps/assets/56030577/62ffec04-32c8-486d-946f-c2e296d9251a)

## Config

SNMP is configured using snmp-server command. 
Read-write SNMP community string is used to enable the network administrator to view and change device configuration. 
```
snmp-server community NETCAMPS RW
```

Access list was created on each router to allow SNMP traffic only from administrators device. 

```
ip access-list extended SNMP-ACCESS
permit udp host 192.168.2.2 host 10.10.10.1 eq snmp
deny udp any host 10.10.10.1 eq snmp
permit ip any any
```

Admin PC is allowed to perform GET and PUT operations. 

![snmp-admin](https://raw.githubusercontent.com/janek1842/NetCamps/main/configs/UC7-SNMP/snmp-admin.png)

Performing SNMP requests is forbidden for all other devices. 
![snmp-another](https://raw.githubusercontent.com/janek1842/NetCamps/main/configs/UC7-SNMP/snmp-another.png)

ACL matches, which correspond to performed requests, can be observed on a router. 
![snmp-acl](https://raw.githubusercontent.com/janek1842/NetCamps/main/configs/UC7-SNMP/snmp-acl.png)
