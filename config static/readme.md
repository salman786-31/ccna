# 🌐 Cisco Packet Tracer – Configuring Static Routes

## 📖 Project Overview

This Cisco Packet Tracer lab demonstrates how to configure **IPv4 static routing** between multiple routers to enable communication between different networks.

The topology consists of **three routers**, **two LANs**, **two switches**, and **two end devices (PCs)**. Static routes are manually configured on each router so that **PC1 can successfully communicate with PC2** across multiple networks.

This lab is ideal for students preparing for the **Cisco CCNA (200-301)** certification and learning the fundamentals of routing.

---

# 🎯 Objectives

- Configure IP addresses on routers and PCs.
- Assign default gateways to end devices.
- Configure router hostnames.
- Configure static routes between routers.
- Verify routing tables.
- Test end-to-end connectivity using `ping`.
- Understand how packets travel through multiple routers.

---

# 🗺️ Network Topology

```
                    192.168.12.0/24
        -----------------------------------

        192.168.1.0/24                192.168.13.0/24

+--------+      +------+       +------+       +------+
|  PC1   |------| SW1  |-------|  R1  |-------|  R2  |
+--------+      +------+       +------+       +------+
                                       |
                                       |
                                       |
                                    +------+
                                    |  R3  |
                                    +------+
                                       |
                                       |
                                 192.168.3.0/24
                                       |
                                  +----------+
                                  |   SW2    |
                                  +----------+
                                       |
                                  +----------+
                                  |   PC2    |
                                  +----------+
```

---

# 📋 IP Addressing Scheme

| Device | Interface | IP Address |
|----------|-----------|----------------|
| PC1 | NIC | `192.168.1.1/24` |
| R1 | G0/1 | `192.168.1.254/24` |
| R1 | G0/0 | `192.168.12.1/24` |
| R2 | G0/0 | `192.168.12.2/24` |
| R2 | G0/1 | `192.168.13.2/24` |
| R3 | G0/0 | `192.168.13.3/24` |
| R3 | G0/1 | `192.168.3.254/24` |
| PC2 | NIC | `192.168.3.1/24` |

### Default Gateways

| Device | Gateway |
|----------|----------------|
| PC1 | `192.168.1.254` |
| PC2 | `192.168.3.254` |

---

# ⚙️ Router Configuration

## Configure Hostnames

### Router 1

```bash
enable
configure terminal
hostname R1
```

### Router 2

```bash
enable
configure terminal
hostname R2
```

### Router 3

```bash
enable
configure terminal
hostname R3
```

---

# 🌍 Configure Interface IP Addresses

## R1

```bash
interface g0/1
 ip address 192.168.1.254 255.255.255.0
 no shutdown

interface g0/0
 ip address 192.168.12.1 255.255.255.0
 no shutdown
```

---

## R2

```bash
interface g0/0
 ip address 192.168.12.2 255.255.255.0
 no shutdown

interface g0/1
 ip address 192.168.13.2 255.255.255.0
 no shutdown
```

---

## R3

```bash
interface g0/0
 ip address 192.168.13.3 255.255.255.0
 no shutdown

interface g0/1
 ip address 192.168.3.254 255.255.255.0
 no shutdown
```

---

# 🛣️ Configure Static Routes

## On R1

```bash
ip route 192.168.3.0 255.255.255.0 192.168.12.2
```

---

## On R2

```bash
ip route 192.168.1.0 255.255.255.0 192.168.12.1

ip route 192.168.3.0 255.255.255.0 192.168.13.3
```

---

## On R3

```bash
ip route 192.168.1.0 255.255.255.0 192.168.13.2
```

---

# 🔍 Verification Commands

Display routing table:

```bash
show ip route
```

View interface status:

```bash
show ip interface brief
```

Verify configured static routes:

```bash
show running-config
```

Test connectivity:

```bash
ping 192.168.3.1
```

or from **PC1 Command Prompt**:

```text
ping 192.168.3.1
```

Successful replies confirm that the static routes are functioning correctly.

---

# 📚 Key Concepts Learned

- IPv4 Addressing
- Static Routing
- Next-Hop IP Configuration
- Router Interface Configuration
- Default Gateway Configuration
- Routing Table Verification
- End-to-End Connectivity Testing
- Cisco IOS CLI Commands

---

# 📝 Important Commands Summary

| Command | Purpose |
|----------|---------|
| `hostname R1` | Set router hostname |
| `ip address` | Assign IP to an interface |
| `no shutdown` | Enable the interface |
| `ip route` | Configure a static route |
| `show ip route` | View routing table |
| `show ip interface brief` | Check interface status |
| `ping` | Test network connectivity |
| `copy running-config startup-config` | Save the configuration |

---

# 💡 Notes

- Static routes must be configured manually on each router.
- Ensure all interfaces are enabled with `no shutdown`.
- PCs must have the correct default gateway configured.
- Incorrect next-hop addresses or subnet masks can prevent successful routing.

---

# 🎓 CCNA Topics Covered

- IPv4 Addressing
- Router Configuration
- Static Routing
- Routing Tables
- Interface Management
- Default Gateway Configuration
- Connectivity Verification
- Troubleshooting with `ping` and `show` commands

---

# 👨‍💻 Author

**Danush Kalyan**

This project was created as part of CCNA practice to build a strong understanding of static routing and inter-network communication using Cisco Packet Tracer.