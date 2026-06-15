# Cisco Packet Tracer - VLAN, FTP & DNS Services Lab

## 📌 Project Overview

This project demonstrates the implementation of VLAN segmentation combined with network services including:

- VLAN Configuration
- Trunking between switches
- Inter-switch VLAN communication
- DNS Server Configuration
- FTP Server Configuration
- Router-based Network Segmentation
- End-to-End Connectivity Testing

The lab simulates a small enterprise network where users in different VLANs access centralized DNS and FTP services.

---

## 🏗️ Network Topology

![Network Topology](topology.png)

### Components

| Device | Quantity |
|----------|----------|
| Cisco 1941 Routers | 2 |
| Cisco 2960 Switches | 2 |
| PCs | 5 |
| Server | 1 |

---

## 🌐 Network Design

### VLAN 10

| Device | IP Address |
|----------|------------|
| Router0 | 192.168.1.1 |
| PC0 | 192.168.1.11 |
| PC1 | 192.168.1.12 |
| PC2 | 192.168.1.13 |

Network:

```text
192.168.1.0/24
```

---

### VLAN 20

| Device | IP Address |
|----------|------------|
| Router1 | 192.169.1.1 |
| PC3 | 192.168.1.13 |
| PC4 | 192.169.1.11 |
| Server0 | 192.169.1.12 |

Network:

```text
192.169.1.0/24
```

---

## 🎯 Objectives

- Create and configure VLANs.
- Assign switch ports to VLANs.
- Configure trunk links between switches.
- Configure FTP service on the server.
- Configure DNS service on the server.
- Verify hostname resolution using DNS.
- Verify file transfer using FTP.
- Test connectivity between VLAN members.

---

## ⚙️ VLAN Configuration

### VLAN Creation

```bash
vlan 10
 name SALES

vlan 20
 name IT
```

### Assign Access Ports

```bash
interface range fa0/1-3
 switchport mode access
 switchport access vlan 10

interface range fa0/1-2
 switchport mode access
 switchport access vlan 20
```

---

## 🔗 Trunk Configuration

Configure the link between Switch0 and Switch1 as a trunk.

```bash
interface fa0/24
 switchport mode trunk
```

Verify:

```bash
show interfaces trunk
```

---

## 🌍 DNS Server Configuration

DNS service is configured on Server0.

### Example DNS Records

| Domain Name | IP Address |
|------------|------------|
| ftp.company.local | 192.169.1.12 |
| server.company.local | 192.169.1.12 |

### Verification

From a PC:

```bash
ping ftp.company.local
```

Expected Result:

```text
DNS resolves hostname to server IP address.
```

---

## 📁 FTP Server Configuration

FTP service is enabled on Server0.

### Sample FTP Credentials

```text
Username: admin
Password: cisco
```

### FTP Connection Test

```bash
ftp 192.169.1.12
```

or

```bash
ftp ftp.company.local
```

---

## 🧪 Verification Tasks

### VLAN Verification

```bash
show vlan brief
```

### Trunk Verification

```bash
show interfaces trunk
```

### DNS Verification

```bash
ping ftp.company.local
```

### FTP Verification

```bash
ftp ftp.company.local
```

### Connectivity Test

```bash
ping 192.169.1.12
```

---

## 📂 Project Structure

```text
VLAN-FTP-DNS-LAB/
│
├── VLAN_FTP_DNS.pkt
├── topology.png
└── README.md
```

---

## 🔍 Features Demonstrated

### VLAN Technology

- Broadcast domain separation
- Improved network organization
- Enhanced security

### DNS Service

- Hostname-to-IP resolution
- Simplified resource access

### FTP Service

- Centralized file storage
- Remote file transfer

### Trunking

- VLAN traffic transport between switches
- IEEE 802.1Q encapsulation

---

## 🛠 Technologies Used

- Cisco Packet Tracer 9.x
- Cisco 1941 Router
- Cisco 2960 Switch
- VLANs
- IEEE 802.1Q Trunking
- DNS Service
- FTP Service

---

## 📚 Learning Outcomes

By completing this lab, you will learn:

- VLAN implementation and management
- Switch trunk configuration
- DNS server deployment
- FTP server deployment
- Client-server communication
- Enterprise network service integration

---

## 📸 Screenshot

Place your topology screenshot in the repository as:

```text
topology.png
```

It will automatically display at the top of this README.

---

## 👨‍💻 Author

**Your Name**

CCNA Networking Lab Series

GitHub: https://github.com/yourusername

LinkedIn: https://linkedin.com/in/yourprofile

---

## 📜 License

This project is provided for educational and learning purposes.