# Metal Use Cases

**Priority:** P1  
**Feature group:** —

## Overview

**DHCP relay** with **VRF** awareness and **loopback** source is common for bare-metal provisioning in tenant VRFs.

## Configuration source (Cisco 8000, IOS XR 26.x)

[IP Addresses and Services Configuration Guide](https://www.cisco.com/c/en/us/td/docs/iosxr/cisco8000/ip-addresses/26xx/configuration/guide/b-ip-addresses-cg-8k-26xx.html) (DHCP relay and related topics).

## Sample IOS XR configuration

```text
dhcp ipv4
 profile METAL relay
  helper-address vrf TENANT 198.51.100.10
 !
 interface GigabitEthernet0/0/0/10 relay profile METAL
!
```

> **Note:** Examples are illustrative for Cisco IOS XR on Cisco 8000-class systems. Validate syntax, scale limits, and feature availability for your exact release (K100/P100) and interface types.
