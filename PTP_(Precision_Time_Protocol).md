# PTP (Precision Time Protocol)

**Priority:** P2  
**Feature group:** —

## Overview

**PTP** (IEEE 1588) with **SyncE**, **G.8275.1**, boundary clock, and hardware timestamping is configured under **ptp** / **clock** hierarchies; exact profile depends on network design.

## Configuration source (Cisco 8000, IOS XR 26.x)

[Timing and Synchronization Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/timing/b-timing-sync-config-guide-cisco8000.html) (PTP/SyncE).

## Sample IOS XR configuration

```text
ptp
 profile G.8275.1
  domain 24
 !
 clock
  source frequency-sync
 !
!
interface GigabitEthernet0/0/0/0
 ptp
  transport ipv4
  unicast master 198.51.100.200
 !
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
