# Cisco Packet Tracer - VLAN Configuration Lab

## 📌 Project Overview

This project demonstrates the implementation of Virtual Local Area Networks (VLANs) using Cisco Packet Tracer. The network is segmented into multiple departments, each assigned to a separate VLAN to improve network organization, security, and traffic management.

The lab includes:

- VLAN creation and assignment
- Inter-VLAN routing using a Router-on-a-Stick configuration
- IP addressing and subnetting
- VLAN trunking between switch and router
- Connectivity testing using ICMP (Ping)

---

## 🏗️ Network Topology

![Network Topology](topology.png)

### VLAN Structure

| VLAN ID | Department | Network Address | Subnet Mask |
|----------|------------|----------------|-------------|
| 10 | Engineering | 10.0.0.0/26 | 255.255.255.192 |
| 20 | HR | 10.0.0.64/26 | 255.255.255.192 |
| 30 | Sales | 10.0.0.128/26 | 255.255.255.192 |

---

## 🖥️ Device Configuration

### Engineering VLAN (VLAN 10)

| Device | IP Address |
|---------|-----------|
| PC1 | 10.0.0.1 |
| PC2 | 10.0.0.2 |
| Gateway | 10.0.0.62 |

### HR VLAN (VLAN 20)

| Device | IP Address |
|---------|-----------|
| PC3 | 10.0.0.65 |
| PC4 | 10.0.0.66 |
| Gateway | 10.0.0.126 |

### Sales VLAN (VLAN 30)

| Device | IP Address |
|---------|-----------|
| PC5 | 10.0.0.129 |
| PC6 | 10.0.0.130 |
| Gateway | 10.0.0.190 |

---

## 🎯 Objectives

- Configure VLANs on the switch.
- Assign switch ports to the appropriate VLANs.
- Configure trunking between Switch SW1 and Router R1.
- Configure Router-on-a-Stick for Inter-VLAN Routing.
- Verify communication within and across VLANs.
- Analyze broadcast traffic behavior.

---

## ⚙️ Configuration Tasks

### 1. Configure IP Addressing

Assign IP addresses to all PCs according to the addressing table above.

### 2. Create VLANs

Create the following VLANs on SW1:

```bash
VLAN 10 - Engineering
VLAN 20 - HR
VLAN 30 - Sales
```

### 3. Assign Access Ports

Assign switch ports connected to end devices to their respective VLANs.

### 4. Configure Trunk Port

Configure the interface connecting SW1 to R1 as a trunk.

```bash
switchport mode trunk
```

### 5. Configure Router-on-a-Stick

Create subinterfaces for each VLAN and assign gateway addresses.

Example:

```bash
interface g0/0.10
 encapsulation dot1Q 10
 ip address 10.0.0.62 255.255.255.192

interface g0/0.20
 encapsulation dot1Q 20
 ip address 10.0.0.126 255.255.255.192

interface g0/0.30
 encapsulation dot1Q 30
 ip address 10.0.0.190 255.255.255.192
```

---

## ✅ Verification

Use the following commands to verify the configuration:

### Switch

```bash
show vlan brief
show interfaces trunk
```

### Router

```bash
show ip interface brief
show running-config
```

### Connectivity Tests

```bash
ping <destination-ip>
```

Verify:

- Communication within the same VLAN
- Inter-VLAN communication
- Broadcast domain isolation

---

## 📂 Project Files

```text
├── VLANs-Part1.pkt
├── topology.png
└── README.md
```

---

## 🛠️ Technologies Used

- Cisco Packet Tracer 9.x
- Cisco Router (1941)
- Cisco Switch (2960)
- VLANs
- IEEE 802.1Q Trunking
- Inter-VLAN Routing

---

## 📚 Learning Outcomes

After completing this lab, you will understand:

- VLAN implementation and management
- Switch port configuration
- Trunking concepts
- Router-on-a-Stick architecture
- Inter-VLAN communication
- Network segmentation best practices

---

## 👨‍💻 Author

**Your Name**

CCNA Networking Lab Project

GitHub: https://github.com/yourusername

---

## 📜 License

This project is intended for educational and learning purposes.