# Multi-Area OSPF (Packet Tracer)

This project demonstrates a **Multi-Area OSPF** design (Area 0 backbone + non-backbone areas) using Cisco routers in **Packet Tracer**.

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
