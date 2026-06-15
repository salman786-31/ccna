# Cisco Packet Tracer - OSPF Routing Configuration

## 📌 Project Overview

This project demonstrates the configuration and implementation of **OSPF (Open Shortest Path First)** dynamic routing protocol using Cisco Packet Tracer.

The network consists of multiple routers connected together in an OSPF Area 0 environment. OSPF is configured to enable automatic route exchange between routers and provide connectivity between different networks.

The objective of this project is to configure router interfaces, assign IP addresses, configure loopback interfaces, enable OSPF routing, and advertise a default route using an ASBR (Autonomous System Boundary Router).

---

## 🛠️ Tools Used

* Cisco Packet Tracer
* Cisco IOS Command Line Interface (CLI)

---

## 🌐 Network Topology

Devices Used:

* 4 × Cisco Routers (R1, R2, R3, R4)
* 1 × Cisco 2960 Switch
* 1 × End Device (PC1)

Routing Protocol:

```
OSPF Area 0
```

---

## 🔗 Network Connections

Topology:

```
                 ISP Router
                     |
                  R1 (ASBR)
                 /        \
              R2            R3
               \            /
                \          /
                  R4
                   |
                Switch
                   |
                  PC1
```

---

## ⚙️ Configuration Implemented

### Router Configuration

Configured on all routers:

* Hostname configuration
* IP address assignment
* Interface activation
* Loopback interface configuration
* OSPF routing configuration

---

## 🌐 IP Addressing

### Router Interfaces

```
R1 - R2 Link
Network: 10.0.12.0/30

R1 - R3 Link
Network: 10.0.13.0/30

R2 - R4 Link
Network: 10.0.24.0/30

R3 - R4 Link
Network: 10.0.34.0/30

PC Network
Network: 192.168.4.0/24
```

---

## 🔄 OSPF Configuration

OSPF Process:

```
router ospf 1
```

Area:

```
area 0
```

Example configuration:

```
router ospf 1
network 10.0.12.0 0.0.0.3 area 0
network 10.0.13.0 0.0.0.3 area 0
network 10.0.24.0 0.0.0.3 area 0
network 10.0.34.0 0.0.0.3 area 0
network 192.168.4.0 0.0.0.255 area 0
```

---

## 🔁 Loopback Interface Configuration

Loopback interfaces configured for router identification:

Example:

```
R1:
Loopback0
IP: 1.1.1.1/32


R2:
Loopback0
IP: 2.2.2.2/32


R3:
Loopback0
IP: 3.3.3.3/32


R4:
Loopback0
IP: 4.4.4.4/32
```

---

## 🌍 Default Route Configuration (ASBR)

R1 is configured as an ASBR to advertise the default route into the OSPF domain.

Configuration:

```
ip route 0.0.0.0 0.0.0.0 <ISP Next-Hop>

router ospf 1
default-information originate
```

This allows other routers in the OSPF network to learn the default route.

---

## 🔍 Verification Commands

Check OSPF neighbors:

```
show ip ospf neighbor
```

Check routing table:

```
show ip route
```

Check OSPF configuration:

```
show ip protocols
```

Check interfaces:

```
show ip interface brief
```

---

## 🎯 Learning Outcomes

Through this project, I learned:

* OSPF dynamic routing configuration
* Router-to-router communication
* OSPF neighbor relationships
* Area 0 configuration
* Loopback interface usage
* ASBR and default route advertisement
* Routing table analysis

---

## 📂 Project File

```
OSPF_Configuration.pkt
```

Cisco Packet Tracer file included in this repository.

---

## 👨‍💻 Author

**Salman**
Cybersecurity Student

---

## ⭐ Note

This project is created for educational purposes to practice CCNA-level routing concepts and dynamic routing protocols using Cisco Packet Tracer.
