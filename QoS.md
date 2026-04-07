# QoS

**Priority:** P1  
**Feature group:** Forwarding

## Overview

**QoS** on IOS XR uses **class-maps**, **policy-maps**, **policing**, **queuing**, **WRED**, and **marking**. On **Cisco 8000**, a common pattern is a **three-policy model**: **ingress** (**INGRESS**) classifies and maps to **traffic-class** / **qos-group**; **egress** attaches **EGRESS-Q** (queues, priorities, shaping) and **EGRESS-mark** (e.g. **MPLS experimental** rewrite). Equinix **P1** includes hierarchical QoS; validate **egress shaper** and marking behavior for your ASIC path and release (K100/P100).

## Configuration source (Cisco 8000, IOS XR 26.x)

[Modular QoS Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/qos/b-modular-qos-config-cisco8000.html) (class-map, policy-map, service-policy, end-policy-map).

## Sample IOS XR configuration

```text
! Cisco 8000 QoS: class-maps (must be defined before policy-maps)
class-map match-any GOLD-prec
 match precedence 5
 end-class-map
!
class-map match-any SILVER-prec
 match precedence 3
 end-class-map
!
class-map match-any BRONZE-prec
 match precedence 2
 end-class-map
!
class-map match-any TC7
 match traffic-class 7
 end-class-map
!
class-map match-any GOLD-TC
 match traffic-class 6
 end-class-map
!
class-map match-any SILVER-TC
 match traffic-class 5
 end-class-map
!
class-map match-any BRONZE-TC
 match traffic-class 4
 end-class-map
!
class-map match-any GOLD-QG
 match qos-group 5
 end-class-map
!
! Cisco 8000 QoS: policy-maps (define before attaching with service-policy)
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
! Attach service-policies to interfaces (one output policy per interface)
interface HundredGigE0/0/0/0
 service-policy input INGRESS
!
interface HundredGigE0/0/0/1
 service-policy output EGRESS-Q
!
! Note: Cisco 8000 supports one output service-policy per interface.
! To apply both queuing and marking, combine them into a single
! hierarchical policy-map or use separate interfaces.
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
