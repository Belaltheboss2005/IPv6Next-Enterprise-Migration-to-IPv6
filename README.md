# IPv6Next – Enterprise Migration to IPv6

## Scenario

A mid-sized enterprise is transitioning to IPv6. The team is responsible for designing and testing a **dual-stack architecture** supporting both IPv4 and IPv6.

---

The project focuses on transitioning a mid-sized enterprise network from IPv4 to a dual-stack IPv4/IPv6 architecture. The team designed and simulated the network in Cisco Packet Tracer, implementing OSPFv3 for IPv6 and OSPF for IPv4. A structured addressing scheme was applied, using /30 for router links and /24 for LANs, with consistent IPv6 subnets.

---

## Functionality

* Implement dual-stack addressing.
* Route IPv6 traffic using OSPFv3.

---

## Implementation

### Design and Simulation

* Simulated a hybrid IPv4/IPv6 network in **Packet Tracer**.
* Configured routing and IPv6 addressing strategies.

---

## Addressing Scheme

### Point-to-Point Links (Router-to-Router)

| Link    | IPv4 Address | IPv6 Address            |
| ------- | ------------ | ----------------------- |
| R1 ↔ R2 | 10.0.0.1/30  | 2001\:db8\:acad:1::/64  |
| R1 ↔ R3 | 10.0.0.5/30  | 2001\:db8\:acad:2::/64  |
| R2 ↔ R4 | 10.0.0.9/30  | 2001\:db8\:acad:3::/64  |
| R3 ↔ R4 | 10.0.0.29/30 | 2001\:db8\:acad:4::/64  |
| R3 ↔ R5 | 10.0.0.13/30 | 2001\:db8\:acad:5::/64  |
| R4 ↔ R6 | 10.0.0.17/30 | 2001\:db8\:acad:6::/64  |
| R5 ↔ R6 | 10.0.0.33/30 | 2001\:db8\:acad:7::/64  |
| R5 ↔ R7 | 10.0.0.21/30 | 2001\:db8\:acad:8::/64  |
| R6 ↔ R8 | 10.0.0.25/30 | 2001\:db8\:acad:9::/64  |
| R7 ↔ R8 | 10.0.0.37/30 | 2001\:db8\:acad\:A::/64 |

### LAN Segments (Router ↔ Switch ↔ PCs)

| Router | IPv4 Subnet    | IPv6 Subnet             |
| ------ | -------------- | ----------------------- |
| R1     | 192.168.1.0/24 | 2001\:db8\:acad:11::/64 |
| R2     | 192.168.2.0/24 | 2001\:db8\:acad:12::/64 |
| R3     | 192.168.3.0/24 | 2001\:db8\:acad:13::/64 |
| R4     | 192.168.4.0/24 | 2001\:db8\:acad:14::/64 |
| R5     | 192.168.5.0/24 | 2001\:db8\:acad:15::/64 |
| R6     | 192.168.6.0/24 | 2001\:db8\:acad:16::/64 |
| R7     | 192.168.7.0/24 | 2001\:db8\:acad:17::/64 |
| R8     | 192.168.8.0/24 | 2001\:db8\:acad:18::/64 |

---

## Routing Configuration

* Configured **OSPFv3** for IPv6 routing across all routers.
* IPv4 uses **OSPF with process ID 1**.

---

## Code Quality

* Organized addressing with `/24` for LANs and `/30` for point-to-point links.
* Clean, commented configurations for routing protocols.

---

## Testing

### ICMPv6 and IPv6 Connectivity

* Successfully pinged addresses like `2001:db8:acad:12::10`, `2001:db8:acad:13::10` with **0% packet loss**.

### SLAAC and DHCPv6

* PCs auto-configured IPv6 addresses via **SLAAC**.

### Link Failure Simulation

* Simulated failure on `Serial0/2/0`.
* **OSPFv3 adjacency restored** after recovery.

---

## Documentation

### Addressing Plan

* Detailed IPv4 and IPv6 subnet allocations as shown above.

### Routing Protocol Comparison

* **OSPFv3** preferred for IPv6 due to native support and adjacency logs.
* **OSPF** used for IPv4 to maintain compatibility.

### Migration Guide

1. Deploy dual-stack on core routers (R1–R8).
2. Configure OSPFv3 and OSPF routing.
3. Test connectivity and simulate failures.
4. Gradually phase out IPv4 where IPv6 is stable.

---
