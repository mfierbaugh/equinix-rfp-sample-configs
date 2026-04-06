# Control Plane Protection (COPP)

**Priority:** P2  
**Feature group:** Control Plane

## Overview

**CoPP** protects the route processor using **LPTS** templates and **control-plane** **policing**. Predefined classes cover BGP, ICMP, SNMP, etc.

## Sample IOS XR configuration

```text
control-plane
 management-plane
  inband
   interface all
    allow all
   !
  !
 !
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
