# SR-TE PCEP

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**PCEP** allows a **Path Computation Element** to compute SR policies. Roles include **PCC-initiated** (computed/controlled) paths and integration with **BGP-LS** for topology. A **segment-routing traffic-eng policy** with **dynamic pcep** under **candidate-paths** asks the PCC to obtain the computed path from the PCE (paired with **pcc** peer configuration).

## Sample IOS XR configuration

```text
pce
 peer ipv4 198.51.100.50
  password encrypted <secret>
!
segment-routing
 traffic-eng
  pcc
   peer ipv4 198.51.100.50
   source-interface Loopback0
  !
  policy MY_PCEP_POLICY
   color 100 end-point ipv4 10.0.0.9
   candidate-paths
    preference 100
     dynamic
      pcep  ! Tells the PCC to request the path from the PCE
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
