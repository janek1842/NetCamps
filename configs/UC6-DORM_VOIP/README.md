### Dormitory VOIP service configuration

VoIP (Voice Over Internet Protocol) is a technology that allows you to make and receive phone calls over the internet. It is an important requirement for a dormitory, as it provides internal voice communication inside a building. It can server also for other organizations for an alternative method of communication especially useful in emergency situations.

> As a user, I want every dormitory member to use an VOIP communication over devices present in the network

Voice over Internet Protocol (VoIP) is a technology that enables the transmission of voice and multimedia content over the internet, replacing traditional telephone networks. VoIP converts analog voice signals into digital data packets, allowing for efficient and cost-effective communication. It leverages the internet infrastructure to facilitate voice calls, video conferencing, and other multimedia services, offering businesses and individuals a more flexible and scalable communication solution. VoIP has become increasingly popular for its affordability, versatility, and the ability to integrate various communication channels seamlessly.

### Demo

Below GIF presents the short overview of the possible configuration for providing VOIP for dormitory:

- Selecting two random VOIP phones from the dormitory network
- Presenting succesfull call from one device to another

![20231202141411 (1)](https://github.com/janek1842/NetCamps/assets/56030577/05a8b901-3c60-4c2e-aae6-0ae4290e8621)

### Config

Configuration has been done in VOIP.pkt file.

A telephony service was created on each router, allowing 30 phones in every building. 
```
telephony-service
max-ephones 30
max-dn 30
ip source-address 192.168.20.20 port 2000
```
2911 routers had to be replaced by 2811, as the former do not support telephony service in Packet Tracer. 

Each phone was assigned a number, type and button. 
```
ephone-dn 1
number 1001
ephone 1
type 7960
button 1:1
```

Subinterface was created on router for voice vlan. 

```
interface FastEthernet0/0.20
encapsulation dot1Q 20

```

Ports on the switch to which phones are connected were assigned voice vlan 20. 
```
interface FastEthernet0/1
switchport mode access
switchport access vlan 10
switchport voice vlan 20
```
