# QoS

**Priority:** P1  
**Feature group:** Forwarding

## Overview

**QoS** on IOS XR uses **class-maps**, **policy-maps**, **policing**, **queuing**, **WRED**, and **marking**. Equinix **P1** includes hierarchical QoS concepts; note that **egress shaper** behavior may be **limited or not supported** on some ASIC paths—validate against your scale sheet and release notes for K100/P100.

## Sample IOS XR configuration

```text
class-map match-any CM-VOICE
 match dscp ef
!
policy-map PM-EDGE-OUT
 class CM-VOICE
  priority level 1
  police rate percent 10
 !
 class class-default
  bandwidth percent 90
  random-detect default
 !
!
interface GigabitEthernet0/0/0/0
 service-policy output PM-EDGE-OUT
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
