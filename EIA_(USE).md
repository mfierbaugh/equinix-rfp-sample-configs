# EIA (USE)

**Priority:** P1  
**Feature group:** EIA

## Overview

**EIA (USE)** covers routing policy for anycast, BGP FlowSpec, communities, local-preference, and related edge features. **VRRP** and some **6PE** corner cases may differ by platform—verify your specific topology in the compliance matrix.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-bgp-config-cisco8000.pdf**; **b-routing-cg-cisco8000-26xx.pdf** (route-policy).

## Sample IOS XR configuration

```text
route-policy ANYCAST-IN
  if destination in PREFIX-ANY then
   set local-preference 200
  endif
  pass
end-policy
!
router bgp 65001
 neighbor 203.0.113.20
  address-family ipv4 unicast
   route-policy ANYCAST-IN in
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
