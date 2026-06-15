

# 🌐 Cisco Packet Tracer – Inter-VLAN Routing (Router-on-a-Stick)

## 📖 Project Overview

This Cisco Packet Tracer project demonstrates **Inter-VLAN Routing using the Router-on-a-Stick (ROAS) technique**. Multiple VLANs are created on Layer 2 switches, and a single router interface is divided into subinterfaces to provide routing between VLANs.

The topology consists of **three switches**, **one router**, **multiple PCs**, and **one server** connected across **VLAN 10, VLAN 20, and VLAN 30**. Trunk links carry traffic between switches and the router, enabling communication between devices in different VLANs.

This project is ideal for learners preparing for the **Cisco CCNA (200-301)** certification and studying VLANs and inter-VLAN communication.

---

# 🎯 Learning Objectives

- Create and configure VLANs on Cisco switches.
- Assign switch ports to the appropriate VLANs.
- Configure trunk ports between switches.
- Configure a trunk link between the switch and router.
- Implement Router-on-a-Stick using router subinterfaces.
- Configure IEEE 802.1Q encapsulation.
- Verify communication between different VLANs.
- Test end-to-end connectivity using `ping`.

---

# 🖥️ Network Topology

```
                    +----------------------+
                    |      Router0         |
                    |   (Router-on-a-Stick)|
                    +----------+-----------+
                               |
                        Trunk Link (802.1Q)
                               |
                     +----------------------+
                     |     Core Switch      |
                     +----------------------+
                      /          |          \
             Trunk   /           |           \ Trunk
                    /            |            \
         +-------------+               +-------------+
         | Switch1     |               | Switch2     |
         +-------------+               +-------------+
          |         |                   |          |
        PC4       PC5                 PC2      Server
      VLAN 10   VLAN 10             VLAN 30   VLAN 30

                 +----------------------+
                 |     Core Switch       |
                 +----------------------+
                    |               |
                  PC0             PC1
                VLAN 20         VLAN 20
```

---

# 📊 VLAN Addressing Plan

| VLAN | Network | Default Gateway | Connected Devices |
|------|----------------|----------------|------------------|
| VLAN 10 | `192.168.10.0/24` | `192.168.10.1` | PC4, PC5 |
| VLAN 20 | `192.168.20.0/24` | `192.168.20.1` | PC0, PC1 |
| VLAN 30 | `192.168.30.0/24` | `192.168.30.1` | PC2, Server |

---

# ⚙️ Router Configuration (Router-on-a-Stick)

## Configure Subinterfaces

```bash
enable
configure terminal

interface gigabitEthernet0/0
 no shutdown

interface gigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface gigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0

interface gigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.1 255.255.255.0
```

---

# 🔀 Switch Configuration

## Create VLANs

```bash
enable
configure terminal

vlan 10
 name VLAN10

vlan 20
 name VLAN20

vlan 30
 name VLAN30
```

---

## Assign Access Ports

Example for VLAN 10:

```bash
interface fastEthernet0/1
 switchport mode access
 switchport access vlan 10
```

Example for VLAN 20:

```bash
interface fastEthernet0/2
 switchport mode access
 switchport access vlan 20
```

Example for VLAN 30:

```bash
interface fastEthernet0/3
 switchport mode access
 switchport access vlan 30
```

---

## Configure Trunk Ports

```bash
interface gigabitEthernet0/1
 switchport mode trunk
```

Configure trunking on:
- Switch-to-Switch links
- Switch-to-Router link

---

# 💻 End Device Configuration

Assign IP addresses manually.

| Device | IP Address | Subnet Mask | Default Gateway |
|----------|----------------|----------------|----------------|
| PC4 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| PC5 | 192.168.10.12 | 255.255.255.0 | 192.168.10.1 |
| PC0 | 192.168.20.11 | 255.255.255.0 | 192.168.20.1 |
| PC1 | 192.168.20.12 | 255.255.255.0 | 192.168.20.1 |
| PC2 | 192.168.30.11 | 255.255.255.0 | 192.168.30.1 |
| Server | 192.168.30.12 | 255.255.255.0 | 192.168.30.1 |

---

# 🔍 Verification Commands

## Verify VLANs

```bash
show vlan brief
```

---

## Verify Trunk Ports

```bash
show interfaces trunk
```

---

## Verify Router Subinterfaces

```bash
show ip interface brief
```

---

## Verify Router Configuration

```bash
show running-config
```

---

## Test Connectivity

From any PC:

```text
ping 192.168.20.11
ping 192.168.30.12
ping 192.168.10.12
```

Successful replies indicate that inter-VLAN routing is functioning correctly.

---

# 📚 Key Concepts Covered

- Virtual Local Area Networks (VLANs)
- Access Ports
- Trunk Ports
- IEEE 802.1Q Encapsulation
- Router-on-a-Stick (ROAS)
- Router Subinterfaces
- Inter-VLAN Routing
- IP Addressing and Default Gateways
- End-to-End Connectivity Verification

---

# 📝 Common Cisco IOS Commands

| Command | Description |
|----------|-------------|
| `vlan 10` | Create a VLAN |
| `switchport access vlan 10` | Assign an access port to a VLAN |
| `switchport mode trunk` | Configure a trunk port |
| `encapsulation dot1Q 10` | Enable 802.1Q tagging on a router subinterface |
| `ip address` | Assign an IP address |
| `show vlan brief` | Display configured VLANs |
| `show interfaces trunk` | Verify trunk links |
| `show ip interface brief` | Display router interface status |
| `ping` | Test connectivity |
| `copy running-config startup-config` | Save the configuration |

---

# 💡 Key Takeaways

- VLANs logically separate devices into different broadcast domains.
- Trunk links transport traffic for multiple VLANs using IEEE 802.1Q tagging.
- Router-on-a-Stick uses a single physical router interface with multiple subinterfaces to route traffic between VLANs.
- Each VLAN requires a unique default gateway configured on a router subinterface.
- Proper VLAN assignment, trunk configuration, and gateway settings are essential for successful inter-VLAN communication.

---

# 🎓 CCNA Topics Covered

- VLAN Configuration
- Access and Trunk Ports
- IEEE 802.1Q
- Router-on-a-Stick (ROAS)
- Inter-VLAN Routing
- Router Subinterfaces
- IP Addressing
- Connectivity Testing and Troubleshooting

---

# 👨‍💻 Author

**Danush Kalyan**

This Cisco Packet Tracer lab was created as part of CCNA practice to develop hands-on skills in VLAN implementation, trunking, and inter-VLAN routing using the Router-on-a-Stick method.