# EACCESS EVPL

**Priority:** P1  
**Feature group:** L2 Ethernet

## Overview

**E-Access EVPL** provides VLAN-based access handoff (translation/ranges, multiple TPID) toward the **EVPN core**: the **control plane** is **BGP EVPN** with an **EVI** on a **bridge-domain** (E-LAN style) or VLAN-aware service—only the **subinterface** is **l2transport** (not the parent port).

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-l2vpn-cg-cisco8000-26xx.pdf**; **b-interfaces-config-guide-cisco8k-r26xx.pdf** (dot1q l2transport).

## Sample IOS XR configuration

```text
! E-Access EVPL: l2transport subif + EVI/bridge-domain + BGP EVPN control plane
evpn
 evi 4100
  advertise-mac
!
interface GigabitEthernet0/0/0/21.100 l2transport
 encapsulation dot1q 100 second-dot1q 200
 rewrite ingress tag push dot1q 100 symmetric
!
l2vpn
 bridge group ACC-EVPL
  bridge-domain BD-ACC
   vpn-id 4100
   interface GigabitEthernet0/0/0/21.100
   evi 4100
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
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
