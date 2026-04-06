# BFD

**Priority:** P2  
**Feature group:** EIA, L3 Services

## Overview

**BFD** provides fast failure detection for IGP, BGP, and LAG (**micro-BFD**). Supports single-hop and multi-hop sessions per routing protocol.

## Sample IOS XR configuration

```text
router bgp 65001
 neighbor 198.51.100.2
  bfd fast-detect
  bfd minimum-interval 50
  bfd multiplier 3
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
