## Secure Wi-Fi configuration

Wi-Fi, short for Wireless Fidelity, refers to a set of wireless networking technologies that allow devices to connect and communicate with each other without the need for physical cables. Wi-Fi technology is based on the IEEE 802.11 family of standards, which define the specifications for implementing wireless local area networking (WLAN) communication.

> As a user, I want every organization memmber to communicate with each other with Wi-Fi interface

> As a user, I want every organization memeber to have Wi-Fi security assured with Layer 2 techniques and WPA2 protocol  

In campus networks, Wi-Fi plays a crucial role in providing connectivity and flexibility for both students and faculty.

## Demo
In this demo, succesfull webpage access from the attached to the Wi-Fi network smartphone is presented 

![20231216124349](https://github.com/janek1842/NetCamps/assets/56030577/3922168a-09a3-454c-aaeb-b1c83f6c0c9a)

In the second part of the demo, security issues regarding configured networks are presented. Multiple wireless networks for every building with enabled WPA2 protocol based on AES encryption algorithm and configured password.  

![config_1](https://github.com/janek1842/NetCamps/assets/56030577/be19756e-5298-4b90-bf32-1fd3ceaf6eec)

https://github.com/janek1842/NetCamps/assets/56030577/5e84afe0-3eae-47e6-b0f3-4009b81c7730

## Config

the configuration included the placement of the ap and the configuration of the central controller for wlc management. 

### 1. topology configuration
in step one, we will attach and integrate wireless devices into our topology. To do this, we add each access point to our LAN, and for one selected wlc controller. We assign a wlc address and enter the address of the wlc controller into the dhcp server for each of our address pools, this way ap from all lan's will connect to the wlc and can be managed from it.
### 2. WLAN management
To manage from wlc we use the web GUI provided. We access the computer on our internal network and type in https://192.168.0.14, login= admin, password=Cisco123 in the browser bar. In the WLANs tab we add wlan for all dorm areas. We select the security type WPA2-Personal with PSK key. The password is name_area_12345 e.g. alfaf112345. Guest password is guest12345. Then create an ap group under WLAN->AP group. Create group alfaf1 for dormitory alfa 1 floor to which you assign the ap located there and wlan ssid alfaf1. In this way, the corresponding ap will broadcast the appropriate network for its location. Each ap simultaneously broadcasts the guest network.
### 3. end device connection
the final step is for the end user to connect to the network using the wifi name and password. The user turns on the 802.11 wireless module on the phone and enters the appropriate password in WPA2-Personal format. Connections are set up automatically. The user has access to internet resources and the dormitory website. He can also transfer files with other network users.
