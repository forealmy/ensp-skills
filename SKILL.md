---
name: ensp
description: Always use when user asks to create, generate, or design a network topology diagram for eNSP (Enterprise Network Simulation Platform), or mentions creating eNSP topologies, network simulations with Huawei devices (AR routers, S5700 switches, PC, Cloud, etc.).
---

# eNSP Topology Skill

Generate eNSP (Enterprise Network Simulation Platform) topology files as native `.topo` files that can be opened directly in eNSP.

## How to create a topology

1. **Parse user's request** to identify:
   - Network devices (routers, switches, PCs, Cloud, etc.)
   - Connections between devices
   - Optional: text labels, area boxes

2. **Generate UUIDs** for each device using a valid UUID v4 format

3. **Calculate layout coordinates** for devices using auto-layout algorithm

4. **Build the .topo XML** following the format in `references/topo-reference.md`

5. **Write the file** to current directory using Write tool

6. **Open the result** - print the file path so user can open it in eNSP

## Output format

Always output a `.topo` file. The user will open it in eNSP for simulation.

Example filenames:
- `simple-network.topo`
- `ospf-topology.topo`
- `campus-network.topo`

## Device types supported

| Model | Description | Common slot config |
|-------|-------------|-------------------|
| AR1220 | Router | 2GE + 8Ethernet + Serial |
| AR2220 | Router | 2GE + Serial |
| S5700 | Switch | 24GE |
| PC | PC | 1GE |
| Laptop | Laptop | 1GE |
| MCS | Multicast Server | 1Ethernet |
| Cloud | Cloud/BNI | Ethernet interfaces |
| AC6005 | Wireless AC | 8GE |
| AP6050 | Wireless AP | 2GE |
| STA | Wireless Station | Wireless |

## Connection types

| Type | Description |
|------|-------------|
| Copper | Ethernet cable |
| Serial | Serial cable |
| Auto | Auto-detect |

## Layout algorithm

Use a simple grid-based auto-layout:

```
Grid spacing: 200px horizontal, 150px vertical
Device size: ~80x60px
Start position: (100, 100)

For each row:
  - Place devices horizontally with 200px gap
  - Move to next row when reaching canvas width (~1200px)
```

Adjust positions based on device types and connections to create logical groupings.

## Adding text labels (txttips)

Common labels for network diagrams:
- Loopback addresses: `Loopback0:10.0.1.1/24`
- Network segments: `10.0.12.0/24`
- Area labels: `Area0`, `Area1`, `AS 64512`
- Device roles: `Core Layer`, `Access Layer`

## Adding area boxes (shapes)

Use type="1" shapes with appropriate colors to group devices:
- Same area devices in one rectangle
- Different colors for different areas/zones

## File naming

- Use lowercase with hyphens
- Descriptive name based on topology purpose
- End with `.topo` extension

## Opening the result

After writing the file, print the absolute path:
```
Topology saved to: C:\path\to\topology.topo
Please open this file in eNSP to view and simulate.
```

## XML format reference

Consult `references/topo-reference.md` for complete XML structure including:
- Device XML format with slots and interfaces
- Line XML format with interfacePair details
- Shape XML format for area boxes
- Txttip XML format for text annotations
