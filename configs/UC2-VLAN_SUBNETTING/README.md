### Link Redundancy and VLAN subnetting configuration

Providing VLAN subnetting and link redundancy, might be a key part of client requirements for a better performance of campus network 

> As a user, I want to be able to communicate with another campus network device despite the fact of backbone link failure

> As a user, I want to secure selected switchports from communicating with devices by assigning them VLAN not supported on trunk link

Link redundancy is crucial in campus networks to ensure high availability, reliability, and fault tolerance. Campus networks typically connect various buildings, departments, and users within an organization's physical location. Redundant links help mitigate the impact of link failures, improving the overall performance and resilience of the network. 

When it comes to assigning VLAN to the unused one, this security measure helps mitigate potential VLAN hopping attacks where an unauthorized user attempts to gain access to traffic in a VLAN other than their own. By assigning switch ports to the top unused VLAN, you create an isolated VLAN that is not in active use, reducing the risk of unauthorized access and potential security breaches.

Because of that, given scenario presents two relevant simulations of securing the switch port by assigning it to and unused VLAN and link redundancy scenario

Configuration has been done in **VLAN_SUBN.pkt** file. 

### Demo

Below GIF presents the short overview of the possible configuration for securing port with the VLAN and contains following steps:

- Connecting new laptop to the switch **SA1** in ALFA dormitory to the port with unused VLAN assigned (secured port **FA 0/24**)
- Connecting new laptop to the switch **SA1** in ALFA dormitory to the port with known VLAN assigned (trusted port **FA 0/22**)
- Testing successfull DHCP request on trusted port and unsuccessfull request on secured port

![20231118170952](https://github.com/janek1842/NetCamps/assets/56030577/4ef0cc98-01d5-4f3e-9fd5-b33ee62e7dca)

Below GIF presents the short overview of the possible configuration for link redundancy and contains following steps:

- Ping connectiong with **-t ** option enabled from PC in alfa dormitory to PC in Gamma dormitory
- Deleting fiber links in core part of the network, which simulates link failure scenario
- Observing constant connectivity (only two pings lost) between devices due to the link redundancy

![20231118172207](https://github.com/janek1842/NetCamps/assets/56030577/a76ad334-8cd7-437f-94dc-de2352e29f21)


### Config

Below configuration presents the key steps of fulfilling Link Redundancy and VLAN subnetting configuration

#### VLAN Configuration
VLAN networks configuration (on every switch with varying **X** in number of VLAN)
```
name vlanX
 int range fa0/1-24
 switchport mode access vlan X
```
When it comes to trunk link configuration between switch and router, the configuration should be made as follows:
```
Switchport mode trunk
Switchport mode trunk native vlan X
Switchport mode trunk allowed vlan 1,10,20,30,40,50,60 (as an example)
```
