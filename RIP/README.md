# RIP Routing Lab (3 Routers) – Cisco Packet Tracer

This project demonstrates dynamic routing using **RIPv2** across three Cisco routers. Two LANs (192.168.1.0/24 and 192.168.2.0/24) are interconnected through a routed WAN using /30 point-to-point links.

---

---

# 📚 What is RIP?

**RIP (Routing Information Protocol)** is one of the oldest distance-vector routing protocols used for dynamic routing within a network.

It is designed for small networks and uses hop count as its routing metric.

RIP automatically shares routing information between routers, allowing them to learn about remote networks without manually configuring static routes.

---

## 🏗 What is Distance-Vector Routing?

Distance-vector protocols:

- Share routing tables with directly connected neighbors
- Periodically update routes
- Select the best path based on a simple metric

In RIP, the metric used is **hop count**.

---

## 🔢 RIP Metric (Hop Count)

- Each router hop adds +1 to the hop count.
- The maximum hop count allowed is **15**.
- A hop count of **16 is considered unreachable**.

Lower hop count = Better route.

---

## 🔄 How RIP Works

1️⃣ Routers send their full routing table to neighbors every 30 seconds.

2️⃣ Neighbor routers update their routing tables based on received information.

3️⃣ If a better route (lower hop count) is found, it replaces the existing route.

4️⃣ RIP uses loop-prevention mechanisms such as:
   - Split Horizon
   - Route Poisoning
   - Hold-down Timers

---

## 📦 RIP Versions

### RIP Version 1 (RIPv1)
- Classful routing
- Does not support VLSM
- Broadcast updates

### RIP Version 2 (RIPv2)
- Classless routing
- Supports VLSM and CIDR
- Uses multicast address 224.0.0.9
- Supports authentication

Most modern labs use **RIPv2**.

---

## 🔑 Key Characteristics of RIP

- Simple configuration
- Easy to understand
- Suitable for small networks
- Slow convergence
- Limited scalability

---

## ⚠ Limitations of RIP

- Maximum 15 hops
- Slow convergence compared to OSPF and EIGRP
- Not suitable for large enterprise networks
- Less efficient bandwidth usage

---

## 🎯 When is RIP Used?

RIP is mainly used for:

- Small networks
- Educational labs
- Basic routing demonstrations

It is rarely used in modern enterprise environments.

---

## 🧠 In Simple Terms

RIP allows routers to share routes with neighbors and choose paths based on the fewest number of hops, making it simple but limited in scalability.


## Network Topology

![Topology](docs/topology.png)

---

## Objectives

- Build a 3-router topology with two LANs.
- Configure IP addressing on LAN and WAN interfaces.
- Configure **RIPv2** on all routers to advertise directly connected networks.
- Verify end-to-end connectivity between LAN hosts using RIP-learned routes.

---

## Technologies Used

- Cisco Packet Tracer
- Cisco 2911 Routers (R1, R2, R3)
- Cisco 2960 Switches
- RIP v2 (Dynamic Routing)

---

## IP Addressing Plan

### LAN 1 (Left Site) – 192.168.1.0/24
| Device | Interface | IP Address | Subnet Mask | Default GW |
|---|---|---:|---:|---:|
| R1 | LAN Interface | 192.168.1.1 | 255.255.255.0 | - |
| PC0 | NIC | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC1 | NIC | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| PC2 | NIC | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 |

### WAN Link 1 – 10.10.10.0/30 (R1 ↔ R2)
| Device | Interface | IP Address | Subnet Mask |
|---|---|---:|---:|
| R1 | to R2 | 10.10.10.1 | 255.255.255.252 |
| R2 | to R1 | 10.10.10.2 | 255.255.255.252 |

### WAN Link 2 – 20.20.20.0/30 (R2 ↔ R3)
| Device | Interface | IP Address | Subnet Mask |
|---|---|---:|---:|
| R2 | to R3 | 20.20.20.1 | 255.255.255.252 |
| R3 | to R2 | 20.20.20.2 | 255.255.255.252 |

### LAN 2 (Right Site) – 192.168.2.0/24
| Device | Interface | IP Address | Subnet Mask | Default GW |
|---|---|---:|---:|---:|
| R3 | LAN Interface | 192.168.2.1 | 255.255.255.0 | - |
| PC3 | NIC | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 |
| PC4 | NIC | 192.168.2.11 | 255.255.255.0 | 192.168.2.1 |
| PC5 | NIC | 192.168.2.12 | 255.255.255.0 | 192.168.2.1 |

---

## RIP Configuration (RIPv2)

RIPv2 is configured on all routers to advertise directly connected networks.

Key settings:
- `version 2`
- `no auto-summary`
- `network ...` statements for LAN and WAN subnets

Router configs are provided in:
- `configs/routers/R1-rip.txt`
- `configs/routers/R2-rip.txt`
- `configs/routers/R3-rip.txt`

---

## Verification & Testing

Run these commands on routers:

### 1) Check RIP neighbors and learned routes
```bash
show ip route rip
show ip protocols
