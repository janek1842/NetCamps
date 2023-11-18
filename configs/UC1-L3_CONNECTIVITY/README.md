### Layer 3 (OSI/ISO) connectivity between campus network end-devices 

Layer 3 connectivty is a common requirement from the potential customers of network design and configuration solution providers, the demand can be defined as follows:

> As a user, I want to be able to communicate with another campus network device directly after connecting to the internal network 

For this reason, the network has been configured with the OSPF protocol. Open Shortest Path First (OSPF) is a routing protocol used in computer networks to help routers dynamically exchange information about network topology. It is an interior gateway protocol (IGP) designed to efficiently determine the best path for routing packets within an autonomous system, typically a single organization's network. OSPF uses a link-state routing algorithm, where routers exchange information about the state of their links with neighboring routers, allowing each router to build a detailed and up-to-date map of the network. 

What's more, NetCamps product also predicted the neccesity of introducing DHCP server that provides connected end-devices with the IP address, and allows them to communicate directly with each other right after connecting PC to the internal network. Dynamic Host Configuration Protocol (DHCP) is a network management protocol used to automatically assign and configure IP addresses to devices within a network. It eliminates the need for manual IP address assignment, making it more efficient to manage a large number of devices on a network.

Configuration has been done in **L3_CONN.pkt** file. 

### Demo

Below GIF presents the short overview of the possible configuration and contains following steps:

- Connecting new device to the switch **SB2** in BETA dormitory
- Requesting DHCP access by newly connected Laptop and PC12 from GAMMA dormitory
- Testing connectivity between selected devices

![20231118162627](https://github.com/janek1842/NetCamps/assets/56030577/65d5274b-e7da-447d-8235-905759148067)


### Config

Below configuration presents the key steps of fulfilling L3 Connectivity requirement for the given network 

#### OSPF Routing
OSPF networks configuration
```
 router ospf 1
  log-adjacency-changes
  network 192.168.0.0 0.0.0.15 area 0
  network 192.168.0.16 0.0.0.15 area 0
  network 10.10.10.16 0.0.0.3 area 0
  network 10.10.10.12 0.0.0.3 area 0
  network 10.10.10.0 0.0.0.3 area 0
```

#### DHCP
DHCP packet forwarding to central server
```
interface GigabitEthernet0/2
  ip address 192.168.0.17 255.255.255.240 ip helper-address 10.10.10.25 
```

