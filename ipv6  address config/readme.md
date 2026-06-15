# IPv6 Configuration (Part 1)

## Overview

This Cisco Packet Tracer lab introduces IPv6 configuration in a dual-stack environment. The IPv4 configuration is already completed, and the objective is to enable IPv6 routing, configure IPv6 addresses on router interfaces and end devices, and verify end-to-end connectivity using both IPv4 and IPv6.

## Topology

The network consists of:

- 1 Cisco 2911 Router (R1)
- 3 Cisco 2960 Switches
- 3 PCs
- 3 LAN segments

### IPv4 Networks

| Network | Gateway |
|----------|----------|
| 192.168.1.0/24 | 192.168.1.1 |
| 192.168.2.0/24 | 192.168.2.1 |
| 192.168.3.0/24 | 192.168.3.1 |

### IPv6 Networks

| Network | Gateway |
|----------|----------|
| 2001:DB8:0:1::/64 | 2001:DB8:0:1::1 |
| 2001:DB8:0:2::/64 | 2001:DB8:0:2::1 |
| 2001:DB8:0:3::/64 | 2001:DB8:0:3::1 |

## Learning Objectives

- Enable IPv6 routing on a Cisco router
- Configure IPv6 addresses on router interfaces
- Configure IPv6 addresses on end devices
- Configure IPv6 default gateways
- Verify IPv6 interface status
- Test IPv4 and IPv6 connectivity
- Understand dual-stack network operation

## Router Configuration

Enable IPv6 routing:

```bash
R1(config)# ipv6 unicast-routing
```

Configure interfaces:

```bash
R1(config)# interface g0/0
R1(config-if)# ipv6 address 2001:DB8:0:1::1/64
R1(config-if)# no shutdown

R1(config)# interface g0/1
R1(config-if)# ipv6 address 2001:DB8:0:2::1/64
R1(config-if)# no shutdown

R1(config)# interface g0/2
R1(config-if)# ipv6 address 2001:DB8:0:3::1/64
R1(config-if)# no shutdown
```

## Verification Commands

Check IPv6 interface status:

```bash
show ipv6 interface brief
```

Display IPv6 routing table:

```bash
show ipv6 route
```

View running configuration:

```bash
show running-config
```

## Connectivity Tests

### IPv4

```cmd
ping 192.168.2.2
ping 192.168.3.2
```

### IPv6

```cmd
ping 2001:DB8:0:2::2
ping 2001:DB8:0:3::2
```

## Expected Results

- IPv6 routing is enabled on R1
- All router interfaces are operational
- PCs can communicate using IPv4
- PCs can communicate using IPv6
- Dual-stack connectivity is verified successfully

## Skills Practiced

- IPv6 Addressing
- Dual-Stack Networking
- Cisco IOS Configuration
- IPv6 Routing
- Network Verification
- Connectivity Troubleshooting

## File

```text
IPv6 Configuration (Part 1).pkt
```

## Author

CCNA Networking Labs – Cisco Packet Tracer