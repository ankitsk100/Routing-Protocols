# EIGRP Routing Lab (4 Routers) – Cisco Packet Tracer

This project demonstrates dynamic routing using **EIGRP (AS 30)** across four Cisco routers in a redundant (diamond) WAN topology. Two LANs (192.168.1.0/24 and 192.168.2.0/24) communicate through EIGRP-learned routes, providing multiple paths for resilience.

---

## Network Topology

![Topology](docs/topology.png)

---

## Objectives

- Build a 4-router redundant topology with two LANs.
- Configure IP addressing on LAN and WAN (/30) links.
- Configure **EIGRP AS 30** on all routers to advertise directly connected networks.
- Verify routing adjacency, learned routes, and end-to-end connectivity.

---

## Technologies Used

- Cisco Packet Tracer
- Cisco 2911 Routers (R1, R2, R3, R4)
- Cisco 2960 Switches
- EIGRP (Classic) Autonomous System 30

---

## IP Addressing Plan

### LAN 1 (Left Site) – 192.168.1.0/24
| Device | Interface | IP Address | Mask | Default GW |
|---|---|---:|---:|---:|
| R1 | LAN | 192.168.1.1 | 255.255.255.0 | - |
| PC0 | NIC | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC1 | NIC | 192.168.1.20 | 255.255.255.0 | 192.168.1.1 |
| PC2 | NIC | 192.168.1.30 | 255.255.255.0 | 192.168.1.1 |

### LAN 2 (Right Site) – 192.168.2.0/24
| Device | Interface | IP Address | Mask | Default GW |
|---|---|---:|---:|---:|
| R3 | LAN | 192.168.2.1 | 255.255.255.0 | - |
| PC3 | NIC | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 |
| PC4 | NIC | 192.168.2.20 | 255.255.255.0 | 192.168.2.1 |
| PC5 | NIC | 192.168.2.30 | 255.255.255.0 | 192.168.2.1 |

---

## WAN Links (/30)

### R1 ↔ R2 : 10.10.10.0/30
| Router | IP |
|---|---:|
| R1 | 10.10.10.1 |
| R2 | 10.10.10.2 |

### R1 ↔ R4 : 10.10.10.4/30
| Router | IP |
|---|---:|
| R1 | 10.10.10.5 |
| R4 | 10.10.10.6 |

### R2 ↔ R3 : 10.10.10.8/30
| Router | IP |
|---|---:|
| R2 | 10.10.10.9 |
| R3 | 10.10.10.10 |

### R4 ↔ R3 : 10.10.10.12/30
| Router | IP |
|---|---:|
| R3 | 10.10.10.13 |
| R4 | 10.10.10.14 |

---

## EIGRP Configuration (AS 30)

EIGRP is enabled on each router using:
- `router eigrp 30`
- `network` statements with wildcard masks:
  - /24 LANs: `0.0.0.255`
  - /30 WANs: `0.0.0.3`

Configuration files are located in:
- `configs/routers/R1-eigrp.txt`
- `configs/routers/R2-eigrp.txt`
- `configs/routers/R3-eigrp.txt`
- `configs/routers/R4-eigrp.txt`

---

## Verification & Testing

### Router Verification Commands
```bash
show ip eigrp neighbors
show ip route eigrp
show ip protocols
show ip interface brief
