# EPL

**Priority:** P1  
**Feature group:** L2 Ethernet

## Overview

**EPL** is a transparent Ethernet private line (often port-based or simple VLAN). On IOS XR this is commonly modeled with **L2VPN cross-connect** or **EVPN VPWS** with **L2CP transparency** and optional **link-loss forwarding** (LLF) on the attachment circuit.

## Sample IOS XR configuration

```text
l2vpn
 xconnect group EPL1
  p2p EPL-P2P
   interface GigabitEthernet0/0/0/2
   neighbor ipv4 198.51.100.3 pw-id 2002
!
! L2CP tunneling / transparency — typically under l2protocol forward … on the AC interface
interface GigabitEthernet0/0/0/2
 l2transport
  l2protocol cdp forward
  l2protocol stp forward
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
