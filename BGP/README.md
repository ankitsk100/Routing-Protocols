# 🌐 Multi-AS eBGP Configuration Lab

## 📌 Project Overview

This project demonstrates External BGP (eBGP) configuration between three Autonomous Systems:

- **AS 20** (Enterprise Site A)
- **AS 35** (Transit ISP)
- **AS 50** (Enterprise Site B)

The objective is to establish BGP neighbor relationships and advertise directly connected networks across different AS domains.

---

## 📚 What is BGP?

The **Border Gateway Protocol (BGP)** is a path-vector routing protocol used to exchange routing information between different Autonomous Systems (AS) on the Internet.

BGP is the protocol that makes the Internet work.

Unlike interior routing protocols such as OSPF or EIGRP, which operate within a single organization, BGP is designed for inter-domain routing between multiple organizations or service providers.

---

## 🏢 What is an Autonomous System (AS)?

An **Autonomous System (AS)** is a collection of IP networks under a single administrative control that presents a common routing policy to the Internet.

Each AS is identified by a unique **Autonomous System Number (ASN)**.

In this project:

- AS 20 → Enterprise Network A
- AS 35 → Transit ISP
- AS 50 → Enterprise Network B

---

## 🔄 Types of BGP

There are two main types of BGP:

### 1️⃣ eBGP (External BGP)
- Runs between different Autonomous Systems.
- Used for Internet and ISP communication.
- Implemented in this project.

### 2️⃣ iBGP (Internal BGP)
- Runs within the same Autonomous System.
- Used inside large enterprise or ISP networks.

---

## ⚙️ How BGP Works

BGP:
- Establishes neighbor relationships
- Exchanges routing updates
- Uses path attributes (AS Path, Local Preference, MED, etc.)
- Selects the best path based on policy

It is considered a **policy-based routing protocol** rather than just a shortest-path protocol.

---

## 🌍 Why BGP is Important

- Powers global Internet routing
- Allows multi-homing to multiple ISPs
- Provides routing policy control
- Enables large-scale scalable routing

---

## 🧠 Why This Lab is Important

This lab demonstrates:

- eBGP peering between multiple AS domains
- Route advertisement using network statements
- Transit AS behavior
- Real-world ISP simulation

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
