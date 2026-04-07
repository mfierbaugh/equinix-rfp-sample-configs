# IX (L2 VXLAN)

**Priority:** P1  
**Feature group:** Encapsulation

## Overview

**IX** L2 handoff uses the same IOS XR **EVPN/MPLS** and **l2vpn** patterns as elsewhere—avoid non–IOS XR `interface nve` / `member vni` syntax. Pair **MP-BGP EVPN** with **bridge-domain** / **EVI**; use **NVE overlay-encapsulation** under physical interfaces when the documented dataplane is UDP/GUE overlay.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-evpn-config-cisco8000.pdf**; **b-interfaces-config-guide-cisco8k-r26xx.pdf** (overlay/NVE).

## Sample IOS XR configuration

```text
! EVPN/MPLS E-LAN style (EVPN Configuration Guide); adjust EVI/BD to your IX design
evpn
 evi 4090
  advertise-mac
!
l2vpn
 bridge group IX1
  bridge-domain BD-4090
   interface Bundle-Ether10.4090
   evi 4090
!
router bgp 65001
 address-family l2vpn evpn
  retain route-target all
!
! Optional overlay on core-facing interface (Interface Guide — NVE / GUE)
! interface HundredGigE0/0/0/1
!  nve overlay-encapsulation guev1
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
