# EVPLAN

**Priority:** P1  
**Feature group:** Encapsulation

## Overview

**EVPLAN** is a multipoint Ethernet LAN service (E-LAN) using **EVPN** for MAC learning and flooding. Supports dot1q/QinQ/native, local switching, storm control, MAC security features, and interop with standards-based EVPN peers.

## Sample IOS XR configuration

```text
l2vpn
 bridge group BG-ELAN
  bridge-domain BD-500
   vpn-id 500
   interface Bundle-Ether10.500
   evi 500
!
router bgp 65001
 address-family l2vpn evpn
!
! MAC move / storm-control — under bridge-domain or interface policy per design
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
