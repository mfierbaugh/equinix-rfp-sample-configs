# BGP LU (NA)

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**BGP Labeled Unicast (LU)** distributes labeled IPv4/IPv6 prefixes for transport scalability. Often used with **SR-MPLS** or hierarchical BGP designs.

## Sample IOS XR configuration

```text
router bgp 65001
 address-family ipv4 labeled-unicast
!
! Advertise LU routes toward RR / peers per policy
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
