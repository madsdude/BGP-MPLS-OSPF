```
hostname R4
!
interface Loopback0
 ip address 4.4.4.4 255.255.255.255
!
interface GigabitEthernet0/0  # Til R1
 ip address 10.0.2.4 255.255.255.0
 no shutdown
!
interface GigabitEthernet0/1  # Til R2
 ip address 10.0.8.4 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 4.4.4.4
 network 10.0.2.0 0.0.0.255 area 0
 network 10.0.8.0 0.0.0.255 area 0
 network 4.4.4.4 0.0.0.0 area 0
!
router bgp 65000
 bgp router-id 4.4.4.4
 neighbor 1.1.1.1 remote-as 65000
 neighbor 1.1.1.1 update-source Loopback0
 neighbor 2.2.2.2 remote-as 65000
 neighbor 2.2.2.2 update-source Loopback0
 network 4.4.4.4 mask 255.255.255.255
!
end
write memory

```
