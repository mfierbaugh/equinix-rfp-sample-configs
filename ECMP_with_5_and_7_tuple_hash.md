# ECMP with 5 and 7 tuple hash

**Priority:** P1  
**Feature group:** HA

## Overview

**ECMP hashing** uses L3/L4 headers (5-tuple) and extended fields (7-tuple concepts) for load balancing. **Entropy labels** and **UCMP** may interact with hashing—tune **CEF load-sharing** fields per service.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-routing-cg-cisco8000-26xx.pdf** (CEF load-sharing); **b-mpls-cg-cisco8000-26xx.pdf** (entropy).

## Sample IOS XR configuration

```text
cef load-sharing fields L4
router bgp 65001
 address-family ipv4 unicast
  additional-paths receive
!
! Verify bundle-hash / show cef … for platform-specific 5/7-tuple behavior
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
