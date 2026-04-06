# Segment Routing Traffic Engineering (SR-TE)

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**SR Traffic Engineering** uses **segment lists**, **SR policies**, **BSIDs**, and **on-demand next-hop** steering. Policies may be BGP-colored or locally configured.

## Sample IOS XR configuration

```text
segment-routing
 traffic-eng
  policy POLICY-TO-PE2
   color 100 end-point ipv4 198.51.100.22
   candidate-paths
    preference 100
     explicit segment-list SL1
      index 10 mpls label 16022
     !
    !
   !
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
