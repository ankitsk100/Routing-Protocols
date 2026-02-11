# OSPF Design (Multi-Area)

## Areas
- **Area 0 (Backbone):** Core transit area; must connect all other areas.
- **Area 10:** Branch / distribution area
- **Area 20:** Another branch / distribution area

## Roles
- **ABR (Area Border Router):** Router with interfaces in Area 0 and a non-backbone area.
- **Internal Router:** All interfaces are within a single area.

## Why Multi-Area OSPF?
- Smaller LSDB per area
- Reduced LSA flooding
- Better scalability for larger networks

## Design Checklist
- Non-backbone areas must connect to Area 0 (directly via ABR)
- Unique router-id per router
- Correct wildcard masks in `network` statements
