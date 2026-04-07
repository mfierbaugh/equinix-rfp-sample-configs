# Dampening

**Priority:** P2  
**Feature group:** —

## Overview

**Interface dampening** suppresses excessive flapping; **BGP dampening** penalizes unstable prefixes (where used).

## Configuration source (Cisco 8000, IOS XR 26.x)

[BGP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/bgp/b-bgp-config-cisco8000.html) (BGP dampening); [Interface and Hardware Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/Interfaces/26xx/configuration/guide/b-interfaces-config-guide-cisco8k-r26xx.html) (interface dampening).

## Sample IOS XR configuration

```text
interface GigabitEthernet0/0/0/3
 dampening
!
router bgp 65001
 address-family ipv4 unicast
  dampening 15 750 2000 60
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
