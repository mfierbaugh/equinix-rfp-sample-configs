# L3 VPN (FCR)

**Priority:** P2  
**Feature group:** L3 Services

## Overview

**L3VPN** (VRF-lite/MPLS L3VPN) for FCR use cases: hub-and-spoke, **6VPE**, **BGP multipath** (**maximum-paths** for parallel CE/PE paths where supported), **QPPB** (QoS Policy Propagation via BGP) using a **table-policy** route-policy on the VRF **ipv4 unicast** address family plus **ipv4 bgp policy propagation** on the CE-facing interface, link-local BGP peering, and stitching toward IP WAN as required.

## Configuration source (Cisco 8000, IOS XR 26.x)

[L3VPN Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/l3vpn/26xx/configuration/guide/b-l3vpn-cg-cisco8000-26xx.html); [BGP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/bgp/b-bgp-config-cisco8000.html) (VRF, maximum-paths, table-policy).

## Sample IOS XR configuration

```text
! QPPB: BGP table-policy sets qos-group / precedence on learned prefixes; enable propagation on CE interface
route-policy PASS
  pass
end-policy
!
route-policy QPPB-PREC
  set qos-group 5
end-policy
!
vrf CUSTOMER-A
 address-family ipv4 unicast
  import route-target
   65001:100
  !
  export route-target
   65001:100
  !
 !
 address-family ipv6 unicast
 !
!
router bgp 65001
 address-family vpnv4 unicast
 !
 address-family ipv4 unicast
 !
 vrf CUSTOMER-A
  rd 65001:100
  address-family ipv4 unicast
   label mode per-vrf
   maximum-paths eibgp 4
   table-policy QPPB-PREC
  !
  neighbor 10.1.1.2
   remote-as 65500
   address-family ipv4 unicast
    route-policy PASS in
    route-policy PASS out
   !
  !
 !
!
interface GigabitEthernet0/0/0/0.100
 vrf CUSTOMER-A
 ipv4 address 10.1.1.1 255.255.255.0
 ipv4 bgp policy propagation input qos-group destination
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
