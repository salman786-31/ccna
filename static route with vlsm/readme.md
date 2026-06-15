# 🌐 Cisco Packet Tracer – Static Routing with VLSM

## 📖 Project Overview

This project demonstrates how to design a network using **Variable Length Subnet Masking (VLSM)** and configure **static routing** between routers in Cisco Packet Tracer.

The network is subnetted from a single **192.168.5.0/24** address space into multiple LANs with different host requirements and a point-to-point WAN link. Static routes are then configured to enable communication between all networks.

This lab helps build practical skills in **IP subnetting, VLSM design, and static route configuration**, making it an excellent exercise for CCNA preparation.

---

# 🎯 Learning Objectives

- Design a VLSM addressing scheme from a single network.
- Allocate subnets based on host requirements.
- Configure router interfaces with appropriate IP addresses.
- Assign IP addresses and default gateways to PCs.
- Configure static routes between routers.
- Verify routing tables and end-to-end connectivity.
- Practice efficient IPv4 address utilization.

---

# 🖥️ Network Topology

```
                     +----------------------+
                     |      Router R1       |
                     +----------------------+
                      |        |         |
                      |        |         |
                 LAN1 |        | LAN2    |
                      |        |         |
                   +------+  +------+ 
                   | SW1 |   | SW2 |
                   +------+  +------+
                      |          |
                    PC1         PC2

                          ||
                    Point-to-Point Link
                          ||

                     +----------------------+
                     |      Router R2       |
                     +----------------------+
                      |                    |
                 LAN3 |                    | LAN4
                      |                    |
                   +------+            +------+
                   | SW3 |            | SW4 |
                   +------+            +------+
                      |                    |
                    PC3                  PC4
```

---

# 📊 Host Requirements

| Network | Required Hosts |
|----------|---------------:|
| LAN2 | 64 Hosts |
| LAN1 | 45 Hosts |
| LAN3 | 14 Hosts |
| LAN4 | 9 Hosts |
| R1 ↔ R2 Link | 2 Hosts |

---

# 🧮 Example VLSM Addressing Plan

Starting network: **192.168.5.0/24**

| Network | CIDR | Subnet Mask | Usable Hosts |
|----------|------|-------------------|-------------|
| LAN2 | /25 | 255.255.255.128 | 126 |
| LAN1 | /26 | 255.255.255.192 | 62 |
| LAN3 | /28 | 255.255.255.240 | 14 |
| LAN4 | /28 | 255.255.255.240 | 14 |
| R1 ↔ R2 WAN | /30 | 255.255.255.252 | 2 |

> **Note:** The exact subnet assignments may vary depending on your implementation. This table shows one valid VLSM allocation strategy.

---

# ⚙️ Configuration Tasks

## 1. Configure Router Hostnames

```bash
enable
configure terminal
hostname R1
```

```bash
enable
configure terminal
hostname R2
```

---

## 2. Configure Router Interfaces

Assign the appropriate IP address and subnet mask to each router interface based on your VLSM plan.

Example:

```bash
interface g0/0
 ip address <IP_ADDRESS> <SUBNET_MASK>
 no shutdown
```

Repeat for all LAN and WAN interfaces.

---

## 3. Configure PCs

For each PC:

- Assign the **first usable IP address** in its subnet.
- Configure the **default gateway** as the router interface connected to that LAN.

Example:

| Device | IP Address | Default Gateway |
|----------|------------|-----------------|
| PC1 | First usable address | Router LAN interface |
| PC2 | First usable address | Router LAN interface |
| PC3 | First usable address | Router LAN interface |
| PC4 | First usable address | Router LAN interface |

---

## 4. Configure Static Routes

### Example on Router R1

```bash
ip route <REMOTE_NETWORK> <SUBNET_MASK> <NEXT_HOP_IP>
```

### Example on Router R2

```bash
ip route <REMOTE_NETWORK> <SUBNET_MASK> <NEXT_HOP_IP>
```

Configure routes for all remote networks so traffic can be forwarded correctly.

---

# 🔍 Verification Commands

## View Interface Status

```bash
show ip interface brief
```

## Display Routing Table

```bash
show ip route
```

## View Running Configuration

```bash
show running-config
```

## Test Connectivity

From a PC command prompt:

```text
ping <destination-ip>
```

Successful replies confirm that routing has been configured correctly.

---

# 📚 Key Concepts Covered

- Variable Length Subnet Masking (VLSM)
- IPv4 Address Planning
- Efficient Address Allocation
- Static Routing
- Router Interface Configuration
- Default Gateway Configuration
- Point-to-Point WAN Networks
- Connectivity Verification and Troubleshooting

---

# 📝 Common Cisco IOS Commands

| Command | Description |
|----------|-------------|
| `hostname R1` | Configure router hostname |
| `interface g0/0` | Enter interface configuration mode |
| `ip address` | Assign an IP address to an interface |
| `no shutdown` | Enable an interface |
| `ip route` | Configure a static route |
| `show ip route` | Display the routing table |
| `show ip interface brief` | Display interface status |
| `show running-config` | Display the active configuration |
| `ping` | Verify network connectivity |
| `copy running-config startup-config` | Save the configuration |

---

# 💡 Key Takeaways

- VLSM minimizes wasted IP addresses by allocating subnet sizes based on actual host requirements.
- Static routing is suitable for small or stable networks where routes do not change frequently.
- Proper subnet planning and correct next-hop configuration are essential for successful communication.
- Always verify interface status, routing tables, and connectivity after configuration.

---

# 🎓 CCNA Topics Covered

- IPv4 Addressing
- Variable Length Subnet Masking (VLSM)
- Static Routing
- Router Configuration
- LAN and WAN Connectivity
- Routing Table Verification
- Default Gateway Configuration
- Network Troubleshooting

---

# 👨‍💻 Author

**Danush Kalyan**

This Cisco Packet Tracer lab was created as part of CCNA practice to strengthen practical knowledge of VLSM subnetting and static routing in enterprise network environments.