# EACCESS EPL

**Priority:** P1  
**Feature group:** L2 Ethernet

## Overview

**E-Access EPL** is access-side **E-Line** handoff: transparent port **l2transport** AC toward the UNI with **EVPN VPWS** signaling—**BGP EVPN** is the **control plane** (not LDP PW). Add **L2CP** transparency on the AC as required.

## Configuration source (Cisco 8000, IOS XR 26.x)

[L2VPN Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/l2vpn/26xx/configuration/guide/b-l2vpn-cg-cisco8000-26xx.html); [Interface and Hardware Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/Interfaces/26xx/configuration/guide/b-interfaces-config-guide-cisco8k-r26xx.html) (l2transport).

## Sample IOS XR configuration

```text
! E-Access EPL: prerequisite route-policy
route-policy PASS
  pass
end-policy
!
! E-Access EPL: port-based AC (l2transport subinterface) + EVPN VPWS + BGP EVPN
evpn
 evi 3010
!
interface GigabitEthernet0/0/0/20.10 l2transport
 encapsulation dot1q 10
!
l2vpn
 xconnect group ACC-EPL
  p2p ACC-EPL-VPWS
   interface GigabitEthernet0/0/0/20.10
   neighbor evpn evi 3010 service 10
!
router bgp 65001
 bgp router-id 192.0.2.1
 address-family l2vpn evpn
  retain route-target all
 !
 neighbor 198.51.100.10
  remote-as 65001
  update-source Loopback0
  address-family l2vpn evpn
   route-policy PASS in
   route-policy PASS out
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
