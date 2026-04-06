# EACCESS EVPL

**Priority:** P1  
**Feature group:** L2 Ethernet

## Overview

**E-Access EVPL** provides VLAN-based handoff with VLAN translation/ranges, multiple TPID support, and local switching for aggregated access toward EVPN core services.

## Sample IOS XR configuration

```text
interface GigabitEthernet0/0/0/21.100 l2transport
 encapsulation dot1q 100 second-dot1q 200
 rewrite ingress tag push dot1q 100 symmetric
!
l2vpn
 bridge group ACC-EVPL
  bridge-domain BD-ACC
   interface GigabitEthernet0/0/0/21.100
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
