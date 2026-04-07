# RIB/FIB Filtering

**Priority:** P2  
**Feature group:** Control Plane

## Overview

**RIB/FIB filtering** limits which routes are installed (e.g., **maximum routes**, **route-policy** on BGP import, or **prefix filtering**). The example attaches **RIB-FILTER** to a **BGP neighbor** inbound (`route-policy … in`) so received prefixes are filtered before RIB install.

## Configuration source (Cisco 8000, IOS XR 26.x)

[BGP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/bgp/b-bgp-config-cisco8000.html); [Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/routing/26xx/configuration/guide/b-routing-cg-cisco8000-26xx.html) (route-policy, prefix-set).

## Sample IOS XR configuration

```text
prefix-set PREFIX-BLOCK
  198.51.100.0/24 le 32
end-set
!
route-policy RIB-FILTER
  if destination in PREFIX-BLOCK then
   drop
  else
   pass
  endif
end-policy
!
router bgp 65001
 bgp router-id 192.0.2.1
 neighbor 198.51.100.2
  remote-as 65500
  address-family ipv4 unicast
   route-policy RIB-FILTER in
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
