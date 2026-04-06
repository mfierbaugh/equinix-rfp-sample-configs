# SR-TE

**Priority:** P1  
**Feature group:** Control Plane

## Overview

**SR-TE path** options include **strict/loose** hops, **admin-groups**, **TE metrics**, **hop limits**, **SRLG**, and **binding SID** usage with SR policy.

## Sample IOS XR configuration

```text
explicit-path name PATH-STRICT
 index 10 next-label 16010
 index 20 next-label 16020
!
segment-routing
 traffic-eng
  policy POLICY-STRICT
   color 200 end-point ipv4 198.51.100.30
   candidate-paths
    preference 100
     explicit segment-list
      segment path-explicit PATH-STRICT
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
