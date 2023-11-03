# Use Case 1 - Overview of the topology
This product is being developed for the use of _Metodyki Projektów Teleinformatycznych_ university course. 

> As a user I want to be able to configure the devices of the simulated network from the perspective of the campus map 

## Feature description

**Wymaganie dotyczące zestawienia ogólnej topologii sieci kampusowej stanowi podstawę do rozwoju produktu NetCamps.**

Powody dla których warto symulować kampusową sieć komputerową: 

1) Optymalizacja i Testowanie: Dzięki symulacji można testować różne scenariusze działania sieci, co pomaga znaleźć optymalne ustawienia sprzętu i konfiguracji, zanim rzeczywista sieć zostanie zbudowana. To minimalizuje ryzyko błędów i koszty związane z ewentualnymi poprawkami po wdrożeniu.

2) Prognostyka i Skalowalność: Symulacja pozwala na prognozowanie zachowania sieci w przyszłości w różnych scenariuszach, na przykład w przypadku wzrostu liczby użytkowników lub obciążenia ruchem sieciowym. 

3) Bezpieczeństwo: Symulacje pozwalają również na testowanie odporności sieci na różnego rodzaju ataki oraz analizę zachowania się systemu w przypadku awarii czy prób nieautoryzowanego dostępu. 

## Feature demo
![Cisco Packet Tracer 2023-11-03 20-24-37](https://github.com/janek1842/NetCamps/assets/56030577/f2437169-ccf8-4b02-a979-64be87e62cb1)


## Device configuration

### R1
```
Router>en
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname R1
R1(config)#interface
R1(config)#interface giga
R1(config)#interface gigabitEthernet 0/0/1
R1(config-if)#ip add
R1(config-if)#ip address 192.168.0.1 255.255.255.0
R1(config-if)#
```

### R2
```
Router>en
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname R1
R1(config)#interface
R1(config)#interface giga
R1(config)#interface gigabitEthernet 0/0/1
R1(config-if)#ip add
R1(config-if)#ip address 192.168.0.1 255.255.255.0
R1(config-if)#
```



