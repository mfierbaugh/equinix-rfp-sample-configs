# URPF

**Priority:** P2  
**Feature group:** —

## Overview

**uRPF** validates source addresses against the FIB. **Loose** mode is typical on internet edges; **strict** may require symmetric routing—confirm roadmap vs release for your ASIC path.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-interfaces-config-guide-cisco8k-r26xx.pdf** (unicast source reachable-via).

## Sample IOS XR configuration

```text
interface GigabitEthernet0/0/0/0
 ipv4 verify unicast source reachable-via any
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
