# EVPN all Types

**Priority:** P1  
**Feature group:** L2 Services

## Overview

This covers **BGP EVPN** services on Cisco IOS XR for Ethernet VPN Instance (EVI) with route types 1–4 (inclusive of inclusive multicast Ethernet tag, MAC/IP advertisement, inclusive multicast Ethernet tag for multicast, and Ethernet segment routes as applicable). **Flow-Aware Transport (FAT)** entropy labels can be advertised with EVPN prefixes where supported to improve ECMP hashing for multipath L2/L3 EVPN traffic.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-evpn-config-cisco8000.pdf** (BGP EVPN, bridge-domain, EVI); **b-bgp-config-cisco8000.pdf** (MP-BGP EVPN AF).

## Sample IOS XR configuration

```text
! BGP EVPN AF + L2VPN EVPN bridge-domain (illustrative)
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
 !
!

l2vpn
 bridge group BG1
  bridge-domain BD100
   vpn-id 100
   interface Bundle-Ether1.100
   evi 100
!
! FAT / entropy — enable per EVPN service policy where required
! (exact knobs vary by release; use entropy-label on EVPN/SR path as designed)
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
