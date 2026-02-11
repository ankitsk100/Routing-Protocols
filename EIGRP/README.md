# EIGRP Routing Lab (4 Routers) – Cisco Packet Tracer

This project demonstrates dynamic routing using **EIGRP (AS 30)** across four Cisco routers in a redundant (diamond) WAN topology. Two LANs (192.168.1.0/24 and 192.168.2.0/24) communicate through EIGRP-learned routes, providing multiple paths for resilience.

---

# 📚 What is EIGRP?

**EIGRP (Enhanced Interior Gateway Routing Protocol)** is an advanced distance-vector routing protocol developed by Cisco.

It is used for routing **within a single Autonomous System (AS)** and is commonly deployed in enterprise networks.

EIGRP combines features of:

- Distance Vector protocols (like RIP)
- Link-State protocols (like OSPF)

Because of this, it is often called a **Hybrid Routing Protocol**.

---

## 🏢 Where is EIGRP Used?

EIGRP is used:

- Inside enterprise networks
- Between branch offices
- In campus networks
- In internal infrastructure routing

It is not typically used between ISPs (that is BGP’s role).

---

## ⚙️ How EIGRP Works

EIGRP uses:

- **DUAL Algorithm (Diffusing Update Algorithm)**  
- Maintains:
  - Neighbor Table
  - Topology Table
  - Routing Table

EIGRP calculates the best path based on a composite metric including:

- Bandwidth
- Delay
- Reliability
- Load
- MTU

By default, bandwidth and delay are used.

---

## 🔑 Key Features of EIGRP

- Fast convergence
- Loop-free routing
- Supports VLSM and CIDR
- Uses multicast (224.0.0.10)
- Supports unequal-cost load balancing
- Low bandwidth usage

---

## 📊 EIGRP Administrative Distance

| Route Type | Administrative Distance |
|------------|-------------------------|
| Internal EIGRP | 90 |
| External EIGRP | 170 |

---

## 🔄 EIGRP Terminology

- **Successor** → Best path to a destination
- **Feasible Successor** → Backup path
- **Feasibility Condition** → Loop prevention rule
- **DUAL** → Algorithm used for route calculation

---

## 🧠 Why This Lab is Important

This lab demonstrates:

- Dynamic routing inside an enterprise
- Neighbor relationship establishment
- Automatic route advertisement
- Convergence behavior
- Internal AS routing design

Understanding EIGRP is essential for:

- Enterprise Network Engineers
- NOC Engineers
- Infrastructure Engineers
- OT Network Engineers

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
