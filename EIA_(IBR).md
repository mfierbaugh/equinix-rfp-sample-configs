# EIA (IBR)

**Priority:** P1  
**Feature group:** EIA

## Overview

**EIA (IBR)** features include **RTBH** (blackhole communities), **AS path prepending**, selective route advertisement, and **static routes** at global or VRF scope.

## Configuration source (Cisco 8000, IOS XR 26.x)

[Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/routing/26xx/configuration/guide/b-routing-cg-cisco8000-26xx.html) (route-policy; static routes in VRF).

## Sample IOS XR configuration

```text
route-policy RTBH-IN
  if community matches-any RTBH then
   set next-hop discard
  endif
  pass
end-policy
!
router static
 vrf INTERNET
  address-family ipv4 unicast
   192.0.2.1/32 Null0 tag 666 description RTBH
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
