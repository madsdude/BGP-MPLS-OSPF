```
hostname R2
!
interface Loopback0
 ip address 2.2.2.2 255.255.255.255
!
interface GigabitEthernet0/0  # Til R4
 ip address 10.0.8.2 255.255.255.0
 no shutdown
!
interface GigabitEthernet0/1  # Til R3
 ip address 10.0.7.2 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 2.2.2.2
 network 10.0.8.0 0.0.0.255 area 0
 network 10.0.7.0 0.0.0.255 area 0
 network 2.2.2.2 0.0.0.0 area 0
!
router bgp 65000
 bgp router-id 2.2.2.2
 neighbor 3.3.3.3 remote-as 65000
 neighbor 3.3.3.3 update-source Loopback0
 neighbor 4.4.4.4 remote-as 65000
 neighbor 4.4.4.4 update-source Loopback0
 network 2.2.2.2 mask 255.255.255.255
!
end
write memory
```

