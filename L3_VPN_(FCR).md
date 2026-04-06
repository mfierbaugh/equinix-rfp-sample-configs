# L3 VPN (FCR)

**Priority:** P2  
**Feature group:** L3 Services

## Overview

**L3VPN** (VRF-lite/MPLS L3VPN) for FCR use cases: hub-and-spoke, **6VPE**, multi-path, **QPPB**, link-local BGP peering, and stitching toward IP WAN as required.

## Sample IOS XR configuration

```text
vrf CUSTOMER-A
 address-family ipv4 unicast
  maximum prefix 100000
 !
 address-family ipv6 unicast
 !
!
router bgp 65001
 vrf CUSTOMER-A
  rd 65001:100
  address-family ipv4 unicast
   label mode per-vrf
  !
  neighbor 10.1.1.2
   remote-as 65500
   address-family ipv4 unicast
    route-policy PASS in
    route-policy PASS out
   !
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
