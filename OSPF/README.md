# OSPF Triangle Topology (3 Routers, 3 LANs) - Packet Tracer Lab

This project demonstrates a basic multi-router OSPF deployment (Area 0) connecting three LANs using a triangular WAN design. All routers form OSPF neighbor adjacencies and advertise their directly connected networks.

---
## Topology

![Topology](docs/topology.png)

# 📚 What is OSPF?

**OSPF (Open Shortest Path First)** is a link-state Interior Gateway Protocol (IGP) used for dynamic routing within a single Autonomous System (AS).

It is an open standard protocol widely used in enterprise and service provider networks for fast, scalable, and reliable routing.

Unlike distance-vector protocols (like RIP), OSPF builds a complete map of the network topology before calculating routes.

---

## 🏗 What is Single-Area OSPF?

In Single-Area OSPF, all routers belong to the same OSPF area, typically **Area 0**.

This design is suitable for:

- Small to medium-sized networks
- Lab environments
- Simple enterprise networks

All routers share the same link-state database and participate equally in routing decisions.

---

## 🔄 How OSPF Works

1️⃣ Routers discover neighbors using **Hello packets**.

2️⃣ Once neighbors are established, routers exchange **Link-State Advertisements (LSAs)**.

3️⃣ Each router builds a **Link-State Database (LSDB)** containing the full network topology.

4️⃣ OSPF runs the **Shortest Path First (SPF) algorithm (Dijkstra's Algorithm)** to calculate the best path to each destination.

5️⃣ The best routes are installed into the routing table.

---

## 🔑 Key Features of OSPF

- Link-State routing protocol
- Uses cost as metric (based on bandwidth)
- Fast convergence
- Supports VLSM and CIDR
- Uses multicast addresses:
  - 224.0.0.5 (All OSPF Routers)
  - 224.0.0.6 (DR/BDR Routers)

---

## 📊 OSPF Metric (Cost)

OSPF determines the best path using **cost**, calculated as:

```
Cost = Reference Bandwidth / Interface Bandwidth
```

Lower cost = Preferred path.

---

## 🔍 Important OSPF Concepts

- **Neighbor Adjacency** → Routers form relationships
- **DR (Designated Router)** → Reduces LSA traffic on multi-access networks
- **BDR (Backup DR)** → Backup for DR
- **LSA (Link-State Advertisement)** → Topology information exchange
- **SPF Algorithm** → Calculates shortest path

---

## 🎯 Why OSPF is Used

- Faster convergence than RIP
- Better scalability
- Efficient routing updates
- Suitable for enterprise networks

---

## 🧠 In Simple Terms

OSPF allows routers to share full topology information, calculate the shortest path using SPF, and dynamically update routing tables when changes occur.

## Network Design

### LAN Networks
| Site | LAN Subnet | Default Gateway |
|------|------------|-----------------|
| R1 LAN | 192.168.1.0/24 | 192.168.1.1 |
| R2 LAN | 192.168.2.0/24 | 192.168.2.1 |
| R3 LAN | 192.168.3.0/24 | 192.168.3.1 |

### WAN / Point-to-Point Links (/30)
| Link | Subnet | Router IPs |
|------|--------|------------|
| R1 ↔ R3 | 10.10.10.0/30 | R1: 10.10.10.1, R3: 10.10.10.2 |
| R3 ↔ R2 | 20.20.20.0/30 | R3: 20.20.20.1, R2: 20.20.20.2 |
| R1 ↔ R2 | 30.30.30.0/30 | R1: 30.30.30.1, R2: 30.30.30.2 |

## Routing Protocol

- Protocol: OSPFv2
- Process ID: 11
- Area: 0 (backbone)
- Router IDs:
  - R1: 1.1.1.1
  - R2: 2.2.2.2
  - R3: 3.3.3.3

All LAN + WAN networks are advertised in Area 0.

## Configuration Files

Router configurations are stored here:

- `configs/routers/R1-OSPF11.txt`
- `configs/routers/R2-OSPF11.txt`
- `configs/routers/R3-OSPF11.txt`

## Verification (Must-Run Commands)

Run these on each router:

```bash
show ip ospf neighbor
show ip route ospf
show ip protocols
show ip ospf interface brief
