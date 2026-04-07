# ECMP with 5 and 7 tuple hash

**Priority:** P1  
**Feature group:** HA

## Overview

**ECMP hashing** uses L3/L4 headers (5-tuple) and extended fields (7-tuple concepts) for load balancing. **Entropy labels** and **UCMP** may interact with hashing—tune **CEF load-sharing** fields per service.

## Configuration source (Cisco 8000, IOS XR 26.x)

[Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/routing/26xx/configuration/guide/b-routing-cg-cisco8000-26xx.html) (CEF load-sharing); [MPLS Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/mpls/26xx/configuration/guide/b-mpls-cg-cisco8000-26xx.html) (entropy).

## Sample IOS XR configuration

```text
! Cisco 8000 performs 5-tuple hashing by default (src/dst IP, protocol, src/dst port).
! The 'cef load-sharing fields L4' command does not exist on this platform.
! ECMP hashing is hardware-driven; tune via bundle hash or entropy labels.
router bgp 65001
 address-family ipv4 unicast
  additional-paths receive
!
! Verify bundle-hash / show cef … for platform-specific 5/7-tuple behavior
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
