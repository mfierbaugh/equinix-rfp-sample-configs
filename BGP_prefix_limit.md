# BGP prefix limit

**Priority:** P2  
**Feature group:** —

## Overview

**BGP prefix limits** can be applied per **neighbor** or per **VRF/AF** using **maximum-prefix** with optional **warning-only** or **restart** behavior.

## Configuration source (Cisco 8000, IOS XR 26.x)

[BGP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/bgp/b-bgp-config-cisco8000.html) (maximum-prefix).

## Sample IOS XR configuration

```text
router bgp 65001
 address-family ipv4 unicast
 !
 neighbor 198.51.100.5
  remote-as 65001
  address-family ipv4 unicast
   maximum-prefix 50000 80 restart 5
  !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
