# PTP (Precision Time Protocol)

**Priority:** P2  
**Feature group:** —

## Overview

**PTP** (IEEE 1588) with **SyncE**, **G.8275.1**, boundary clock, and hardware timestamping is configured under **ptp** / **clock** hierarchies; exact profile depends on network design.

## Configuration source (Cisco 8000, IOS XR 26.x)

[Timing and Synchronization Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/timing/b-timing-sync-config-guide-cisco8000.html) (PTP/SyncE).

## Sample IOS XR configuration

```text
! PTP is not supported on Cisco 8711-32FH-M (P100) platform.
! The configuration below is syntactically valid IOS XR but will fail
! semantic validation on platforms without PTP hardware support.
! On supported Cisco 8000 models (e.g. with SyncE/PTP line cards):
!
! ptp
!  clock
!   domain 24
!   profile g.8275.1 clock-type T-BC
!  !
! !
! interface HundredGigE0/0/0/0
!  ptp
!   profile slave
!   transport ipv4
!   port state slave-only
!  !
!
! Verify PTP hardware support with: show ptp platform servo
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
