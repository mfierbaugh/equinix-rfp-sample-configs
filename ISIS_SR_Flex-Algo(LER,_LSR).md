# ISIS SR Flex-Algo(LER, LSR)

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**Flexible Algorithm** extends IGP SR with custom SPF constraints (metrics, admin-groups, delay). Configure **FAD** definitions, **Flex-Algo** participation, and **TI-LFA** for FA.

## Sample IOS XR configuration

```text
segment-routing
 traffic-eng
  flex-algo 128
   definition
    metric delay
   !
  !
 !
!
router isis CORE
 address-family ipv4 unicast
  segment-routing mpls
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
