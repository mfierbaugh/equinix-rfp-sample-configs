# Metal Use Cases

**Priority:** P1  
**Feature group:** —

## Overview

**DHCP relay** with **VRF** awareness and **loopback** source is common for bare-metal provisioning in tenant VRFs.

## Sample IOS XR configuration

```text
dhcp ipv4
 profile METAL profile-helper relay
  helper-address vrf TENANT 198.51.100.10 gi0/0/0/10
 !
!
! Exact dhcp ipv4 syntax varies — align with IOS XR DHCP relay doc for your release
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
