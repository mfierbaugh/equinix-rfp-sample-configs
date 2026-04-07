# Traffic Mirroring

**Priority:** P1  
**Feature group:** —

## Overview

**SPAN / ERSPAN** mirrors traffic to a local or remote analyzer. On IOS XR use **monitor-session** (feature availability varies by platform/NPU).

## Configuration source (Cisco 8000, IOS XR 26.x)

[Traffic Mirroring Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/traffic-mirroring/b-traffic-mirroring-configuration-guide-cisco8k.html) (monitor-session).

## Sample IOS XR configuration

```text
monitor-session SPAN1
 destination interface GigabitEthernet0/0/0/48
 source interface GigabitEthernet0/0/0/0 rx
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
