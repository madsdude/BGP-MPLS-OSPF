
```
hostname R5
!
interface Loopback0
 ip address 5.5.5.5 255.255.255.255
!
interface GigabitEthernet0/0  # Til R1
 ip address 10.0.5.5 255.255.255.0
 no shutdown
!
interface GigabitEthernet0/1  # Til R3
 ip address 10.0.6.5 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 5.5.5.5
 network 10.0.5.0 0.0.0.255 area 0
 network 10.0.6.0 0.0.0.255 area 0
 network 5.5.5.5 0.0.0.0 area 0
!
router bgp 65000
 bgp router-id 5.5.5.5
 neighbor 1.1.1.1 remote-as 65000
 neighbor 1.1.1.1 update-source Loopback0
 neighbor 3.3.3.3 remote-as 65000
 neighbor 3.3.3.3 update-source Loopback0
 network 5.5.5.5 mask 255.255.255.255
!
end
write memory

```
