# Addressing Plan

> Update the IPs below to match your actual topology.

## Router-to-Router Links
| Link | Subnet | R-A IP | R-B IP | Area |
|------|--------|--------|--------|------|
| R1-R2 | 10.0.12.0/30 | 10.0.12.1 | 10.0.12.2 | Area 0 |
| R2-R3 | 10.0.23.0/30 | 10.0.23.2 | 10.0.23.3 | Area 10 |
| R2-R4 | 10.0.24.0/30 | 10.0.24.2 | 10.0.24.4 | Area 20 |

## LAN Networks
| Site | Subnet | Gateway | Area |
|------|--------|---------|------|
| R1 LAN | 192.168.1.0/24 | 192.168.1.1 | Area 0 |
| R3 LAN | 192.168.3.0/24 | 192.168.3.1 | Area 10 |
| R4 LAN | 192.168.4.0/24 | 192.168.4.1 | Area 20 |
