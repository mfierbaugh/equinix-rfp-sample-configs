# RIB/FIB Filtering

**Priority:** P2  
**Feature group:** Control Plane

## Overview

**RIB/FIB filtering** limits which routes are installed (e.g., **maximum routes**, **route-policy** on BGP import, or **prefix filtering**).

## Sample IOS XR configuration

```text
route-policy RIB-FILTER
  if destination in PREFIX-BLOCK then
   drop
  else
   pass
  endif
end-policy
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
