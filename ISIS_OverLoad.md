# ISIS OverLoad

**Priority:** P2  
**Feature group:** —

## Overview

**IS-IS overload bit** signals that the router should not be used for transit (useful during maintenance). Set **overload** or **on-startup** timers.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-routing-cg-cisco8000-26xx.pdf** (IS-IS overload).

## Sample IOS XR configuration

```text
router isis CORE
 set-overload-bit on-startup 300
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
