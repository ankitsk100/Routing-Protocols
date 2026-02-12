

# Routing Protocol Comparison Guide

This document provides a concise comparison of major routing protocols:

- RIP
- EIGRP
- OSPF
- Multi-Area OSPF
- BGP

This guide is useful for networking labs and enterprise design understanding.

---

## 1. RIP (Routing Information Protocol)

**Type:** Distance Vector (IGP)  
**Metric:** Hop Count (Maximum 15 hops)  
**Algorithm:** Bellman-Ford  

### Key Characteristics
- Simple configuration
- Sends full routing updates every 30 seconds
- Slow convergence
- Not scalable for large networks

### Best Use Case
Small networks and lab environments.

### Summary
RIP is a basic distance vector protocol that uses hop count as its metric. It is simple but limited to 15 hops, making it unsuitable for large enterprise networks.

---

## 2. EIGRP (Enhanced Interior Gateway Routing Protocol)

**Type:** Hybrid (Advanced Distance Vector IGP)  
**Metric:** Bandwidth + Delay (Composite Metric)  
**Algorithm:** DUAL  

### Key Characteristics
- Fast convergence
- Sends partial updates
- Maintains neighbor and topology tables
- Originally Cisco proprietary

### Best Use Case
Medium to large enterprise networks, especially Cisco-based environments.

### Summary
EIGRP is a hybrid routing protocol that uses the DUAL algorithm to achieve fast convergence and efficient bandwidth usage.

---

## 3. OSPF (Open Shortest Path First - Single Area)

**Type:** Link-State (IGP)  
**Metric:** Cost (based on bandwidth)  
**Algorithm:** Dijkstra SPF  

### Key Characteristics
- Fast convergence
- Uses Link State Advertisements (LSAs)
- All routers maintain full topology database
- Open standard protocol

### Best Use Case
Enterprise networks requiring scalability and multi-vendor support.

### Summary
OSPF is a link-state protocol that calculates the shortest path using SPF algorithm and is widely used in enterprise networks.

---

## 4. Multi-Area OSPF

**Type:** Hierarchical Link-State (IGP)  
**Metric:** Cost  
**Backbone Area:** Area 0 (Mandatory)  

### Key Characteristics
- Divides network into multiple areas
- Reduces routing table size
- Limits LSA flooding
- Uses Area Border Routers (ABR)

### Why Use Multi-Area?
Improves scalability and reduces CPU and memory utilization in large networks.

### Summary
Multi-Area OSPF enhances scalability by dividing large networks into smaller areas connected through Area 0, reducing routing overhead.

---

## 5. BGP (Border Gateway Protocol)

**Type:** Path Vector (EGP)  
**Metric:** Path Attributes (AS-PATH, Local Preference, MED, etc.)  
**Used Between:** Autonomous Systems  

### Key Characteristics
- Policy-based routing
- Highly scalable
- Slower convergence than IGPs
- Backbone of the Internet

### Best Use Case
ISP networks, multi-homed enterprises, and inter-AS routing.

### Summary
BGP is a path vector protocol used between autonomous systems. It selects routes based on policies and path attributes and forms the backbone of the Internet.

---

# Quick Comparison Table

| Feature | RIP | EIGRP | OSPF | Multi-Area OSPF | BGP |
|----------|------|--------|-------|----------------|------|
| Protocol Type | Distance Vector | Hybrid | Link-State | Hierarchical Link-State | Path Vector |
| Metric | Hop Count | Bandwidth + Delay | Cost | Cost | Path Attributes |
| Convergence | Slow | Fast | Fast | Very Scalable | Slower |
| Scalability | Low | Medium | High | Very High | Extremely High |
| Primary Use | Small LAN | Enterprise (Cisco) | Enterprise | Large Enterprise | Internet / ISP |

---

# Final Summary

- RIP is simple but outdated.
- EIGRP offers fast convergence in Cisco environments.
- OSPF is an open-standard scalable enterprise protocol.
- Multi-Area OSPF improves scalability through hierarchical design.
- BGP is used for inter-AS routing and powers the global Internet.

---

# Routing Concepts: Metric, Convergence, and Protocol Types

This document explains three core routing concepts in simple terms:
- Metric
- Convergence
- Routing Protocol Types
---
## 1. Metric
### Definition
A **metric** is a value used by a routing protocol to choose the best path to a destination network.
Lower metric = Better path.
### Examples by Protocol
| Protocol | Metric Used |
|-----------|------------|
| RIP | Hop Count |
| EIGRP | Bandwidth + Delay |
| OSPF | Cost (based on bandwidth) |
| BGP | Path Attributes (AS-PATH, Local Preference, etc.) |
### Interview Summary
A metric is the numerical value used by routing protocols to select the most efficient route.
---
## 2. Convergence
### Definition
**Convergence** is the time it takes for all routers in a network to update their routing tables after a topology change.
Example:  
If a link fails, routers must detect the failure and calculate a new best path.
Faster convergence = More stable network.
### Convergence Comparison
| Protocol | Speed |
|-----------|--------|
| RIP | Slow |
| EIGRP | Fast |
| OSPF | Fast |
| Multi-Area OSPF | Very Scalable |
| BGP | Slower but Stable |
### Summary
Convergence is the time required for all routers to have consistent and updated routing information after a network change.
---
## 3. Routing Protocol Types
Routing protocols are categorized based on how they share routing information.
### Distance Vector
- Sends routing table to neighbors
- Simpler design
- Slower convergence
Example: RIP
---
### Link-State
- Builds full network topology map
- Uses SPF algorithm
- Faster and scalable
Example: OSPF
---
### Hybrid
- Combines features of distance vector and link-state
- Fast convergence
- Efficient updates

Example: EIGRP
---
### Path Vector
- Used between Autonomous Systems
- Uses routing policies and attributes
Example: BGP
---
## Final Summary
- Metric = Value used to choose best route  
- Convergence = Time to update routes after change  
- Protocol Types = Distance Vector, Link-State, Hybrid, Path Vector  

This knowledge is fundamental for enterprise routing design.
