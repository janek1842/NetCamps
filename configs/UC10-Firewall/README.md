### Firewall
Cisco ASA 5506-X is a firewall security appliance which provices services such as firewall, VPN (Virtual Private Network), intrusion prevention.  Its primary function is to act as a firewall, controlling and monitoring traffic between different network segments and protecting against unauthorized access. 

> As a user, I want to posses firewall in front of the servers, filtering selected traffic from accessing organizational services 

The presence of a firewall in a dormitory network is vital for safeguarding against various cyber threats, controlling access, ensuring privacy, and complying with security regulations. It is an essential component of a comprehensive network security strategy.

## Demo
Below demo presents a configuration that is described in Config section. It assumes an organizational webpage access attempt: 

- firewall forbiden access (unsuccessful) from PC-Alfa-0
- legal (successfull) access from PC-Alfa-1

![20240105181626](https://github.com/janek1842/NetCamps/assets/56030577/93bd4364-1927-43ff-8b7e-af45124fecfc)

### Config

Configuration is provided in Firewall.pkt file. 

First, an ASA device was added between the router and server part of the network. The interface which connects to HTTP server was configured as an inside interface, containing a name, an IP address and security level of 100. 
```
interface GigabitEthernet1/2
 nameif INSIDE2
 security-level 100
 ip address 10.10.10.29 255.255.255.252
```
The interface which connects to the dormitory was configured as the outside interace with the security level of 0. 
```
interface GigabitEthernet1/4
 nameif OUTSIDE
 security-level 0
 ip address 10.10.10.102 255.255.255.252
 ```
An extended ACL was created to prevent host 192.168.0.26 located in Alfa dormitory (PC-Alfa-0) from accessing the website. All other hosts are allowed. 
```
access-list HTTP_ACCESS extended deny tcp host 192.168.0.26 host 10.10.10.30 eq www
access-list HTTP_ACCESS extended permit tcp 192.168.0.16 255.255.255.240 host 10.10.10.30 eq www
```
The access list was assigned to the OUTSIDE interface in inbound direction. 
```
 access-group HTTP_ACCESS in interface OUTSIDE
```
Also, a default route was created to allow the server response get back to the user. 
```
route OUTSIDE 0.0.0.0 0.0.0.0 10.10.10.101 1
```
