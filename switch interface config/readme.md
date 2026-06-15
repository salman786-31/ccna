# Cisco Packet Tracer - Switch Interface Configuration

## 📌 Project Overview

This project is a network simulation created using Cisco Packet Tracer. It demonstrates the configuration of router and switch interfaces in a small enterprise network environment.

The main objective of this project is to configure Cisco devices with proper hostnames, IP addressing, interface descriptions, speed and duplex settings, and manage unused interfaces according to networking best practices.

---

## 🛠️ Tools Used

* Cisco Packet Tracer
* Cisco IOS Command Line Interface (CLI)

---

## 🌐 Network Topology

The network consists of:

* 1 × Cisco 2911 Router (R1)
* 2 × Cisco 2960 Switches (SW1 and SW2)
* 4 × End Devices (PC1, PC2, PC3, PC4)

Network Address:

```
172.16.0.0/16
```

Topology:

```
                 Router R1
                    |
                  G0/0
                    |
                  G0/1
                  SW1
              /          \
           F0/1          F0/2
            |              |
           PC1            PC2

                  |
                G0/2
                  |
                  SW2
              /          \
           F0/1          F0/2
            |              |
           PC3            PC4
```

---

## ⚙️ Configuration Implemented

### Router Configuration (R1)

Configured:

* Device hostname
* IP address assignment
* Interface description
* Interface activation

Example:

```
interface gigabitEthernet 0/0
description Connection_to_SW1
ip address 172.16.0.254 255.255.0.0
no shutdown
```

---

## Switch Configuration

### Switch 1 (SW1)

Configured interfaces:

```
G0/1 → Connected to Router R1
G0/2 → Connected to SW2
F0/1 → Connected to PC1
F0/2 → Connected to PC2
```

Interface configuration:

```
interface gigabitEthernet 0/1
description Connection_to_Router
speed 1000
duplex full
no shutdown
```

```
interface gigabitEthernet 0/2
description Connection_to_SW2
speed 1000
duplex full
no shutdown
```

```
interface fastEthernet 0/1
description PC1_Connection
no shutdown
```

```
interface fastEthernet 0/2
description PC2_Connection
no shutdown
```

---

### Switch 2 (SW2)

Configured interfaces:

```
G0/1 → Connected to SW1
F0/1 → Connected to PC3
F0/2 → Connected to PC4
```

Interface configuration:

```
interface gigabitEthernet 0/1
description Connection_to_SW1
speed 1000
duplex full
no shutdown
```

```
interface fastEthernet 0/1
description PC3_Connection
no shutdown
```

```
interface fastEthernet 0/2
description PC4_Connection
no shutdown
```

---

## 💻 IP Address Configuration

| Device | IP Address   | Subnet Mask |
| ------ | ------------ | ----------- |
| R1     | 172.16.0.254 | 255.255.0.0 |
| PC1    | 172.16.0.1   | 255.255.0.0 |
| PC2    | 172.16.0.2   | 255.255.0.0 |
| PC3    | 172.16.0.3   | 255.255.0.0 |
| PC4    | 172.16.0.4   | 255.255.0.0 |

---

## 🔍 Verification Commands

The following commands were used for checking the configuration:

```
show ip interface brief
```

```
show interfaces
```

```
show running-config
```

```
show version
```

Connectivity testing:

```
ping <destination IP>
```

---

## 🎯 Learning Outcomes

Through this project, I gained practical knowledge of:

* Cisco router and switch configuration
* Interface management
* IP addressing
* Network connectivity testing
* Troubleshooting network issues
* Basic CCNA networking concepts

---

## 📂 Project File

```
Switch_Interface_Configuration.pkt
```

Cisco Packet Tracer file included in this repository.

---

## 👨‍💻 Author

**Salman**
Cybersecurity Student

---

## ⭐ Note

This project is created for educational purposes to practice Cisco networking concepts and CCNA-level configurations using Cisco Packet Tracer.
