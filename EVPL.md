# EVPL

**Priority:** P1  
**Feature group:** L2 Ethernet E-Line

## Overview

**EVPL** is a point-to-point **E-Line** on Cisco 8000 using **EVPN VPWS**: attachment circuits are **l2transport** subinterfaces; the **control plane** is **BGP EVPN** (**address-family l2vpn evpn**) with **EVI**-based signaling (**neighbor evpn evi** … **target** / **source**). Supports VLAN manipulation, multiple TPID values, control-word, and FAT where applicable—validate per release.

## Configuration source (Cisco 8000, IOS XR 26.x)

**b-l2vpn-cg-cisco8000-26xx.pdf**; **b-evpn-config-cisco8000.pdf** (EVPN VPWS / xconnect).

## Sample IOS XR configuration

```text
! EVPL (EVPN VPWS): subinterface AC + BGP EVPN control plane
evpn
 evi 1001
!
interface GigabitEthernet0/0/0/1.100 l2transport
 encapsulation dot1q 100
!
l2vpn
 xconnect group XG-EVPL
  p2p VPWS-1001
   interface GigabitEthernet0/0/0/1.100
   neighbor evpn evi 1001 target 198.51.100.2 source 192.0.2.1
!
router bgp 65001
 bgp router-id 192.0.2.1
 address-family l2vpn evpn
  retain route-target all
 !
 neighbor 198.51.100.2
  remote-as 65001
  update-source Loopback0
  address-family l2vpn evpn
   route-policy PASS in
   route-policy PASS out
!
! Align EVI, RD/RT, and pw-class (control-word / encapsulation) with your design
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
