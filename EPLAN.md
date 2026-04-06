# EPLAN

**Priority:** P1  
**Feature group:** L2 Ethernet

## Overview

**EPLAN** provides multipoint L2 connectivity with EVPN E-LAN semantics; similar to EVPLAN with emphasis on L2CP handling and broadcast/multicast behavior within the bridge domain.

## Sample IOS XR configuration

```text
l2vpn
 bridge group BG-EPLAN
  bridge-domain BD-600
   vpn-id 600
   interface GigabitEthernet0/0/0/10.600
   evi 600
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
