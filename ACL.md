# ACL

**Priority:** P1  
**Feature group:** Forwarding

## Overview

**Access lists** on Cisco 8000 support **L2 (MAC)**, **IPv4/IPv6**, and **L4** matches for interface ingress/egress and for control-plane attachment via **IPv4/IPv6 access-list** and **object-group** where supported.

## Sample IOS XR configuration

```text
ipv4 access-list ACL-EDGE-IN
 10 permit tcp 198.51.100.0 0.0.0.255 any eq bgp
 20 deny ipv4 any any
!
interface GigabitEthernet0/0/0/0
 ipv4 access-group ACL-EDGE-IN ingress
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
