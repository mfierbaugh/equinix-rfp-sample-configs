# ISIS SR (LER, LSR)

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**IS-IS Segment Routing** on IOS XR uses **SRGB**, **SRLB**, **mapping server**, **TI-LFA**, **microloop avoidance**, and **MPLS ping/traceroute** for SR paths.

## Sample IOS XR configuration

```text
router isis CORE
 net 49.0001.1920.0200.0001.00
 address-family ipv4 unicast
  metric-style wide
  segment-routing mpls
 !
 interface Loopback0
  passive
  address-family ipv4 unicast
   prefix-sid index 1
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
