# EVPLAN

**Priority:** P1  
**Feature group:** Encapsulation

## Overview

**EVPLAN** is a multipoint **E-LAN** with **BGP EVPN** as the control plane: **MP-BGP EVPN** distributes MAC/IP and inclusive multicast routes; **l2vpn** **bridge-domain** is bound to an **EVI**. Supports dot1q/QinQ/native, local switching, storm control, and MAC security per design.

## Configuration source (Cisco 8000, IOS XR 26.x)

[EVPN Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/evpn/b-evpn-config-cisco8000.html) (EVPN E-LAN, bridge-domain).

## Sample IOS XR configuration

```text
! EVPLAN: EVI + bridge-domain + full BGP EVPN AF (control plane)
evpn
 evi 500
  advertise-mac
!
l2vpn
 bridge group BG-ELAN
  bridge-domain BD-500
   vpn-id 500
   interface Bundle-Ether10.500
   evi 500
!
router bgp 65001
 bgp router-id 192.0.2.1
 address-family l2vpn evpn
  retain route-target all
 !
 neighbor 203.0.113.2
  remote-as 65001
  update-source Loopback0
  address-family l2vpn evpn
   route-policy PASS in
   route-policy PASS out
!
! MAC mobility / storm-control — bridge-domain or interface policy per design
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
