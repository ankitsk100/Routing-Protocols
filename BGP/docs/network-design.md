# 📐 Network Design Documentation

## Overview

This lab simulates a real-world External BGP (eBGP) scenario between three Autonomous Systems:

- AS20 (Enterprise Network A)
- AS35 (Transit ISP)
- AS50 (Enterprise Network B)

AS35 functions as a transit provider allowing inter-AS communication.

---

## Logical Flow

Enterprise A (AS20)
        ↓
Transit ISP (AS35)
        ↓
Enterprise B (AS50)

---

## IP Addressing Plan

### LAN Networks

- AS20 LAN: 192.168.1.0/24
- AS50 LAN: 192.168.2.0/24

### WAN Links

- R1–R2: 10.10.10.0/30
- R2–R3: 20.20.20.0/30

---

## BGP Peering Design

| Router | ASN | Neighbor | Remote ASN |
|--------|-----|----------|------------|
| R1 | 20 | 10.10.10.2 | 35 |
| R2 | 35 | 10.10.10.1 | 20 |
| R2 | 35 | 20.20.20.2 | 50 |
| R3 | 50 | 20.20.20.1 | 35 |

---

## Routing Logic

- Each router advertises its directly connected networks.
- AS35 propagates routes between AS20 and AS50.
- No static routes used.
- Full dynamic routing via eBGP.

---

## Learning Outcome

- Understanding of eBGP fundamentals
- Multi-AS routing behavior
- Transit AS operation
- Route advertisement mechanics
- BGP verification and troubleshooting
