# Apply-groups

**Priority:** P2  
**Feature group:** —

## Overview

**apply-group** attaches reusable configuration snippets (including **templates** and **inheritance**) to reduce repetition across interfaces.

## Sample IOS XR configuration

```text
apply-group-templates
 template IF-TEMPLATE
  interface GigabitEthernet0/0/0/1
   mtu 9216
  !
 !
!
apply-group IF-TEMPLATE
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
