# SR-TE PCEP

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**PCEP** on the head-end follows *Configure the Head-End Router as PCEP PCC* paired with **segment-routing traffic-eng pcc** peers. A **policy** **candidate-path** using **dynamic pcep** requests the computed SID list from the SR-PCE; see also *on-demand color … dynamic pcep* in the ODN section of *Configure SR-TE Policies*.

**Configuration reference:** Use the Cisco 8000 Series [Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) as the authoritative source for segment routing syntax, options, and platform behavior on Cisco 8000 (validate against your software release).

## Sample IOS XR configuration

```text
! Cisco 8000 SR guide: PCEP peer + SR-TE PCC; policy uses PCE-computed (dynamic) path
pce
 peer ipv4 192.168.0.50
  password encrypted <secret>
!
segment-routing
 traffic-eng
  pcc
   peer ipv4 192.168.0.50
   source-interface Loopback0
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
