# BFD

**Priority:** P2  
**Feature group:** EIA, L3 Services

## Overview

**BFD** provides fast failure detection for **BGP**, **IS-IS**, and other clients. Enable **IS-IS BFD** under **`router isis`** on each interface (for example **Bundle-Ether**) with **`bfd fast-detect ipv4`** (or **ipv6**). For **L3 Bundle-Ether** (or other interfaces), you can also set **`bfd address-family ipv4`** **minimum-interval** / **multiplier** / **fast-detect** on the interface; **LAG** may use **micro-BFD** on member links where supported—validate for your release and platform.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-bgp-config-cisco8000.pdf** (BFD under BGP neighbor); **b-routing-cg-cisco8000-26xx.pdf** (IS-IS BFD); **b-interfaces-config-guide-cisco8k-r26xx.pdf** (BFD on Bundle-Ether and interfaces).

## Sample IOS XR configuration

```text
! BGP neighbor BFD
router bgp 65001
 neighbor 198.51.100.2
  bfd fast-detect
  bfd minimum-interval 50
  bfd multiplier 3
!
! IS-IS BFD on core Bundle-Ether (per-interface under router isis)
router isis CORE
 net 49.0001.1920.0200.0001.00
 address-family ipv4 unicast
  metric-style wide
 !
 interface Bundle-Ether1
  bfd fast-detect ipv4
 !
 interface Bundle-Ether2
  bfd fast-detect ipv6
 !
!
! Interface-level BFD timers on Bundle-Ether (L3); pairs with IS-IS/BGP/OSPF as applicable
interface Bundle-Ether10
 bfd address-family ipv4 fast-detect
 bfd address-family ipv4 minimum-interval 50
 bfd address-family ipv4 multiplier 3
!
! Example: second bundle (single-stack IPv6)
interface Bundle-Ether11
 bfd address-family ipv6 fast-detect
 bfd address-family ipv6 minimum-interval 50
 bfd address-family ipv6 multiplier 3
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
