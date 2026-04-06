# IX (L2 VXLAN)

**Priority:** P1  
**Feature group:** Encapsulation

## Overview

**IX L2 VXLAN** handoff requirements may be partially supported depending on EVI/VNI design; validate the compliance matrix row for your platform. Illustrative **NVE** snippet:

## Sample IOS XR configuration

```text
interface nve1
 source-interface Loopback1
 member vni 4090
  ingress-replication 198.51.100.40
!
! Pair with BGP EVPN control plane as designed
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
