# SR-TE

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**Manually provisioned SR policies** use **explicit-path** definitions and a **segment-routing traffic-eng policy** with **color**, **end-point**, and **candidate-paths** referencing **segment path-explicit**—see *Explicit Paths* / *SR-TE Policy with Explicit Path* in *Configure SR-TE Policies*.

**Configuration reference:** Use the Cisco 8000 Series [Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) as the authoritative source for segment routing syntax, options, and platform behavior on Cisco 8000 (validate against your software release).

## Configuration source (Cisco 8000, IOS XR 26.x)

[Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) (explicit-path, segment-routing traffic-eng policy).

## Sample IOS XR configuration

```text
! Cisco 8000 SR guide: explicit named path + SR-TE policy (explicit segment-list)
explicit-path name PATH-STRICT
 index 10 next-label 16010
 index 20 next-label 16020
!
segment-routing
 traffic-eng
  policy POLICY-STRICT
   color 200 end-point ipv4 192.168.0.2
   candidate-paths
    preference 100
     explicit segment-list
      segment path-explicit PATH-STRICT
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
