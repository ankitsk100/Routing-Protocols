# Multi-Area OSPF (Packet Tracer)

This project demonstrates a **Multi-Area OSPF** design (Area 0 backbone + non-backbone areas) using Cisco routers in **Packet Tracer**.

---

# 📚 What is Multi-Area OSPF?

**OSPF (Open Shortest Path First)** is a link-state Interior Gateway Protocol (IGP) used for routing within a single Autonomous System.

**Multi-Area OSPF** is a hierarchical design of OSPF where the network is divided into multiple areas to improve scalability, performance, and routing efficiency.

Instead of placing all routers in one large OSPF area, the network is segmented into smaller logical areas connected through a backbone area.

---

## 🏗 OSPF Hierarchical Structure

Multi-Area OSPF uses a two-level hierarchy:

### 1️⃣ Backbone Area (Area 0)
- The core of the OSPF network
- All other areas must connect to Area 0
- Responsible for inter-area communication

### 2️⃣ Non-Backbone Areas (Area 1, Area 2, etc.)
- Contain internal routers
- Reduce routing table size
- Limit LSA flooding

---

## 🔄 How Multi-Area OSPF Works

1️⃣ Routers within the same area exchange link-state information.

2️⃣ Each router builds a **Link-State Database (LSDB)** for its area.

3️⃣ Using the **Shortest Path First (SPF) algorithm (Dijkstra's Algorithm)**, routers calculate the best path.

4️⃣ Area Border Routers (ABRs):
   - Connect one area to Area 0
   - Summarize routes between areas
   - Reduce routing overhead

5️⃣ Inter-area routes are advertised through the backbone (Area 0).

---

## 🔑 Key Components

- **Internal Router** → All interfaces in the same area  
- **Backbone Router** → Connected to Area 0  
- **Area Border Router (ABR)** → Connects multiple areas  
- **Link-State Advertisements (LSAs)** → Used to share topology information  

---

## 🎯 Why Multi-Area OSPF is Used

- Improves scalability in large networks
- Reduces CPU usage
- Minimizes routing table size
- Limits SPF recalculation scope
- Enhances network stability

---

## 🧠 In Simple Terms

Single-Area OSPF works for small networks.

Multi-Area OSPF is designed for large enterprise or campus networks where dividing the network into logical areas improves performance and management.
---

## Topology

![Topology](docs/topology.png)

## What’s Included
- Packet Tracer lab file (`.pkt`)
- Router configuration files (per-router)
- OSPF area design notes + addressing plan
- Verification commands and sample outputs

## Folder Structure
- `docs/` → topology image + design docs
- `packet-tracer/` → `.pkt` file and lab notes
- `configs/routers/` → router configs (R1, R2, ...)
- `validation/` → show/debug commands + expected results

## How to Use
1. Download the `.pkt` file from `packet-tracer/`
2. Open it in Cisco Packet Tracer
3. Compare running config with files in `configs/routers/`
4. Run verification commands from `validation/verification-commands.md`

## OSPF Notes
- Area 0 is the backbone
- ABRs connect non-backbone areas to Area 0
- Design aims for scalable routing and reduced LSA flooding per area
