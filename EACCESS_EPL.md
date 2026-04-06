# EACCESS EPL

**Priority:** P1  
**Feature group:** L2 Ethernet

## Overview

**E-Access EPL** models access-side EPL handoff: transparent L2 with L2CP transparency, local switching, and VLAN manipulation as required toward the UNI.

## Sample IOS XR configuration

```text
l2vpn
 xconnect group ACC1
  p2p ACC-EPL
   interface GigabitEthernet0/0/0/20
   neighbor ipv4 198.51.100.10 pw-id 3010
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
