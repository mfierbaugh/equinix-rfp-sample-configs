# SR-TE PCEP

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**PCEP** on the head-end uses **segment-routing traffic-eng pcc** with **pce address** (and optional **password**, **precedence**) per *Configure the Head-End Router as PCEP PCC*. An **SR-TE policy** **candidate-path** with **dynamic pcep** uses only the path computed by SR-PCE when local computation is not desired (see also *on-demand color … dynamic pcep* in *Configure SR-TE Policies*).

**Configuration reference:** Use the Cisco 8000 Series [Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) as the authoritative source for segment routing syntax, options, and platform behavior on Cisco 8000 (validate against your software release).

## Configuration source (Cisco 8000, IOS XR 26.x)

[Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) (*Configure the Head-End Router as PCEP PCC*).

## Sample IOS XR configuration

```text
! Segment Routing Configuration Guide — PCEP PCC + SR-TE policy (dynamic pcep)
segment-routing
 traffic-eng
  pcc
   source-address ipv4 192.168.0.1
   pce address ipv4 192.168.0.50
    password encrypted <secret>
  !
  policy MY_PCEP_POLICY
   color 100 end-point ipv4 192.168.0.9
   candidate-paths
    preference 100
     dynamic
      pcep
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
