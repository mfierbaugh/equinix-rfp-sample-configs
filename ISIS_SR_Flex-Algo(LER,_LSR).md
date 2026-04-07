# ISIS SR Flex-Algo(LER, LSR)

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**Flexible Algorithm** is configured under **router isis** using **flex-algo** (**advertise-definition**, **metric-type delay**, affinities, and so on). Prefix-SIDs for algorithm 128–255 use **prefix-sid algorithm** on the loopback. See *Enabling Segment Routing Flexible Algorithm* in the guide.

**Configuration reference:** Use the Cisco 8000 Series [Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) as the authoritative source for segment routing syntax, options, and platform behavior on Cisco 8000 (validate against your software release).

## Configuration source (Cisco 8000, IOS XR 26.x)

[Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) (flex-algo, prefix-sid algorithm).

## Sample IOS XR configuration

```text
! Cisco 8000 SR guide: IS-IS Flexible Algorithm 128 (delay metric) + FA prefix-SID
router isis 1
 net 49.0001.1920.0200.0001.00
 address-family ipv4 unicast
  metric-style wide level 1
  router-id Loopback0
  segment-routing mpls
 !
 flex-algo 128
  advertise-definition
  metric-type delay
 !
 interface Loopback0
  passive
  address-family ipv4 unicast
   prefix-sid algorithm 128 index 106
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
