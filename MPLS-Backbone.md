# Cisco MPLS Backbone Lab  

## 📌 **Projektoversigt**
Dette repository indeholder konfigurationer til en fuldt fungerende **MPLS backbone** bygget med **OSPF og BGP**.  
Labbet kan bruges til at forstå **dynamisk routing**, **BGP peerings** og **MPLS-forberedelse**.  

---

## 🖥 **Netværksdiagram**

![image](https://github.com/user-attachments/assets/30f899b2-d7a4-47bd-a884-45d8197de71a)

- **5 Core Routere**: R1, R2, R3, R4, R5  
- **Dynamisk Routing**: OSPF (Interne forbindelser)  
- **BGP**: Bruges til at annoncere loopback-netværk  
- **Kunde Edge Routers (CE1/CE2)**: (Kan tilføjes senere for MPLS VPN)  

---

## 🛠 **Konfigurerede Protokoller**
✔ **OSPF** til intra-netværksforbindelser  
✔ **BGP** til annoncering af loopbacks  
✔ **Statisk IP-allokering på interconnects**  

---

## 📝 **Netværks-IP Plan**
| Router | Interface | IP-adresse | Forbindelse |
|---------|------------|-------------|--------------|
| R1 | Lo0 | 1.1.1.1/32 | Loopback |
| R1 | Gi0/0 | 10.0.5.1/24 | R1 ↔ R5 |
| R1 | Gi0/1 | 10.0.2.1/24 | R1 ↔ R4 |
| R2 | Lo0 | 2.2.2.2/32 | Loopback |
| R2 | Gi0/0 | 10.0.8.2/24 | R2 ↔ R4 |
| R2 | Gi0/1 | 10.0.7.2/24 | R2 ↔ R3 |
| R3 | Lo0 | 3.3.3.3/32 | Loopback |
| R3 | Gi0/0 | 10.0.6.3/24 | R3 ↔ R5 |
| R3 | Gi0/1 | 10.0.7.3/24 | R3 ↔ R2 |
| R4 | Lo0 | 4.4.4.4/32 | Loopback |
| R4 | Gi0/0 | 10.0.2.4/24 | R4 ↔ R1 |
| R4 | Gi0/1 | 10.0.8.4/24 | R4 ↔ R2 |
| R5 | Lo0 | 5.5.5.5/32 | Loopback |
| R5 | Gi0/0 | 10.0.5.5/24 | R5 ↔ R1 |
| R5 | Gi0/1 | 10.0.6.5/24 | R5 ↔ R3 |

---
