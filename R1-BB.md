```
hostname R1
!
interface Loopback0
 ip address 1.1.1.1 255.255.255.255
!
interface GigabitEthernet0/0  # Til R5
 ip address 10.0.5.1 255.255.255.0
 no shutdown
!
interface GigabitEthernet0/1  # Til R4
 ip address 10.0.2.1 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 1.1.1.1
 network 10.0.5.0 0.0.0.255 area 0
 network 10.0.2.0 0.0.0.255 area 0
 network 1.1.1.1 0.0.0.0 area 0
!
router bgp 65000
 bgp router-id 1.1.1.1
 neighbor 4.4.4.4 remote-as 65000
 neighbor 4.4.4.4 update-source Loopback0
 neighbor 5.5.5.5 remote-as 65000
 neighbor 5.5.5.5 update-source Loopback0
 network 1.1.1.1 mask 255.255.255.255
!
end
write memory
```
