# EPL

**Priority:** P1  
**Feature group:** L2 Ethernet

## Overview

**EPL** is a transparent Ethernet private line (often port-based or simple VLAN). On IOS XR this is commonly modeled with **L2VPN cross-connect** or **EVPN VPWS** with **L2CP transparency** and optional **link-loss forwarding** (LLF) on the attachment circuit.

## Configuration source (Cisco 8000, IOS XR 26.x)

[L2VPN Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/l2vpn/26xx/configuration/guide/b-l2vpn-cg-cisco8000-26xx.html) (L2VPN cross-connect).

## Sample IOS XR configuration

```text
! EPL: L2VPN cross-connect with LDP pseudowire
l2vpn
 xconnect group EPL1
  p2p EPL-P2P
   interface GigabitEthernet0/0/0/6
   neighbor ipv4 198.51.100.3 pw-id 2006
!
! L2CP tunneling — on IOS XR Cisco 8000, l2transport and l2protocol are
! configured on subinterfaces (not physical ports). For port-based EPL,
! use the physical interface directly in the xconnect as shown above.
! For VLAN-based service with L2CP transparency, use a subinterface:
!   interface GigabitEthernet0/0/0/2.100 l2transport
!    encapsulation dot1q 100
!   !
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
