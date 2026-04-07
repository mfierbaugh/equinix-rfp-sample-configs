# Segment Routing Traffic Engineering (SR-TE)

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**SR-TE On-Demand Next Hop (ODN)** templates are defined under **segment-routing traffic-eng** using **on-demand color** … **dynamic** with **metric type** (te, igp, **latency**), optional **affinity**, **pcep**, and **sid-algorithm** / flex-algo constraints—per *Configuring SR-ODN: Examples* in *Configure SR-TE Policies*.

**Configuration reference:** Use the Cisco 8000 Series [Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) as the authoritative source for segment routing syntax, options, and platform behavior on Cisco 8000 (validate against your software release).

## Configuration source (Cisco 8000, IOS XR 26.x)

[Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) (*Configure SR-TE Policies*, ODN color templates).

## Sample IOS XR configuration

```text
! Cisco 8000 SR guide: ODN color templates (Configuring ODN Color Templates: Example)
segment-routing
 traffic-eng
  on-demand color 10
   dynamic
    metric
     type te
    !
   !
  !
  on-demand color 20
   dynamic
    metric
     type igp
    !
   !
  !
  on-demand color 21
   dynamic
    metric
     type igp
    !
    affinity exclude-any
     name CROSS
    !
   !
  !
  on-demand color 22
   dynamic
    pcep
    !
    metric
     type te
    !
    affinity exclude-any
     name CROSS
    !
   !
  !
  on-demand color 30
   dynamic
    metric
     type latency
    !
   !
  !
  on-demand color 128
   dynamic
    sid-algorithm 128
   !
  !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
