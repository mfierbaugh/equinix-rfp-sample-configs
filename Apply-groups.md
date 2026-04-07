# Apply-groups

**Priority:** P2  
**Feature group:** —

## Overview

**group** defines a reusable configuration snippet; **apply-group** attaches that group so the same settings apply to multiple targets (IOS XR configuration hierarchy). This is **not** `apply-group-templates` (other NOS).

## Configuration source (Cisco 8000, IOS XR 26.x)

Cisco IOS XR **group** / **apply-group** (see [Cisco 8000 configuration guides](https://www.cisco.com/c/en/us/support/routers/8000-series-routers/products-installation-and-configuration-guides-list.html) for the Configuration Management chapter in your release). Not `apply-group-templates` (non-XR).

## Sample IOS XR configuration

```text
group IF-TEMPLATE
 interface HundredGigE0/0/0/0
  mtu 9216
 !
!
apply-group IF-TEMPLATE
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
