# OSPF Triangle Topology (3 Routers, 3 LANs) - Packet Tracer Lab

This project demonstrates a basic multi-router OSPF deployment (Area 0) connecting three LANs using a triangular WAN design. All routers form OSPF neighbor adjacencies and advertise their directly connected networks.

## Topology

![Topology](docs/topology.png)

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
