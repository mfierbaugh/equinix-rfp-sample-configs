# EVPN-VXLAN

**Priority:** P2  
**Feature group:** L2 Ethernet

## Overview

**EVPN-VXLAN** maps EVPN routes to a VXLAN data plane. For **P2** Equinix asks for **policing per VNI or EVI**; configure **QoS policy** on the **BVI / NVE** or **l2vpn bridge** attachment as supported on your software train.

## Sample IOS XR configuration

```text
vrf VXLAN-VRF
 address-family ipv4 unicast
!
interface nve500
 source-interface Loopback0
 member vni 50100
  host-reachability protocol bgp
  ingress-replication 203.0.113.10
!
! Example policer applied to service policy (platform-specific)
policy-map PM-VNI-POLICE
 class class-default
  police rate percent 50
!
! Apply service-policy to relevant L3 interface / BVI per design
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
