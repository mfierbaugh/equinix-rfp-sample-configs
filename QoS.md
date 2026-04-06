# QoS

**Priority:** P1  
**Feature group:** Forwarding

## Overview

**QoS** on IOS XR uses **class-maps**, **policy-maps**, **policing**, **queuing**, **WRED**, and **marking**. On **Cisco 8000**, a common pattern is a **three-policy model**: **ingress** (**INGRESS**) classifies and maps to **traffic-class** / **qos-group**; **egress** attaches **EGRESS-Q** (queues, priorities, shaping) and **EGRESS-mark** (e.g. **MPLS experimental** rewrite). Equinix **P1** includes hierarchical QoS; validate **egress shaper** and marking behavior for your ASIC path and release (K100/P100).

## Sample IOS XR configuration

```text
! Cisco 8000 QoS: ingress + egress queueing + egress mark (example class names; add class-maps)
interface HundredGigE0/0/0/0
 service-policy input INGRESS
!
interface HundredGigE0/0/0/1
 service-policy output EGRESS-Q
 service-policy output EGRESS-mark
!
policy-map INGRESS
 class GOLD-prec
  set traffic-class 6
  set qos-group 5
  police rate 100 mbps
 !
 class SILVER-prec
  set traffic-class 5
  set qos-group 4
 !
 class BRONZE-prec
  set traffic-class 4
  set qos-group 3
 !
 class class-default
 !
 end-policy-map
!
policy-map EGRESS-Q
 class TC7
  priority level 1
 !
 class GOLD-TC
  priority level 2
  shape average percent 50
 !
 class SILVER-TC
  bandwidth remaining ratio 6
 !
 class BRONZE-TC
  bandwidth remaining ratio 3
 !
 class class-default
  bandwidth remaining ratio 1
 !
 end-policy-map
!
policy-map EGRESS-mark
 class GOLD-QG
  set mpls experimental topmost 5
 !
 class SILVER-TC
  set mpls experimental topmost 4
 !
 class BRONZE-TC
  set mpls experimental topmost 3
 !
 class class-default
  set mpls experimental topmost 0
 !
 end-policy-map
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
