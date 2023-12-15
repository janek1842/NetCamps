### HTTP Web Page for dormitory 

Providing an internally hosted webpage can be a very common customer requirement, not only for dormitory residents but also for every kind of orgnization that want to enhance the sense of community by providing a space for its members to connect. 

> As a user, I want every orgzanition member to use an internally hosted web page for inter-organization communication  

An internal webpage serves as a centralized platform where students can access essential resources such as event schedules, facility updates, and important announcements. It facilitates seamless communication between residents and dormitory management, ensuring that everyone is well-informed about policies, regulations, and upcoming activities. Additionally, the internal webpage can enhance the sense of community by providing a space for students to connect, share information, and collaborate on various initiatives, ultimately contributing to a more vibrant and connected living environment within the dormitory. That's why a given scenario 

Configuration has been done in **dorm_HTTP.pkt** file. 

### Demo

Below GIF presents the short overview of the possible configuration for providing HTTP Web Page for dormitory:

- Checking HTTP service is enabled at the configured server
- Selecting a randomly chosen PC from the campus network
- Successful webpage access for the selected device

![20231202151345](https://github.com/janek1842/NetCamps/assets/56030577/de15fa3b-ca13-4a6f-9004-c36c4ee7630c)

### Config

Below configuration presents the key steps of fulfilling Web Page for Dormitory requirement

Configuration can be divided into 3 subparts.
1. setting up a http server
2. setting up a dns server
3. configuring DHCP server 

### setting up a http server
for this part we deploy a server device in our centralised server area and add it to our internal network. This server will be acting as http serwer.
Then we go into Services tab and select HTTP. Here we edit index.html file which describes the interior display of our web page. Now we have our server side application which hosts our web page.
### setting up a dns server
Now we need to map our static ip address to our domain name, so we can use mnemonics url's instead of binary digits. We deploy another server just as described in subpart 1. Then we go into ###Services and DNS. 
We set service on and add coresponding domain name for our ip address. In our case it name is www.akademik.pl and Address is 10.10.10.30.
### configuring DHCP server 
Now we want our end device users to type our domain name in their browser address and be forwarded just into our http server. In order to achieve that we need to set our internal dns in our dhcp   server pools. We open our dhcp server setting by left-clicking on it and go into services, DHCP. here we edit pools for every dorm and every user in our network so that their assigned dns match      with our internal dns.

      Now every user should have access to our internal web page from his browser under the www.akademik.pl url.
