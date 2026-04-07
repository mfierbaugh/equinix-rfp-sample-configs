# BGP prefix limit

**Priority:** P2  
**Feature group:** —

## Overview

**BGP prefix limits** can be applied per **neighbor** or per **VRF/AF** using **maximum-prefix** with optional **warning-only** or **restart** behavior.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-bgp-config-cisco8000.pdf** (maximum-prefix).

## Sample IOS XR configuration

```text
router bgp 65001
 neighbor 198.51.100.5
  address-family ipv4 unicast
   maximum-prefix 50000 80 restart 5
  !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
