# Day 3 — Verifying Router-to-Switch Connectivity ✅

**Project:** Cybersecurity Home Lab (15-day journal)  
**Focus:** Cisco Discovery Protocol and interface diagnostics  
**Status:** Completed four read-only verification missions

## Mission objective

Confirm the physical connection between the Cisco 1921 router and Catalyst 3750G switch from both devices, then inspect the switch interface for link speed, duplex, traffic, and errors.

## Commands used

```text
enable
show cdp neighbors
show interfaces status
show interfaces gigabitEthernet2/0/1
```

No configuration-changing commands were used.

## Results

| Check | Result |
|---|---|
| Switch discovers router | Confirmed with CDP |
| Router discovers switch | Confirmed with CDP |
| Physical connection | Router `Gi0/1` ↔ switch `Gi2/0/1` |
| Link negotiation | 1 Gbps, full duplex |
| Input errors | 0 |
| CRC errors | 0 |
| Output errors | 0 |
| Interface resets | 1 historical reset |
| Packets received | 53,534 cumulative |
| Packets sent | 314,874 cumulative |
| IP ping | Not tested yet |

## What I learned

- CDP can identify directly connected Cisco devices and map the interfaces between them.
- A connected Ethernet link confirms Layer 1/2 status, but it does not prove end-to-end IP communication.
- Full-duplex operation allows traffic in both directions at the same time.
- CRC and input/output error counters help identify physical link problems.
- Cumulative packet counts show that traffic has crossed an interface, while a zero five-minute rate only describes the moment of the check.
- A single historical interface reset is worth recording and monitoring, but it does not by itself prove an active fault.

## Confirmed topology

```mermaid
flowchart LR
    R["Cisco 1921 router<br/>Gi0/1"] <-->|"CDP confirmed<br/>1 Gbps full duplex"| S["Catalyst 3750G switch<br/>Gi2/0/1"]
```

## Scope and limits

This milestone verifies device discovery and interface health for the router-to-switch link. It does not yet prove IP addressing, routing, DHCP, Internet access, or end-to-end packet delivery.

## Next — Day 4

Assign or verify the isolated lab addressing, then test IP connectivity with ping while keeping the legacy Cisco devices behind the existing home network perimeter.

## Evidence privacy

Any screenshots shared publicly must have usernames, MAC addresses, serial numbers, credentials, and IP addresses removed or covered.