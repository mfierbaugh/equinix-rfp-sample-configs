# EVPL

**Priority:** P1  
**Feature group:** L2 Ethernet E-Line

## Overview

**EVPL** is a point-to-point Ethernet Virtual Private Line (E-Line) typically implemented with **EVPN VPWS** (Ethernet VLAN or VLAN-aware) or **MPLS xconnect** on Cisco 8000. Supports VLAN manipulation, multiple TPID values, control-word, and FAT for load balancing. Only the **subinterface** is configured in **l2transport** mode (not the parent physical port).

## Sample IOS XR configuration

```text
! EVPL: only the subinterface is in l2transport mode (no parent interface l2transport)
interface GigabitEthernet0/0/0/1.100 l2transport
 encapsulation dot1q 100
!
l2vpn
 xconnect group XG1
  p2p P2P1
   interface GigabitEthernet0/0/0/1.100
   neighbor ipv4 198.51.100.2 pw-id 1001
    pw-class EVPN-VPWS-CLASS
!
! Cross-check pw-class encapsulation (mpls / evpn) per your design
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
