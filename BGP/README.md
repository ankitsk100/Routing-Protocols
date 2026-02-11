# 🌐 Multi-AS eBGP Configuration Lab

## 📌 Project Overview

This project demonstrates External BGP (eBGP) configuration between three Autonomous Systems:

- **AS 20** (Enterprise Site A)
- **AS 35** (Transit ISP)
- **AS 50** (Enterprise Site B)

The objective is to establish BGP neighbor relationships and advertise directly connected networks across different AS domains.

---

## 🗺 Network Topology

![BGP Multi-AS Topology](docs/topology.png)

### Addressing Scheme

| Segment | Network |
|---------|----------|
| AS20 LAN | 192.168.1.0/24 |
| R1–R2 Link | 10.10.10.0/30 |
| R2–R3 Link | 20.20.20.0/30 |
| AS50 LAN | 192.168.2.0/24 |

---

## 🏗 Architecture

- R1 → AS 20
- R2 → AS 35 (Transit ISP)
- R3 → AS 50
- eBGP sessions between different AS numbers
- End-to-end reachability via BGP routing

---

## 🔧 Devices Used

- Cisco 2911 Routers
- Cisco 2960 Switches
- End hosts for validation
- Cisco Packet Tracer

---

## 🚀 Configuration Summary

- eBGP Peering:
  - AS20 ↔ AS35
  - AS35 ↔ AS50
- Directly connected networks advertised using `network` statements
- Route propagation through transit AS35

---

## 🔍 Verification Commands

```
show ip bgp summary
show ip bgp
show ip route
show ip route bgp
```

---

## 🎯 Expected Result

- PCs in **192.168.1.0/24**
- PCs in **192.168.2.0/24**

Should successfully ping each other via BGP routing through AS35.

---

## 📂 Project Structure

```
BGP-Multi-AS-Lab/
│
├── README.md
├── docs/
│   └── topology.png
├── configs/
│   ├── routers/
│   └── verification/
└── packet-tracer/
```

---

## 👨‍💻 Author

**Ankit Kuttarmare**  
Master of Science in Computer Science  
Focus: Networking | Infrastructure | Network Engineering
