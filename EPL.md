# EPL

**Priority:** P1  
**Feature group:** L2 Ethernet

## Overview

**EPL** is a transparent Ethernet private line (often port-based or simple VLAN). On IOS XR this is commonly modeled with **L2VPN cross-connect** or **EVPN VPWS** with **L2CP transparency** and optional **link-loss forwarding** (LLF) on the attachment circuit.

## Configuration source (Cisco 8000, IOS XR 26.x)

[L2VPN Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/l2vpn/26xx/configuration/guide/b-l2vpn-cg-cisco8000-26xx.html) (L2VPN cross-connect).

## Sample IOS XR configuration

```text
! EPL: L2VPN EVPN VPWS with SR-TE preferred-path
l2vpn
 router-id 1.1.1.1
 logging
  pseudowire
  nsr
  vfi
 !
 pw-class RED
  encapsulation mpls
   preferred-path sr-te policy RED fallback disable
  !
 !
 pw-class BLUE
  encapsulation mpls
   preferred-path sr-te policy BLUE fallback disable
  !
 !
 xconnect group NSO-VPWS-Customer1
  p2p NSO-VPWS-Customer1
   interface TenGigE0/0/0/0
   neighbor evpn evi 1234 target 1 source 2
    pw-class RED
   !

interface TenGigE0/0/0/0
 description NSO-VPWS-Customer1
 mtu 9192
 lldp
  receive disable
  transmit disable
 !
 l2transport
  propagate remote-status
 !
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
