# ISIS OverLoad

**Priority:** P2  
**Feature group:** —

## Overview

**IS-IS overload** tells neighbors to avoid this router for transit (directly attached prefixes may still be reachable). Under **router isis**, IOS XR supports **set-overload-bit** with no arguments (overload until removed), **on-startup** with a **delay** (seconds) or **wait-for-bgp**, and optional **level 1** or **level 2** scoping. **max-metric** is an alternative that raises link metrics (transit of last resort) without setting the overload bit in the LSP as in the overload-bit example. During out-of-memory conditions the overload bit may be set automatically; **oor-set-overload-bit disable** is optional (the guide cautions against disabling it). Overload-bit behavior does not apply to NSF restarts per the same chapter.

## Configuration source (Cisco 8000, IOS XR 26.x)

[Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/routing/26xx/configuration/guide/b-routing-cg-cisco8000-26xx.html) (*Customize Routes for IS-IS*: `set-overload-bit`; *Example: Configuring IS-IS To Handle Router Overload*: `max-metric`; OOR: `oor-set-overload-bit disable`).

## Sample IOS XR configuration

```text
router isis CORE
! Overload bit — use one variant as needed (not all at once):
 set-overload-bit
! set-overload-bit on-startup 300
! set-overload-bit on-startup wait-for-bgp
! set-overload-bit level 2
! set-overload-bit on-startup 300 level 1
!
! Alternative: very high interface metrics without overload bit in LSP (see routing guide example)
! max-metric
!
! Optional OOR: suppress automatic overload during memory pressure (use with design review)
! oor-set-overload-bit disable
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
