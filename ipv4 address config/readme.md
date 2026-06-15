# IPv4 Addressing and Router Interface Configuration Lab

## Description

This Cisco Packet Tracer lab demonstrates basic IPv4 addressing and router interface configuration. The topology consists of a single router connecting three separate LANs through Gigabit Ethernet interfaces. The lab focuses on configuring router interfaces, assigning IP addresses to end devices, verifying connectivity, and saving configurations.

---

## Topology Overview

### Networks

| Network | Subnet |
|----------|----------|
| LAN 1 | 15.0.0.0/8 |
| LAN 2 | 182.98.0.0/16 |
| LAN 3 | 201.191.20.0/24 |

### Addressing Table

| Device | Interface | IP Address | Subnet Mask |
|----------|----------|----------|----------|
| R1 | G0/0 | 15.255.255.254 | 255.0.0.0 |
| R1 | G0/1 | 182.98.255.254 | 255.255.0.0 |
| R1 | G0/2 | 201.191.20.254 | 255.255.255.0 |
| PC1 | NIC | 15.0.0.1 | 255.0.0.0 |
| PC2 | NIC | 182.98.0.1 | 255.255.0.0 |
| PC3 | NIC | 201.191.20.1 | 255.255.255.0 |

### Default Gateways

| Device | Gateway |
|----------|----------|
| PC1 | 15.255.255.254 |
| PC2 | 182.98.255.254 |
| PC3 | 201.191.20.254 |

---

## Objectives

- Configure router hostname.
- Configure IPv4 addresses on router interfaces.
- Enable router interfaces.
- Add interface descriptions.
- Configure IP addresses on end devices.
- Verify connectivity using ping.
- Save the router configuration.

---

## Router Configuration

### Set Hostname

```bash
enable
configure terminal
hostname R1
```

### Configure GigabitEthernet 0/0

```bash
interface g0/0
description LAN_15_NETWORK
ip address 15.255.255.254 255.0.0.0
no shutdown
exit
```

### Configure GigabitEthernet 0/1

```bash
interface g0/1
description LAN_182_NETWORK
ip address 182.98.255.254 255.255.0.0
no shutdown
exit
```

### Configure GigabitEthernet 0/2

```bash
interface g0/2
description LAN_201_NETWORK
ip address 201.191.20.254 255.255.255.0
no shutdown
exit
```

### Save Configuration

```bash
copy running-config startup-config
```

---

## Verification Commands

### Check Interface Status

```bash
show ip interface brief
```

### View Running Configuration

```bash
show running-config
```

### View Interface Descriptions

```bash
show interfaces description
```

### View Startup Configuration

```bash
show startup-config
```

---

## PC Configuration

### PC1

```text
IP Address: 15.0.0.1
Subnet Mask: 255.0.0.0
Default Gateway: 15.255.255.254
```

### PC2

```text
IP Address: 182.98.0.1
Subnet Mask: 255.255.0.0
Default Gateway: 182.98.255.254
```

### PC3

```text
IP Address: 201.191.20.1
Subnet Mask: 255.255.255.0
Default Gateway: 201.191.20.254
```

---

## Connectivity Testing

### From PC1

```cmd
ping 182.98.0.1
ping 201.191.20.1
```

### From PC2

```cmd
ping 15.0.0.1
ping 201.191.20.1
```

### From PC3

```cmd
ping 15.0.0.1
ping 182.98.0.1
```

---

## Expected Results

- All router interfaces should display an **up/up** status.
- All PCs should successfully reach their default gateway.
- Inter-LAN communication should be successful.
- Ping tests between all PCs should succeed.
- Configuration should be saved in NVRAM.

---

## Skills Practiced

- IPv4 Addressing
- Router Configuration
- Interface Management
- Cisco IOS Commands
- Connectivity Verification
- Basic Network Troubleshooting
- Configuration Saving

---

## File

```text
IPv4 Addresses.pkt
```

## Author

Created as part of CCNA networking practice using Cisco Packet Tracer.
