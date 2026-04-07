# ISIS SR (LER, LSR)

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**IS-IS Segment Routing** follows the *Configure Segment Routing for IS-IS Protocol* procedure: **metric-style wide**, **router-id** on the loopback used for the prefix-SID, **segment-routing mpls** on the IPv4 unicast address family, and **prefix-sid index** (or **absolute**) on the IS-IS **Loopback** interface. Pair with **SRGB**/TI-LFA per design.

**Configuration reference:** Use the Cisco 8000 Series [Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) as the authoritative source for segment routing syntax, options, and platform behavior on Cisco 8000 (validate against your software release).

## Sample IOS XR configuration

```text
! Cisco 8000 SR guide: enable SR-MPLS on IS-IS + node prefix-SID on Loopback0
router isis 1
 net 49.0001.1920.0200.0001.00
 address-family ipv4 unicast
  metric-style wide level 1
  router-id Loopback0
  segment-routing mpls
 !
 interface Loopback0
  passive
  address-family ipv4 unicast
   prefix-sid index 1001
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
