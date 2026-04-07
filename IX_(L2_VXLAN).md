# IX (L2 VXLAN)

**Priority:** P1  
**Feature group:** Encapsulation

## Overview

**Cisco 8000** does **not** support **VXLAN** (including **EVPN-VXLAN**) as a dataplane today. For an **IX L2** service, use **EVPN over MPLS** with an **SR-MPLS** (or MPLS) **underlay**: **MP-BGP EVPN** (**address-family l2vpn evpn**), **EVI**, and **bridge-domain** / attachment circuits— the same E-LAN **EVPN/MPLS** patterns as elsewhere on IOS XR. Do not use **NVE** / **VNI** models from other NOS.

## Configuration source (Cisco 8000, IOS XR 26.x)

[EVPN Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/evpn/b-evpn-config-cisco8000.html) (MP-BGP EVPN, EVI, bridge-domain); [L2VPN Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/l2vpn/26xx/configuration/guide/b-l2vpn-cg-cisco8000-26xx.html) (L2VPN); [Segment Routing Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/segment-routing/26xx/configuration/guide/b-segment-routing-cg-cisco8000-26xx.html) (SR-MPLS underlay).

## Sample IOS XR configuration

```text
! EVPN E-LAN over MPLS (SR-MPLS underlay per Segment Routing / MPLS guides); adjust EVI/BD to your IX design
! Core MPLS/SR, label stack, and BGP EVPN neighbors — configure per your topology
evpn
 evi 4090
  advertise-mac
!
l2vpn
 bridge group IX1
  bridge-domain BD-4090
   interface Bundle-Ether10.4090
   evi 4090
!
router bgp 65001
 address-family l2vpn evpn
  retain route-target all
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
