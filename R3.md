```
hostname R3
!
interface Loopback0
 ip address 3.3.3.3 255.255.255.255
!
interface GigabitEthernet0/0  # Til R5
 ip address 10.0.6.3 255.255.255.0
 no shutdown
!
interface GigabitEthernet0/1  # Til R2
 ip address 10.0.7.3 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 3.3.3.3
 network 10.0.6.0 0.0.0.255 area 0
 network 10.0.7.0 0.0.0.255 area 0
 network 3.3.3.3 0.0.0.0 area 0
!
router bgp 65000
 bgp router-id 3.3.3.3
 neighbor 5.5.5.5 remote-as 65000
 neighbor 5.5.5.5 update-source Loopback0
 neighbor 2.2.2.2 remote-as 65000
 neighbor 2.2.2.2 update-source Loopback0
 network 3.3.3.3 mask 255.255.255.255
!
end
write memory

```

