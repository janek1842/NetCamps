### VOIP

VoIP (Voice Over Internet Protocol) is a technology that allows you to make and receive phone calls over the internet. It is an important requirement for a dormitory, as it provides internal voice communication inside a building.

A telephony service was created on each router, allowing 30 phones in every building. 
```
telephony-service
max-ephones 30
max-dn 30
ip source-address 192.168.20.20 port 2000
```
2911 routers had to be replaced by 2811, as the former do not support telephony service in Packet Tracer. 

![phones](https://private-user-images.githubusercontent.com/26022570/287365612-ba95887b-d62c-4981-a07b-b4da52c1dea7.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDE0NTk5NzQsIm5iZiI6MTcwMTQ1OTY3NCwicGF0aCI6Ii8yNjAyMjU3MC8yODczNjU2MTItYmE5NTg4N2ItZDYyYy00OTgxLWEwN2ItYjRkYTUyYzFkZWE3LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFJV05KWUFYNENTVkVINTNBJTJGMjAyMzEyMDElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjMxMjAxVDE5NDExNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWJmOTJiMTAzOGNjNjIxODAyMGY3YjkxMzA4YWNhYmUyOGZiMWIzNDZjNzhmNjQxMGE5YTFkMDE1ZWE4ZGUyMzImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.n6l5cfUohq9fUA5pP9blQJBKxDJLwLDBKkK4POYj2-w)


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

![voip](https://private-user-images.githubusercontent.com/26022570/287365615-2e8a134d-91e9-43b8-8a59-b619af25833c.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDE0NTk5NzQsIm5iZiI6MTcwMTQ1OTY3NCwicGF0aCI6Ii8yNjAyMjU3MC8yODczNjU2MTUtMmU4YTEzNGQtOTFlOS00M2I4LThhNTktYjYxOWFmMjU4MzNjLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFJV05KWUFYNENTVkVINTNBJTJGMjAyMzEyMDElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjMxMjAxVDE5NDExNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPThiMjU4ODI3N2JiNmJmNzBhODgxNTk2NmE3MmVjODA5ZmMwNTc0NjE0OWU4NWE4Y2Y4ZWZhZTE0NTNiY2ViZjgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.ufDcIzKKLPkNCjZ1v9wsfmW2ttmTkdYCByU8RdX80Uo)